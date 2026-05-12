>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: MCP Setup, Tools, and Troubleshooting

*Companion to [Building a Cyberbrain: Step 5 - Connect MCP to Obsidian](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/Building%20a%20Cyberbrain.md#step-5-connect-mcp-to-obsidian)*

---

# What MCP Is in Plain Language

MCP stands for Model Context Protocol. In plain terms, it is the bridge that lets your AI (Artificial Intelligence) read and write files in your Obsidian vault.

Without MCP, your AI can have a conversation with you but can't touch your vault. It can't search your notes, create new entries, update task statuses, or do anything that requires interacting with your knowledge base. MCP is what turns the AI from a chatbot into an agent that can actually operate on your data.

The chain works like this. REST means Representational State Transfer, a common architectural style for web APIs (Application Programming Interfaces, which are just ways for two software systems to talk to each other):

```
Your AI (Claude)
  --> calls MCP tools
    --> MCP server translates those calls into REST API requests
      --> Obsidian's Local REST API plugin receives the requests
        --> Obsidian reads/writes the actual files in your vault
```

Three components, each doing one job. The Local REST API plugin exposes your vault as a local API. The MCP server wraps that API into tools your AI can call. Your AI calls those tools to do work.

---

# Step-by-Step Setup

## 1. Install the Obsidian Local REST API Plugin

This plugin turns your Obsidian vault into a local API that other tools can talk to.

1. Open Obsidian
2. Go to Settings > Community Plugins > Browse
3. Search for "Local REST API" by Adam Coddington
4. Install and enable it
5. Go to the plugin settings:
   - Copy the API key (you'll need this for the MCP server configuration)
   - Note the default URL: `https://127.0.0.1:27124`
   - The plugin uses HTTPS (HyperText Transfer Protocol Secure, the encrypted version of HTTP used by web browsers) by default with a self-signed certificate

**Why HTTPS with a self-signed cert?** The plugin runs locally on your machine (127.0.0.1 = localhost, which means the connection never leaves your computer). The self-signed certificate means encryption is active but the certificate isn't issued by a trusted authority. That's fine for local use because the traffic stays on your own machine. You'll set `OBSIDIAN_VERIFY_SSL` to `false` in the MCP config to account for this (SSL stands for Secure Sockets Layer, an older name for the encryption protocol that HTTPS uses).

## 2. Install Node.js (If You Don't Have It)

The MCP server is a Node.js package. If you don't have Node.js installed:

1. Go to [nodejs.org](https://nodejs.org)
2. Download the LTS (Long Term Support) version
3. Run the installer with default settings
4. Verify by opening a terminal and running `node --version`

You won't be writing any JavaScript. Node.js is just the runtime that the MCP server needs to run.

## 3. Install the MCP Server

The MCP server is `cyanheads/obsidian-mcp-server`. Install it globally:

```bash
npm install -g obsidian-mcp-server
```

This installs the server as a command-line tool that Claude Desktop can launch and manage.

## 4. Configure the MCP Server in Claude Desktop

On Windows, edit the file at `%APPDATA%\Claude\claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": ["obsidian-mcp-server"],
      "env": {
        "OBSIDIAN_API_KEY": "YOUR_API_KEY_FROM_PLUGIN",
        "OBSIDIAN_BASE_URL": "https://127.0.0.1:27124",
        "OBSIDIAN_VERIFY_SSL": "false",
        "OBSIDIAN_ENABLE_CACHE": "true"
      }
    }
  }
}
```

**Field explanations:**

- `command` / `args`: Tells Claude Desktop how to launch the MCP server. `npx` runs the package without needing to specify the full path.
- `OBSIDIAN_API_KEY`: The API key you copied from the Local REST API plugin settings. This authenticates the MCP server to your vault.
- `OBSIDIAN_BASE_URL`: The URL where the Local REST API is listening. Default is `https://127.0.0.1:27124`. Don't change this unless you've modified the plugin settings.
- `OBSIDIAN_VERIFY_SSL`: Set to `false` because the Local REST API uses a self-signed certificate. If set to `true`, the connection will fail with an SSL error.
- `OBSIDIAN_ENABLE_CACHE`: Set to `true` to reduce redundant reads. The MCP server caches recent responses so repeated reads of the same file don't hit the REST API every time.

## 5. Restart and Verify

1. Save the config file.
2. Quit Claude Desktop completely. On Windows, right-click the Claude icon in the system tray and choose Quit, or use Task Manager to confirm no Claude process is still running. Opening a new conversation is not enough; the config file is only loaded at app startup.
3. Reopen Claude Desktop and open a new Cowork conversation.
4. Ask Claude something like: "List the MCP tools you have access to, then search my vault for any file with 'CLAUDE' in the filename."

**What success looks like:** Claude will name the twelve `obsidian_*` tools and find your `CLAUDE.md` file. If the tools show up but the search returns nothing, Obsidian probably isn't open. If no tools show up at all, the config file has an issue. Skip down to the troubleshooting section below.

---

# Complete Tool Reference

Once connected, your AI has access to these 12 MCP tools:

## Reading Tools

**`obsidian_list_notes`** - List files and subdirectories at any vault path.
- Supports depth filtering (how many levels deep to list)
- Supports extension filtering (only show `.md` files, for example)
- Supports regex filtering (match filenames against a pattern)
- Used by: morning briefing (to scan `08-todo/` and `00-inbox/`), dashboard (to discover task files)

**`obsidian_get_note`** - Read a note's content in several formats.
- `raw`: The plain text content of the file
- `full`: Structured data including content, frontmatter (parsed YAML), tags, and metadata
- `document_map`: An outline of the note's heading structure
- `section`: A specific section by heading name
- Used by: everything. This is the most-used tool in the system.

**`obsidian_search_notes`** - Full-text search across the vault.
- Uses Obsidian's built-in search engine
- Returns matching files with context snippets
- Used by: RECALL MODE (to find entries matching a query)

**`obsidian_list_tags`** - List all tags used across the vault.
- Returns every unique tag and how many notes use it
- Used by: weekly review (to identify inconsistent or orphaned tags)

## Writing Tools

**`obsidian_write_note`** - Create a new note at a specified path.
- Creates the file and any intermediate directories
- Used by: INTAKE MODE (to write new entries after confirmation)

**`obsidian_append_to_note`** - Append content to the end of an existing note.
- Does not overwrite existing content
- Used by: evening review (to append the review section to the daily note)

**`obsidian_patch_note`** - Insert content relative to a heading or block.
- Can prepend, append, or insert at a specific location within a note
- More surgical than append - useful for adding content under a specific heading

**`obsidian_replace_in_note`** - Search-and-replace within a note.
- Supports regex patterns
- Used by: dashboard (to update frontmatter fields when you edit a task inline)

## Metadata Tools

**`obsidian_manage_frontmatter`** - Update individual YAML frontmatter fields without rewriting the whole file.
- Surgical updates: change one field without touching the rest
- Used by: evening review (to update `focus_date`), task management (to update `status`, `completed_at`)

**`obsidian_manage_tags`** - Add or remove tags on a note.
- Works on both inline tags and frontmatter tags

## Other Tools

**`obsidian_delete_note`** - Delete a note from the vault.
- Used sparingly. Most "deletion" is actually archiving (moving to `08-todo/archived/`).

**`obsidian_open_in_ui`** - Open a specific note in the Obsidian desktop UI.
- Useful when you want to see the note rendered in Obsidian's editor

---

# What We Tried and Dropped

**obsidian-hybrid-search** was in the original implementation plan. It's an MCP server that provides BM25 (Best Matching 25, a keyword-based ranking function used in information retrieval) plus vector semantic search over your vault. Essentially, it understands the meaning of your query, not just the keywords.

We dropped it due to an MCP protocol incompatibility with Claude Desktop at the time of the build. The built-in `obsidian_search_notes` tool (which uses Obsidian's native full-text search) has been sufficient for a vault of this size (under 100 files).

**When semantic search becomes important:** Once your vault grows past roughly 500 notes, keyword-based search starts returning too many results and missing entries that use different terminology for the same concept. At that point, semantic search (which understands that "pricing strategy" and "how much to charge" are the same topic) becomes valuable. If you're building a vault you expect to grow large, keep an eye on the `obsidian-hybrid-search` project for compatibility updates.

---

# The Critical Constraint: Obsidian Must Be Running

The Local REST API plugin only works when Obsidian is open on your desktop. If Obsidian is closed, every MCP call fails. This is a hard constraint with no workaround.

**What this means in practice:**
- Before starting a Cowork session, open Obsidian
- Before scheduled tasks run, make sure Obsidian is open (or set Obsidian to launch on startup)
- If a scheduled task runs while Obsidian is closed, the task will fail

**How scheduled tasks handle this gracefully:** The task prompts are written to check for vault connectivity first. If the vault is unreachable, the task writes an error note and exits cleanly instead of crashing or producing garbage output. This means you'll see a "vault unreachable" note in your session history rather than a corrupted daily brief.

**Recommended:** Set Obsidian to launch on Windows startup so it's always available in the background. You don't need to interact with Obsidian directly - just keep it open.

---

# Troubleshooting

## "No Obsidian tools found" after restart

**Cause:** Claude Desktop didn't load the MCP config correctly.

**Fix:**
1. Check the config file path: `%APPDATA%\Claude\claude_desktop_config.json`
2. Validate the JSON (JavaScript Object Notation, the format the config file is written in) syntax. A missing comma or bracket will silently fail. Paste the file contents into a free online JSON validator (search "JSON validator" and use any reputable one). It will highlight any syntax errors.
3. Make sure the file is saved with UTF-8 encoding
4. Restart Claude Desktop completely (not just a new conversation)

## SSL/TLS errors

**Cause:** `OBSIDIAN_VERIFY_SSL` is set to `true` (or not set at all). TLS (Transport Layer Security) is the modern name for the encryption protocol that used to be called SSL (Secure Sockets Layer). Most tools still use "SSL" in their config field names even though the actual protocol is TLS, which is why the field is called `OBSIDIAN_VERIFY_SSL`.

**Fix:** Set `"OBSIDIAN_VERIFY_SSL": "false"` in the env section. The Local REST API uses a self-signed certificate, so SSL verification will always fail unless you install the cert as trusted (unnecessary for local use).

## "Connection refused" errors

**Cause:** Obsidian is not running, or the Local REST API plugin is disabled.

**Fix:**
1. Open Obsidian
2. Go to Settings > Community Plugins and verify Local REST API is enabled
3. Check that the URL in your config matches the plugin's URL (default: `https://127.0.0.1:27124`)
4. Check that no other application is using port 27124

## API key errors

**Cause:** The API key in the MCP config doesn't match the one in the plugin.

**Fix:** Go to Obsidian Settings > Local REST API > copy the API key again and paste it into the MCP config. Restart Claude Desktop.

## MCP tools work but searches return nothing

**Cause:** The vault path might be wrong, or the vault has no indexed content yet.

**Fix:**
1. Ask Claude to run `obsidian_list_notes` at the vault root to verify it can see your folder structure
2. If it can see folders but search returns nothing, Obsidian's search index may need to rebuild. Close and reopen Obsidian, wait a minute, and try again.

## Scheduled tasks fail with MCP errors

**Cause:** Obsidian was closed when the scheduled task ran.

**Fix:** Keep Obsidian running. Set it to launch on system startup. The task's error handling will produce a "vault unreachable" note rather than corrupted output, so no data is at risk - but the task's actual work won't get done until the next run.

---

# Keep It Simple: One MCP Server, Not Five

There are multiple MCP servers available for Obsidian. You might be tempted to install several for different capabilities. Don't.

The `cyanheads/obsidian-mcp-server` covers everything the system needs: reading, writing, searching, frontmatter management, and tag operations. Adding more servers creates more points of failure, more config to maintain, and more potential for tool conflicts.

If the connection between Claude and Obsidian breaks, the entire system stops - scheduled tasks fail, intake can't write, recall can't search, the dashboard can't load. Keeping the MCP layer as simple as possible (one server, one plugin, one config block) minimizes the surface area for failure.

---

*Next: [The Dispatch Pipeline and RAG Ingestion](./dispatch-pipeline.md) - how raw captures from your phone become structured knowledge entries in your vault.*
