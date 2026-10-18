# Agent Gravitab - AI-Powered Browser Tab Sorter

> Agent Gravitab is an AI-powered browser tab finder and workspace sorter that helps knowledge workers, researchers, and students autonomously organize, categorize, and manage overwhelming browser tab clutter.

## Problem Statement

Knowledge workers, researchers, and students frequently suffer from "tab overload," accumulating dozens or hundreds of open browser tabs that lead to severe cognitive overhead, fragmented attention, and lost productivity. AI engineering makes it possible to build a multi-dimensional system that analyzes page semantics, urgency, and project context to autonomously structure digital workspaces under strict user preferences.

## Evidence of the Problem

1.	“Knowledge workers experience frequent fragmentation of attention and severe cognitive overhead due to digital clutter and unmanaged information streams, leading to measurable losses in task efficiency and focus.”

  *Citation*: Mark, G., Gudith, D., & Klocke, U. (2008). The Cost of Interrupted Work: More Speed and Stress. Proceedings of the SIGCHI Conference on Human Factors in Computing Systems, 107–110.

  *URL*: https://doi.org/10.1145/1357054.1357072

2.	Led by researchers at CMU’s Human-Computer Interaction Institute, it discovered that 25% of users experienced a complete system crash due to hoarding tabs. The authors detailed the "blackhole effect"—the intense psychological fear that as soon as a tab goes out of sight, the thought or task is lost forever.

  *Citation*: Aupperlee, A. (2021, May 10). Overcoming tab overload. Carnegie Mellon University.

  *URL*: https://www.cmu.edu/news/stories/archives/2021/may/overcoming-tab-overload.html



## Initial Related Work / Existing Approaches

* **Traditional Manual Folder Hierarchies:** Relies on manual user sorting and static bookmarks
>  *Limitation:* Fails to adapt to dynamic, fast-paced workflows and leads to digital hoarding behaviors where tabs are left open indefinitely out of fear of losing them.
* **Basic Session Managers:** Saves raw lists of URLs into grouped lists
>  *Limitation:* Lacks semantic intelligence, multi-dimensional ranking, or automated context awareness to help users make sense of their information streams.
* **Skeema (CMU Research Extension):** A browser extension utilizing machine learning to help users group open tabs into tasks
>  *Limitation:* Focused primarily on task-centric groupings without a multi-agent negotiation framework or customizable agentic utility weighting across privacy, urgency, and semantic clusters.

## Project Objectives

* O1: To design a multi-agent tab organization architecture featuring specialized domain agents (Semantic Topic, Urgency/Recency, Project Context, and Privacy) and a central Aggregator/Planner.
* O2: To develop the system using local vector embeddings and ranking algorithms combined with agentic workflows to generate clean, categorized workspace sessions and automated tab management actions.
* O3: To evaluate the solution in terms of categorization accuracy, retrieval precision for natural language queries, system latency, and reduction in user context-switching overhead.

## Target Users

Students, software engineers, researchers, and heavy web users who juggle multiple projects simultaneously and suffer from productivity loss due to manual tab management.

## Data Sources

* Source 1: Browser Extension Telemetry APIs (`chrome.tabs`, `chrome.history`, `chrome.bookmarks`) — URL: [https://developer.chrome.com/docs/extensions/reference/api/tabs](https://developer.chrome.com/docs/extensions/reference/api/tabs)
* Source 2: Local Vector Embeddings / Semantic Knowledge Base (Generated locally via lightweight embedding models) — URL: [https://huggingface.co/docs/transformers.js/index](https://huggingface.co/docs/transformers.js/index)

## Weekly Progress

| Week | Focus | Deliverable | Status |
| --- | --- | --- | --- |
| W1 | System map + project scope | README + docs | ✅ |
