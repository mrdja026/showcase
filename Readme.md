# Mrdjan Stajic AI Research Showcase

## Intro

- 10 years of experience as a fullstack, frontend-heavy developer
- No production backend projects I can fully call my own
- Currently on a career break, exploring the AI/ML ecosystem

### Observations – Short and Blunt

- “10X Developers” don’t exist. At best, you get a 3–4x boost.
- LLMS do produce good prompts for other LLMS.
- You need to know the model, and how to talk with it. English is a funny language and models are different

---

## Video Demos - All of these projects were written with ChatGPT, Codex, Cursor, KiloCode, Google AI Studio (for coding, of for brainstorming, debugging or creating prompts)

### Jira MCP Demo

**Description:**
An end-to-end demo of a Model Context Protocol (MCP) server integrated with Jira. It fetches epic status, surfaces risks, and answers PM-style questions using live project data and a controlled system prompt.

The setup uses a **two-model approach**:

1. Model one checks (via fuzzy search) whether a request is an MCP tool call.

   - If yes, it returns the JSON to the user and passes it into another reasoning model.

2. If the request exactly matches a known pattern, it skips fuzzy search and goes straight to tool call.

**Watch:**

- Direct link: [public/jira_mcp_demo.mp4](public/jira_mcp_demo.mp4)
- Inline preview (may not render on all platforms):

![JIRA-MCP-Epic-Analyzer](public/jira_mcp_demo.gif)

---

### WebGL Scene Maker

I wanted to add **ThreeJS scenes** to my blog. I already knew the basics, but I challenged myself to build something quickly. The first step: **three voxel-style scenes** made in under one hour, with just 3.5 Codex prompts (20€ subscription).

Steps:

1. Asked ChatGPT for a prompt to generate three scenes (guy in a room, Minecraft style).
2. Next prompt: find good models for a room and a sitting character, then adapt them.
3. Added rotation controls to reposition objects.
4. Fixed small rotation issues with one final “make it like the pros do it” prompt.

**Watch:**

- Direct link: [public/merged_video.mp4](public/merged_video.mp4)
- Inline preview (may not render on all platforms):

  ![Scene editor](public/merged_video.gif)

---

### Dungeons & Dragons Singleplayer Agent

**NOTE** : I dont know Python, and absolutly do not know Terminal In UI (TUI) but this is a CLI game

This demo shows how **FAST MCP** enables deterministic tool calling for gameplay mechanics:

- Roll dice
- Attack
- Move (Left / Right / Up / Down)
- Attack again

Once actions are resolved, a narrative LLM takes over — blending tool outputs into a story.

**Example:**
When I moved north, I found a dagger. That dagger then became part of the ongoing story.

**Watch:**

- Direct link: [public/dnd_agent_demo.mp4](public/dnd_agent_demo.mp4)
- Inline preview (may not render on all platforms):

  ![DND Agent Demo](public/dnd_agent_demo.gif)

---

## My Take on LLMs

### What LLMs are **good** for

- Automating boring tasks
- Writing quick one-off scripts (e.g., my Azure fullstack deployment is a single `.sh` file)
- Understanding codebases faster (my experience: **50–70% speedup**)
- Greenfield projects
- Boilerplate generation
- Migrations (both code and infrastructure)

### What LLMs are **bad** for

- Complex calculations and math
- Strictly following instructions (ties into why prompting is hard)
- Staying current (they have cutoff dates, lack private data)
- Niche domains with limited training data (e.g., Haskell)

---

## Prompting is Hard

There are many techniques, but all boil down to the same principle: managing context.

- **Prompt engineering**
- **Context engineering**
- **Chain of Thought (CoT)**

  - e.g., ask the model to generate subquestions before answering

---

## Context Management

Every LLM is useful **until its context is ~60% full**. After that, it starts compressing and summarizing (lossy), and quality drops fast. This is why context strategy is just as important as prompt design.

---

## MCPs (Model Context Protocol)

Custom MCPs allow you to inject **fresh, relevant context** into the LLM.

- They’re not perfect — you must know _when_ to call them.
- By design, MCPs act like API calls: fetch data → feed into LLM → get reasoning.

**Example:**
A PM asks, “How’s EPIC-6 going? Any red flags?”
→ MCP fetches Jira data, injects it into the LLM context, and the system prompt guides the model’s response.

---

## What Everyone Gets Wrong

- **Too much freedom:** Sometimes a simple deterministic function beats an LLM.
- **Poor prompt injection handling:** Few people take this seriously enough.

---
