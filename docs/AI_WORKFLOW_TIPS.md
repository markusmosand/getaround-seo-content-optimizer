# AI Workflow Tips & Advanced Techniques

A curated collection of tips for working efficiently with AI tools, specifically Claude Code, multi-agent systems, and automation workflows.

**Source:** Transcribed from various tutorial videos
**Last Updated:** 2025-12-15

---

## Table of Contents

1. [Presentation Generation](#1-presentation-generation)
2. [Claude Code Skills](#2-claude-code-skills)
3. [Personal AGI Setup](#3-personal-agi-setup)
4. [Multi-Agent Systems](#4-multi-agent-systems)
5. [Multi-Agent Observability](#5-multi-agent-observability)
6. [Content Scraping Workflow](#6-content-scraping-workflow)
7. [Docker MCP Optimization](#7-docker-mcp-optimization)
8. [Complete Prompts Reference](#8-complete-prompts-reference)

---

## 1. Presentation Generation

### Overview
Use Google NotebookLM to create visually stunning PowerPoint presentations completely with AI, for free.

### When to Use
- Creating pitch decks
- Educational presentations
- Business proposals
- Any slide-based content

### Workflow
1. Open Google NotebookLM
2. Click "Slide decks" on the right sidebar
3. Paste the full prompt (see [Prompts Reference](#prompt-1-notebooklm-presentation-generator))
4. Customize the theme section as needed

### Key Features
- 14 proven viral layouts
- Clean typography rules (max 8 words headlines, 15 words body)
- Cohesive color schemes
- Visual metaphors and data visualizations

---

## 2. Claude Code Skills

### Overview
Skills allow you to dynamically load folders containing prompts, scripts, custom API calls, or specific instructions for tasks into Claude Code.

### Use Cases

#### Content Generation Skill
- Scrapes Twitter, Instagram, TikTok for niche content
- Formats scripts in your voice/style
- Contains prompts, scripts, and API connections

#### Second Brain Skill
- Interfaces with Notion, Obsidian, Google Drive
- Contains customized SOPs for:
  - File structure management
  - Data transfer between services
  - Cataloguing new notes/data

#### Project Setup Skill (Agentic Coding)
- Automates new project creation
- Sets up:
  - Project/folder structure
  - Configuration files
  - Unit testing files
  - Build pipelines

### How to Build
Create a folder for each skill containing:
```
skill-name/
├── SKILL.md           # Main instructions
├── prompts/           # Task-specific prompts
├── scripts/           # Automation scripts
├── templates/         # File templates
└── api-configs/       # API connection settings
```

---

## 3. Personal AGI Setup

### Overview
A 24/7 autonomous system that reads your to-do list, evaluates tasks, completes what it can, and reports back via messaging.

### Architecture

```
┌─────────────────────────────────────────────────┐
│           Claude Agents SDK (24/7)              │
│         Running locally on computer             │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│              Telegram MCP                        │
│         (Two-way communication)                 │
└─────────────────────────────────────────────────┘
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
┌─────────────────┐     ┌─────────────────┐
│   To-Do List    │     │  MCP Integrations│
│   (File-based)  │     │                 │
└─────────────────┘     │  - GitHub       │
                        │  - Notion       │
                        │  - Google Drive │
                        │  - Calendar     │
                        │  - Email        │
                        │  - Social Media │
                        │  - Skool        │
                        └─────────────────┘
```

### Daily Workflow
1. **Morning:** Agent gives news summaries from social feeds
2. **Morning:** Reports calendar events and priority tasks
3. **Throughout day:** Reads to-do list, evaluates tasks
4. **Execution:** Completes tasks it can handle autonomously
5. **Notification:** Sends text message when tasks are done

### Technical Stack
- **Core:** Claude Agents SDK (running 24/7 locally)
- **Communication:** Telegram MCP (text back and forth)
- **Task Source:** To-do list file (synced)
- **Integrations:** Multiple MCP servers for different apps

---

## 4. Multi-Agent Systems

### Overview
The Claude Agents SDK allows launching multiple Claude Code instances in parallel, each in its own container/sandbox.

### Key Capabilities

#### Sandboxed Execution
- Launch via TypeScript or Python script (not terminal)
- Each instance has its own desktop computer environment
- Full Claude Code capabilities and tools

#### Parallel Processing
```python
# Conceptual example
for task in tasks:
    agent = launch_claude_agent(task)
    agents.append(agent)

# All agents run simultaneously
results = await gather(*agents)
```

#### Coordination via Shared Context
- All instances use same external document system
- Agents can see what others are doing
- Enables collaborative problem-solving

#### Recursive Agent Spawning
```
Agent A
├── Spawns Agent B
│   ├── Spawns Agent D
│   └── Spawns Agent E
└── Spawns Agent C
    └── Spawns Agent F
```

### Use Cases
- Large codebase refactoring (parallel file processing)
- Research tasks (multiple sources simultaneously)
- Content generation at scale
- Complex problem decomposition

---

## 5. Multi-Agent Observability

### Overview
A framework for monitoring multiple agents working together, seeing their actions and information exchange in real-time.

### Architecture

```
┌─────────────────────────────────────────────────┐
│              Custom Dashboard (UI)               │
│         Real-time agent status display          │
└─────────────────────────────────────────────────┘
                      ▲
                      │ Updates
                      │
┌─────────────────────────────────────────────────┐
│              Monitoring Script                   │
│         Triggered by Claude Code Hooks          │
└─────────────────────────────────────────────────┘
                      ▲
                      │ Hook triggers
                      │
┌─────────────────────────────────────────────────┐
│              Claude Code Hooks                   │
│         Watches for tool calls/actions          │
└─────────────────────────────────────────────────┘
                      ▲
          ┌───────────┼───────────┐
          │           │           │
     ┌────┴────┐ ┌────┴────┐ ┌────┴────┐
     │ Agent 1 │ │ Agent 2 │ │ Agent 3 │
     └─────────┘ └─────────┘ └─────────┘
```

### Consensus Solution Pattern

The most powerful application of observability:

1. **Parallel Prompting:** Multiple LLMs respond to same problem
2. **Diverse Solutions:** Each produces slightly different solution
3. **Orchestration:** One "orchestrator LLM" synthesizes all solutions
4. **Consensus:** Combined solution is significantly better than any single one

```
Problem
   │
   ├──► LLM A ──► Solution A ──┐
   ├──► LLM B ──► Solution B ──┼──► Orchestrator ──► Consensus Solution
   └──► LLM C ──► Solution C ──┘
```

### Implementation Steps
1. Set up Claude Code hooks to watch for tool calls
2. Create script that triggers on hook events
3. Build dashboard UI to display agent states
4. Configure shared context for coordination

---

## 6. Content Scraping Workflow

### Overview
Automated workflow to scrape Twitter for niche news and generate content scripts.

### Architecture

```
┌─────────────────────────────────────────────────┐
│           100 Twitter Influencers               │
│            (Curated handles list)               │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│              Apify Scraper                       │
│    Last 10 tweets per account (24h window)      │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│           Cleaning Script                        │
│       Extract tweet content only                │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│           Claude API (Analysis)                  │
│    "Find most common topics discussed"          │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│        Claude API (Content Generation)           │
│       "Write 10 short-form video scripts"       │
└─────────────────────────────────────────────────┘
```

### Implementation Steps

1. **Set up Apify account** - Marketplace for web scrapers
2. **Collect influencer handles** - 100 accounts in your niche
3. **Configure scraper** - Last 10 tweets, 24h window, all accounts
4. **Build cleaning script** - Strip metadata, keep only text
5. **Analysis prompt** - Find trending topics
6. **Generation prompt** - Create content based on trends

### Customization
- Change source (Instagram, TikTok instead of Twitter)
- Adjust time window (48h, 1 week, etc.)
- Modify output format (blog posts, newsletters, etc.)

---

## 7. Docker MCP Optimization

### The Problem
Connecting 5+ MCP servers directly to your agent floods the context window:
- Each server has ~10 tools
- Each tool definition = ~4,000 tokens
- 5 servers × 10 tools = 50 tool definitions = ~200,000 tokens wasted

### The Solution: Docker MCP Server

```
Before (Context Flooding):
┌─────────────────────────────────────────────────┐
│                 Claude Agent                     │
│  Context: Tool1, Tool2, ... Tool50 (200K tokens)│
└─────────────────────────────────────────────────┘
          │     │     │     │     │
          ▼     ▼     ▼     ▼     ▼
        MCP1  MCP2  MCP3  MCP4  MCP5

After (Docker MCP):
┌─────────────────────────────────────────────────┐
│                 Claude Agent                     │
│     Context: Docker MCP only (~20K tokens)      │
└─────────────────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────┐
│              Docker MCP Server                   │
│    "Search available tools, use what's needed"  │
└─────────────────────────────────────────────────┘
          │     │     │     │     │
          ▼     ▼     ▼     ▼     ▼
        MCP1  MCP2  MCP3  MCP4  MCP5
```

**Result:** 90%+ reduction in context consumption

### Setup Steps
1. Connect Docker MCP server to your coding agent
2. In Docker Desktop, select MCP servers from marketplace
3. Docker MCP acts as single entry point that searches all tools

### Advanced: Programmatic MCP Workflows

Docker MCP includes a **code execution tool** that enables:

#### Sequential Tool Calling
```javascript
// Example: MCP workflow script
const data = await mcp.github.getIssues({ repo: 'myrepo' });
const filtered = data.filter(i => i.label === 'bug');
await mcp.notion.createPage({ content: filtered });
await mcp.slack.sendMessage({ channel: '#dev', text: 'Bug report updated' });
```

#### Data Control
- Data retrieved by script goes to external file
- NOT into agent's context window
- Agent can access file when needed
- Prevents context flooding from large data retrieval

### Key Benefits
- Reduced token usage (90%+)
- Programmatic workflows (scripted tool sequences)
- Data stays external (controlled context)
- Native Anthropic support coming (currently beta)

---

## 8. Complete Prompts Reference

### Prompt 1: NotebookLM Presentation Generator

**When to use:** Creating PowerPoint slides in Google NotebookLM

**Part 1: Visuals & Layouts**

```
You are a top 0.1% PowerPoint presentation designer. Using ONLY the provided sources, create a visually stunning VIRAL SLIDE DECK by following these exact design principles:

# VISUALS
1. Transform every key concept into a STRONG VISUAL METAPHOR based on source material
2. Convert all statistics into CLEAN, ELEGANT DATA VISUALIZATIONS (e.g. circle percentages, icon-based charts, progress bars)
3. Implement a COHESIVE COLOR SCHEME: Choose colors that match the topic's emotional tone
4. Every slide must use one of these PROVEN VIRAL LAYOUTS:
   1. Hero Layout: Big bold headline with cinematic image
   2. Contrast Layout: Split screen showing comparison or transformation
   3. Icon Grid: Key points as icons with minimal supportive text
   4. Quote Focus: Powerful statement with contextual visual
   5. Process Flow: Clean steps or flowchart with icon visuals
   6. Timeline/Storyline: Horizontal or vertical path with visual milestones
   7. Before/After: Dramatic transformation visualization
   8. Photo Background: Full-bleed impactful image with overlaid text
   9. Data Spotlight: Single statistic or data point magnified
   10. Interactive Prompt: Question or challenge posed to audience with supporting visual
   11. Anatomy Breakdown: Complex concept decomposed into labeled parts
   12. Comparison Matrix: Grid comparing multiple options or features
   13. Testimonial: Quote or endorsement with persona photo/avatar
   14. Minimalist Text: Single word or short phrase with artistic typography
```

**Part 2: Structure, Typography & Theme**

```
# CONTENT STRUCTURE
Adjust number of slides based on source material complexity. Use the following guidelines to structure the main narrative:

1. COMPELLING START: Most surprising/valuable insight presented as bold visual statement
2. CONTEXT SETTING: Essential background or problem visualized clearly
3. CENTRAL CONCEPT: Main idea or methodology shown as elegant diagram or metaphor
4. KEY COMPONENTS: Essential elements presented as icon grid or visual list
5. APPLICATION EXAMPLE: How it works in practice, shown as case study or demonstration
6. PRACTICAL GUIDANCE: Actionable steps presented as clean process flow
7. IMPACT & RESULTS: Outcomes/benefits visualized with data or evidence
8. MEMORABLE CLOSE: Powerful conclusion with clear next steps

# TYPOGRAPHY
- Headlines: Maximum 8 words, clear and impactful
- Body text: Maximum 15 words per point, use visual lists when available
- Apply clear visual hierarchy: Title > Highlight > Body
- Use typography to emphasize key information (size, weight, color contrast)

# THEME
- Background: Off white or white
- Primary text: near black
- Secondary text: neutral gray
- Accent color: 1 strong blue or orange
- 1 accent color per slide max
- Accent highlights the main idea or number only
- All visuals stay neutral with 1 accent highlight
- No gradients, no shadows, no rounded cards.

# SAFETY RULES
[Add any content restrictions or guidelines specific to your use case]
```

---

## Appendix: Raw Transcripts

### Transcript 1: PowerPoint Generation

> (00:00 - 00:04) "But first, if you're still creating PowerPoints manually by hand, you are literally wasting hours of your life."
>
> (00:04 - 00:10) "You can now make visually stunning PowerPoint slides like this completely with AI, completely for free. I'm gonna give you the full advanced prompts you can use right now."
>
> (00:10 - 00:17) "We're gonna use a tool called Google NotebookLM, which is a free AI tool, highly underrated. This is the first part of the prompt, it's super long just take a screenshot and drop it into ChatGPT to get the full text."
>
> (00:17 - 00:26) "Here's the second part of the prompt where you can customize the theme. Now you're gonna open NotebookLM, click slide decks on the right sidebar and paste the full prompt in."

### Transcript 2: Claude Skills Feature

> (00:00 - 00:05) "Here are my top use cases for the new Claude Skills feature that just dropped. Save for later when you're building your Claude skills."
>
> (00:05 - 00:17) "For context, Claude Skills is a new feature that allows you to dynamically load a folder that's full of prompts, scripts, custom API calls, or any specific instructions for a specific task that you wanna load into your Claude Code dynamically."
>
> (00:17 - 00:29) "I'm currently using a Content Generation Skill that has Claude Code load in a bunch of prompts, scripts, and API connections to allow it to scrape Twitter, Instagram, and TikTok for different content from my niche, and format scripts in my voice."
>
> (00:29 - 00:43) "I've also set up a Second Brain Skill, which allows Claude Code to interface with Notion, Obsidian, and my Google Drive. And it has customized SOPs in there, instructing it how to manage my file structures, how to transfer data between services, and how to catalogue new data when I input notes."
>
> (00:43 - 00:58) "For agentic coding, there's endless use cases, but the most helpful one that I've set up so far is a Project Setup Skill. Which basically instructs Claude how to set up the project structure, how to set up configuration files, how to set up unit testing files, and more. Follow for more agentic coding tips."

### Transcript 3: Claude Code as Personal AGI

> (00:00 - 00:06) "It's insane how many people even in the AI space don't see how close Claude Code is coming to being your own little personal AGI."
>
> (00:07 - 00:13) "At this point for me, I literally have Claude Code completing tasks for me like it's my personal assistant throughout the day, triggered from my phone."
>
> (00:13 - 00:28) "Most people still use a to-do list on their phone and check off things as they complete it throughout the day. Instead, I have my to-do list synced up with Claude Code so it can read my to-do list file, evaluate whether it can complete the task for me, and if it can, it does it, and it sends me a text message when it's done."
>
> (00:28 - 00:37) "This is accomplished by using an instance of Claude Agents SDK, which is running 24/7 on my computer, combined with the Telegram MCP, which allows me to text it back and forth."
>
> (00:37 - 00:47) "It has MCP integrations with all of the different apps that I use on a daily basis: GitHub, Notion, Google Drive, Calendar, Email, all my social media profiles, my Skool community, and many more."
>
> (00:47 - 00:55) "It gives me comprehensive news summaries from all my social media feeds in the morning every day, tells me what's on my calendar, and tells me the next tasks that need to be accomplished."

### Transcript 4: Claude Agents SDK

> (00:00 - 00:06) "If you use Claude Code and you want to build the most powerful multi-agent systems that you can with the tool, you need to check out the Claude Agents SDK."
>
> (00:07 - 00:14) "In simple terms, the Claude Agents SDK allows you to launch an instance of Claude Code in its own container and sandbox without interacting with it in the terminal."
>
> (00:15 - 00:27) "This is done with a TypeScript or Python script, and essentially allows you to launch an instance of Claude Code with all of the same capabilities and tools that Claude Code has, but it has its own access to its own desktop computer and all the tools that Claude Code normally has."
>
> (00:27 - 00:34) "Because you can launch agents with a script instead of starting it in your own terminal, you can launch as many instances of Claude Code in parallel as you want."
>
> (00:34 - 00:41) "You can then use Claude Code hooks to monitor the tool usage and the actions that all of your agents are taking to have a multi-agent observability framework."
>
> (00:41 - 00:49) "You can instruct all of the instances of Claude Code that you have running to use the same external document system as a context system so that they can coordinate what they're doing."
>
> (00:49 - 00:59) "Each agent can also run a script to launch another agent, which itself can launch another agent, so you can have an infinite branching tree of Claude agents."

### Transcript 5: Multi-Agent Observability

> (00:00 - 00:06) "Multi-agent observability for Claude Code. This is something that is really powerful, but I don't see a lot of other people talking about."
>
> (00:06 - 00:15) "A multi-agent observability framework is essentially just a system that allows you to monitor multiple agents working together, so you can see the actions that they're taking and the information that they're passing between each other."
>
> (00:15 - 00:25) "The most interesting way I've seen this used with Claude Code... is by using Claude Code hooks to basically wait for all of your agents to make tool calls or make certain actions."
>
> (00:25 - 00:35) "Once the hook is triggered by Claude Code's tool use, it will trigger a script to update your user interface in a custom dashboard... where you can monitor all of the current actions of all of your agents."
>
> (00:35 - 00:45) "I've been using this method to test out a concept... which says that if you use multiple LLMs to respond to the same prompt or problem, they'll all come up with slightly different solutions."
>
> (00:45 - 00:55) "But then if you have one orchestrating LLM take all of those separate solutions and synthesize them together into one consensus solution, that will result in a much better solution than just one LLM by itself."

### Transcript 6: Twitter Scraping Tool

> (00:00 - 00:06) "I made the ultimate tool to get cutting-edge news from any Twitter niche using Claude Code. Here's how. Save for later and follow for more tools like this."
>
> (00:06 - 00:13) "This workflow relies on a platform called Apify, which is essentially a marketplace of scrapers that allow you to scrape almost any source on the internet."
>
> (00:13 - 00:21) "Since I and many other people use Twitter as a proxy for the most cutting-edge news in any niche that's relevant to their business, I chose to use Twitter as the source for my Apify scraper."
>
> (00:21 - 00:27) "I collected the handles of 100 different AI influencers that I already follow that tweet about relevant topics in the AI space."
>
> (00:27 - 00:33) "I set up my Apify API to scrape the last 10 tweets in the past 24 hours from all 100 influencers."
>
> (00:33 - 00:38) "I then passed that raw tweet data through a script that cleans it and outputs only the tweet content."
>
> (00:38 - 00:49) "Then we passed this tweet data along with a comprehensive system prompt to Claude API, essentially asking it to filter through the tweet data to monitor for the most common topics discussed in the past 24 hours by all of these AI influencers."
>
> (00:49 - 00:55) "Claude's output analysis is then passed back to Claude API with a system prompt instructing it to write 10 short-form video scripts for me."
>
> (00:55 - 00:59) "If you want to use this for your niche, I'm dropping the full project in my Skool community. Link in bio."

### Transcript 7: Docker MCP Optimization

> (00:00 - 00:12) "Stop connecting your MCP servers directly to your coding agents and instead use the new MCP server release by Docker that turns all your MCP servers into one MCP server, reducing your context consumption from MCP servers by over 90%."
>
> (00:12 - 00:21) "To do this, first you're going to connect the Docker MCP server to your coding agent. Then using Docker or in the Docker Desktop app, you're going to select all the MCP servers from their marketplace that you want to use."
>
> (00:21 - 00:38) "This solves the problem where you have 5 MCP servers, each with 10 tools that take up like 20,000 tokens of context from flooding the context window of your coding agent. Instead now you just have one MCP tool that can basically search all of the other MCP tools available to only select the ones that you need for the specific task that you're doing."
>
> (00:38 - 00:52) "Anthropic just published an article that they are adding these features natively to Claude Code... The new features from Anthropic are still in a closed beta, but you can use the Docker MCP right now."
>
> (00:52 - 01:05) "This also unlocks a whole new world of programmatic MCP tool usage. Within the Docker MCP tool, there is a code execution MCP tool which essentially allows you to call an MCP tool using a JavaScript script instead of having the model call it directly."
>
> (01:05 - 01:20) "What this allows you to do is write a script that will call specific tools in sequence so you can create an MCP workflow. What's great about this is that all the MCP tool calls and all the data that's retrieved do not enter the context window of your agent. You can decide what enters the context window and what doesn't."
>
> (01:21 - 01:46) "If you're using MCP tools to retrieve large amounts of data... this solves the problem... This allows you to program a workflow into an MCP script and have all that data be stored in an external file so that none of it reaches your context window, but your agent still has access to all the data that it needs."

---

## Quick Reference Card

### Tool Selection Guide

| Task | Recommended Tool/Approach |
|------|---------------------------|
| Presentations | Google NotebookLM + Prompt |
| Task automation | Claude Code Skills |
| 24/7 assistance | Claude Agents SDK + Telegram MCP |
| Parallel processing | Multi-agent with shared context |
| Quality improvement | Consensus solution pattern |
| Content research | Apify + Claude API pipeline |
| Many integrations | Docker MCP (reduces 90% tokens) |

### Key Concepts

- **Skills:** Loadable folders with prompts, scripts, configs
- **Hooks:** Event listeners that trigger on tool calls
- **MCP:** Model Context Protocol - standardized integrations
- **Observability:** Real-time monitoring of agent actions
- **Consensus:** Multiple LLMs → Orchestrator → Better solution
- **Docker MCP:** Single entry point to many MCP servers
