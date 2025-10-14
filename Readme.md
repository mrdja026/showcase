# Mrdjan Stajic AI Research Showcase

## Intro

- 10YOE fullstack frontend heavy expirience
- no backend production projects that i can call my own
- Investigating AI/ML Ecosystem while on a Carier break

### Observations - Short and Blunt

10 X Developers are not possible, 3-4 boost at best.

## Video Demos

### Jira MCP Demo

- Description: End-to-end demo showcasing a Model Context Protocol (MCP) server integrated with Jira. It fetches epic status and surfacing risks to answer PM-style questions using live project data and a controlled system prompt.

It uses a 2 model aproach where model one will determine from fuzzy search if it is a tool call for MCP, if yes, it will return the JSON to the user and feed it into another reasoning model.
If it is a exact match of the pattern it will skip fuzzy search -> tool call step

- Watch:

  - Direct link: [public/jira_mcp_demo.mp4](public/jira_mcp_demo.mp4)
  - Inline preview (may not render on all platforms):

    &lt;video src="public/jira_mcp_demo.mp4" controls width="720"&gt;
    Your browser does not support the video tag. Use the direct link above.
    &lt;/video&gt;

---

### WebGL Scene Maker

- I wanted a ThreeJS 3 Scenes for my blog. I knew about ThreeJS and what is it abstraction of. This is made under 1 hour with 3,5 prompts in Codex (price 20e a month)

1. Asked ChatGPT to create me a prompt that will have three scenes with a guy in a room doing stuff, and for simplicity sake make it voxel (minecraft style)
2. Second prompt is was to find me a good model for room and a person (one in siting position) and to change it.
3. Add rotation so i can position them
4. 0.5 was fixes after rotation (one prompt was make it like the pros do it)

- Watch:

  - Direct link: [public/merged_video.mp4](public/merged_video.mp4)
  - Inline preview (may not render on all platforms):

    &lt;video src="public/merged_video.mp4" controls width="720"&gt;
    Your browser does not support the video tag. Use the direct link above.
    &lt;/video&gt;

### Dungeons and Dragons Singleplayer Agent

- FAST MCP for excelent tool call support for deterministic needs:
- Roll dice
- Attack
- Move (Left/Right/Up/Down)
- Attack

After that the narative LLM goes into place, where it shifts between tool calling and naration using input from tool call to write a narative.

**EG** When i moved north i saw a dagger and that dagger has a place in the story

- Watch:

  - Direct link: [public/dnd_agent_demo.mp4](public/dnd_agent_demo.mp4)
  - Inline preview (may not render on all platforms):

    &lt;video src="public/dnd_agent_demo.mp4" controls width="720"&gt;
    Your browser does not support the video tag. Use the direct link above.
    &lt;/video&gt;

**What are LLMS good for**:

- Automating boring stuff, writing one off testing scripts (my azure deployment is in one .sh file for fullstack project)
- Understanding codebase faster (my expirience 50-70% increase)
- For greenfield projects
- Boilerplate code
- Migrations (code, infra)

**What are LLMS bad for**:

- Doing calculations math stuff
- Following instructions (ties into why prompting is hard)
- They have a cutoff date - Dont have relevant data, or private data
- They are trained on data that is available on the internet -> More Data -> More knowlage - If you want to use it for Haskel you wont find any joy

**Prompting is HARD**

There are lot of techniques how to prompt:

- Prompt engineering
- Context engineering
- Chain of thought
  - EG: Add to prompt ask subquestions and wait for answer

**Context management**

- Every llm is usefull untill its 60% context is full. Then it starts summarizing the conversation (lossy compression) and goes from there. That ties into Prompting is Hard

**MCPs**

- Custom MCPS allows users to add context to the LLM to produce results
- That is somewhat flaky, you need to know when to run inference, by design MCP is like an API call that returns data
- Scenario:
  PM is wondering how the epic named EPIC-6 is going and are there any red flags, MCP fetches the data for it, add it to context of the LLM and then you can ask questions about that - System prompt is very important here

## What everyone is doing wrong

- Giving LLMs too much freedom, sometimes a simple deterministic function as a tool call is better than LLM
- Not handling prompt injection well (there are various examples)
