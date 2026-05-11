>  **License:** CC BY 4.0
>  **Reuse Policy:** You're free to share, adapt, and build upon this guide for any purpose, even commercially. Just provide proper attribution and indicate if changes were made.

---

# Deep Dive: The Dispatch Pipeline and RAG Ingestion

*Companion to [Building a Cyberbrain: Step 6 - Set Up Dispatch](../building-a-cyberbrain-guide.md#step-6-set-up-dispatch-mobile-capture)*

---

# The Problem: Mobile Capture Is Too Slow Without Dispatch

I tried using Obsidian on my phone. It works for reading notes, but the capture experience is painful. To save a thought, I'd have to: open Obsidian, navigate to a folder, create a new file, type a filename, switch to editing mode, write the content, and then hope I'd remember to add frontmatter later. By the time I've done all that, the thought is half-gone and I've burned 30-60 seconds on something that should take 5.

The core insight is this: you will not capture things if capturing is slow. Every second of friction kills the habit. The difference between a 5-second capture and a 30-second capture is the difference between a system you actually use and one you abandon within a month.

Dispatch solves this by reducing capture to one action: tap and talk, tap and screenshot, tap and type. Five seconds, maximum. The processing - the hard part - happens later, automatically, on the desktop side.

---

# What Dispatch Is

Dispatch is a mobile capture app designed to work with Claude Cowork. It's your phone-side input to the system. It supports four capture modes:

- **Voice notes** - Tap the microphone and speak. Dispatch transcribes it and sends the transcription to Cowork. This is my most-used capture method. Walking, driving, in a meeting - just speak the thought.
- **Screenshots** - Screenshot anything on your phone (a message, an article, a chart) and send it to Dispatch. The AI (Artificial Intelligence) will run OCR (Optical Character Recognition) to extract the text content.
- **Photos** - Snap a picture of a whiteboard, a document, a business card, a receipt, anything physical. Same OCR extraction on the desktop side.
- **Text** - Type a quick note. Sometimes a text capture is faster than voice, especially in quiet environments.

All captures get sent to Cowork automatically. No manual sync, no file transfers, no folder navigation.

---

# The Full Pipeline: Capture to Storage

This is the complete flow from the moment you capture something on your phone to the moment it becomes a structured, searchable entry in your vault.

## Step 1: CAPTURE (Phone)

You grab whatever you need to remember, in whatever form is fastest:

- A 10-second voice note: "Call with the manufacturer - they can't hit the Q3 timeline, pushing to October, need to rethink the launch sequence."
- A screenshot of an interesting article or a chat message with key information.
- A photo of a whiteboard from a brainstorming session.
- A quick text note: "Idea - what if we used the same onboarding flow for both products?"

Dispatch sends it to Cowork automatically. Your part is done.

## Step 2: PROCESS (Cowork, Desktop)

When Cowork receives the Dispatch capture, the AI runs INTAKE MODE from your CLAUDE.md. This is where the heavy lifting happens:

**a. Extract content**
- Voice notes: works from the transcription Dispatch already created
- Screenshots and photos: runs OCR to extract visible text, identifies visual elements
- Text: parses the raw text for key information

**b. Build a structured candidate**
- Reads `_system/schema.md` to know the template
- Creates a complete YAML (a human-readable data format used for structured metadata) frontmatter block: id, project, topic, type, summary, source_kind, tags, people, entities, confidence, status
- Writes the body sections: Summary, Key Points, and any applicable optional sections (Decisions, Action Items, Context)

**c. Classify**
- Reads `_system/taxonomy.md` to use the controlled vocabulary
- Assigns the project key (which project does this belong to?)
- Assigns the type (what kind of knowledge is this?)
- Identifies tags, people mentioned, and entities referenced
- Determines confidence level (high for clear factual content, medium for meeting notes, low for rough thoughts)

**d. Propose placements**
- Generates 3 placement options with confidence scores
- Example: "Option 1: `01-projects/project-alpha/` as type `decision` (high confidence). Option 2: `03-decisions/` as type `decision` (medium confidence). Option 3: `04-facts/` as type `fact` (low confidence)."

**e. Wait for confirmation**
- The AI does not write anything until you confirm. This is a hard rule in CLAUDE.md. You review the structured candidate, adjust anything that's off, and approve the placement.

## Step 3: STORE (Obsidian Vault)

After you confirm:

1. The AI writes the structured entry to the correct vault folder via MCP (Model Context Protocol)
2. It searches for related existing entries and populates the `related_ids` field
3. It updates those related entries to point back to the new one (creating bidirectional links)
4. It returns the file path so you know exactly where it landed

The entry is now a first-class citizen in your knowledge base: fully structured, properly classified, tagged, linked, and searchable.

---

# Dispatch as the RAG Ingestion Point

This is where it gets interesting. The Dispatch pipeline is not just a capture tool. It's the ingestion layer of a RAG (Retrieval-Augmented Generation) system.

## What RAG Means Here

RAG is a pattern where an AI retrieves information from an external knowledge base to augment its responses. Instead of relying only on its training data, the AI pulls in your personal stored knowledge to answer questions.

In this system, RAG has two sides:

**INGESTION (the ETL side):**
```
Raw capture (voice / photo / screenshot / text)
  --> Cowork EXTRACTS content (transcription, OCR, parsing)
    --> Cowork TRANSFORMS it (structures using schema, classifies using taxonomy)
      --> Cowork LOADS it (writes to the correct vault folder via MCP)
```

ETL stands for Extract, Transform, Load - a standard data pipeline pattern. Your Dispatch captures are the raw inputs. The AI's processing is the transformation. The vault is the destination.

**RETRIEVAL (the RAG side):**
```
Question ("What do I know about the manufacturer timeline?")
  --> AI searches vault via MCP tools
    --> Retrieves relevant structured entries
      --> Generates answer augmented by your stored knowledge
```

When you ask a question weeks or months later, the AI doesn't try to remember the conversation. It searches your vault, finds the structured entry you created from that voice note, and gives you an answer grounded in what you actually recorded - complete with the date, the people involved, and the context.

## Why Ingestion Quality Determines Retrieval Quality

Here's the key insight: the retrieval side is only as good as the ingestion side. If a voice note gets filed without proper tags, the AI won't find it when you search. If the project key is wrong, it won't show up in project-specific queries. If the type is misclassified, it won't surface when you filter by type.

The schema, the taxonomy, and the classification process are not bureaucracy. They are the indexing layer that makes future retrieval work. Think of it like a library: the books are useless if the catalog is wrong. Your ingestion pipeline builds the catalog.

This is why the system invests so much in the processing step. A simpler system would just dump raw captures into a folder and search by keyword later. That works for 20 notes. It does not work for 200. Structured metadata - project keys, types, tags, people, entities, confidence levels - is what scales.

---

# Why Dispatch and Not Obsidian Mobile

Three reasons:

**1. Speed.** Dispatch is built for fast capture. Voice note is one tap. Screenshot is one tap. I do not need to navigate a vault, create a file, or type frontmatter. The entire capture takes 5 seconds.

**2. Processing.** Dispatch content flows to Cowork where the AI does the heavy lifting. With Obsidian mobile, I would be creating unstructured notes that still need processing later. Those unstructured notes pile up, and "later" often means "never."

**3. Single interface.** I interact with my knowledge system through the AI, not through Obsidian. Dispatch feeds the AI. Obsidian is just storage. I don't want to switch between two interfaces for the same system.

---

# Optional: The Context Prompt for Richer Captures

When you save something, the AI doesn't have to just file it passively. You can pair this system with a context prompt that tells the AI to ask follow-up questions before filing:

- "Who else was involved?"
- "What's the deadline?"
- "How does this relate to what you decided last week?"
- "What's the confidence level on this information?"
- "Are there any action items?"

These follow-up questions enrich the entry with context you might not have included on your own. A voice note that says "pushing to October" becomes an entry that also captures who was on the call, what the downstream impact is, and what decisions need to be made as a result.

This is completely optional. The system works fine without it - the AI will still classify and structure your captures using the schema. But if you want to go deeper, the context prompt adds a layer of richness that makes future retrieval even more precise.

For the full context prompt approach, see: [The context prompt that will revolutionize your workflow](https://github.com/VeritasPlaybook/playbook/blob/main/ai-powered-workflows/The%20context%20prompt%20that%20will%20revolutionize%20your%20workflow.md).

---

# Common Mistakes

**Not confirming classifications early on.** The first few weeks of using the system are a trust-building phase. The AI is learning your preferences and you're learning whether its classifications are accurate. Don't skip the confirmation step. Review every proposed placement, correct anything that's off, and give feedback. This is how the AI's accuracy improves over time.

**Skipping the taxonomy step.** Setting up Dispatch without first defining your taxonomy and schema. This leads to captures being filed with inconsistent labels because the AI has no controlled vocabulary to work from. Always have your taxonomy in place before you start capturing.

**Capturing without structure.** Using Dispatch to dump raw thoughts without any processing. The pipeline works because the AI transforms raw input into structured entries. If you bypass the processing step (by, say, just having captures sit in the inbox indefinitely), you end up with the same pile of unstructured notes you had before.

**Not reviewing the inbox regularly.** Dispatch captures that land in `00-inbox/` need to be processed. The morning briefing proposes classifications for inbox items, but you still need to confirm them. If you let the inbox pile up, the captures lose context (you forget what you meant three weeks ago) and the system's value degrades.

**Over-capturing without purpose.** Saving every screenshot, every article, every stray thought. The system works best when you capture things you'll actually want to retrieve later. A good filter: "Will I need this in two weeks?" If yes, capture it. If no, let it go. Quality of captures matters more than quantity.

---

*Next: [Scheduled Task Design and Prompt Engineering](./scheduled-tasks.md) - the automation layer that keeps your vault alive without you lifting a finger.*
