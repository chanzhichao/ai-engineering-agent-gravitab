| Checkpoint Field | Project Details (Agent Gravitab) |
| :---- | :---- |
| **Problem Evidence** | Knowledge workers experience frequent attention fragmentation and severe cognitive overhead due to digital clutter and unmanaged information streams, leading to measurable losses in task efficiency (Mark et al., 2008). Additionally, CMU research highlighted that 25% of users experienced severe system performance issues or crashes due to tab hoarding, driven by the "blackhole effect"—the psychological fear of losing a thought if a tab goes out of sight (Aupperlee, 2021). |
| **Existing Approaches** | 1\. **OneTab:** Flattens open tabs into a static list to conserve memory, but completely lacks semantic organization, automated categorization, and contextual workspace awareness. 2\. **Workona:** Provides structured manual workspace management, but imposes a heavy manual setup and maintenance burden on the user. 3\. **Chrome’s Native Tab Organizer:** Offers automated grouping via built-in LLMs, but lacks multi-dimensional priority/urgency ranking and customizable user preference constraints. |
| **Project / Engineering Gap** | Existing browser organization tools either rely on rigid, manual folder hierarchies that fail to adapt to dynamic workflows, or unconstrained LLMs that lack structured multi-dimensional classification (balancing project context, semantic similarity, recency, and active priority concurrently) and fail to respect local data privacy boundaries. |
| **Objective O1** | To design a multi-agent tab organization architecture featuring specialized domain agents (Semantic Topic, Urgency/Recency, Project Context, and Privacy/Security) and a central Aggregator/Planner. |
| **Objective O2** | To develop the system using local vector embeddings and ranking algorithms combined with agentic workflows to generate clean, categorized workspace sessions and automated tab management actions. |
| **Objective O3 (if relevant)** | To evaluate the solution in terms of categorization accuracy, retrieval precision for natural language queries, system latency, and reduction in user context-switching overhead. |
| **Intended Users** | Students, software engineers, researchers, and heavy web users who juggle multiple projects simultaneously and suffer from productivity loss due to manual tab management. |
| **Supported Tasks** | Automated tab categorization, semantic workspace grouping, urgency/recency ranking, and automated tab management actions (such as group creation and tab suspension/hibernation with undo support). |
| **Information / Knowledge Domain** | Browser metadata (titles, URLs, session history), local content snippets/DOM text, and user-defined project taxonomies. |
| **Operating Context** | Client-side browser extension environment running in Chromium-based browsers via Manifest V3, utilizing local vector embeddings and lightweight asynchronous execution. |
| **Important Constraints** | Strict local data privacy boundaries (avoiding external cloud transmission of raw sensitive page content), client-side CPU/memory resource constraints, and the requirement for user confirmation/undo states to prevent accidental tab data loss. |
| **Explicit Out-of-Scope Tasks** | The system will not permanently store raw sensitive page contents in external cloud databases, execute destructive unconfirmed tab closures, or replace native browser bookmarking permanently without consent. |
| **Evaluation Focus** | Categorization accuracy, retrieval precision for natural language queries, system latency impact on browser performance, and reduction in user context-switching overhead. |

# Section 1:
## Functional Requirements — Agent Gravitab
### Version: 1.0

| # | Requirement — The system SHALL | Scope Boundary — SHALL NOT (where relevant) |
| :--- | :--- | :--- |
| **FR1** | Capture and ingest active browser tab metadata, URLs, and contextual titles from the current browser session using extension APIs. | Intercept, log, or scrape private incognito window data or unapproved browser storage areas. |
| **FR2** | Process local vector embeddings of tab titles and content snippets to compute semantic similarity and categorize tabs into project workspaces. | Send raw, unencrypted sensitive tab text or credentials to external third-party cloud LLM endpoints. |
| **FR3** | Rank open tabs using a multi-dimensional scoring algorithm that evaluates semantic topic, recency, and user-defined priority weights. | Automatically close or hibernate active user tabs without providing an undo state or an opt-out buffer. |
| **FR4** | Decline or isolate tabs containing sensitive information (e.g., banking, healthcare) when privacy guardrails or filters are triggered. | Make permanent modifications to browser bookmarks or external password vaults without explicit user confirmation. |
| **FR5** | Present categorized workspaces and tab organization suggestions in a clean, intuitive browser extension popup or side-panel interface. | Sort tabs without the user's agreement. |

# Section 2:
## Non-Functional Requirements — Agent Gravitab
### Version: 1.0
| \# | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **NFR1** | Performance | The system shall keep workspace generation and tab categorization response times within the agreed latency target. | Measure end-to-end execution latency on a defined test workload of open tabs. | p90 latency | \< 2,000 ms |
| **NFR2** | Correctness | Tab groupings and semantic classifications shall be consistent with expected project context and user taxonomies. | Score a curated evaluation set of browser sessions using a defined rubric. | Correct categorization rate (%) | $\geq$ 85% |
| **NFR3** | Resource Efficiency | Extension memory and CPU overhead during background indexing shall remain within lightweight browser performance limits. | Monitor resource usage profiles during active background batch indexing workloads. | Peak memory overhead | \< 150 MB additional RAM (illustrative) |
| **NFR4** | Maintainability | New classification logic or UI components shall be incorporated without disrupting core background extension modules. | Run a controlled component-update and integration test. | Integration / update time | \< 10 min |

# Section 3:
## Responsible AI risks - Agent Gravitab
### Version 1.0
| \# | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
| :---- | :---- | :---- | :---- | :---- | :---- |
| **RAI1** | Fairness / Domain Consistency | System categorization performance shall not degrade beyond an acceptable tolerance across diverse web domains and user workflows. | Evaluate a stratified test set of various tab domains and compare categorization accuracy rates. | Absolute accuracy-rate gap between domains | $\leq$ 10 percentage points |
| **RAI2** | Safety / Destructive Actions | The system shall prevent automated hibernation or closure of active, user-pinned, or sensitive tabs without explicit confirmation. | Run a defined safety test set containing active, pinned, and protected tabs under auto-organization triggers. | Unintended destructive action rate | 0% |
| **RAI3** | Privacy | The system shall not transmit raw sensitive browsing history or private tab contents to external cloud endpoints. | Inspect outgoing network payloads and API requests during local vectorization and processing. | Number of detected raw data transmissions | 0 |
| **RAI4** | Transparency / Interpretability | The system shall provide verifiable reasoning or metadata traces for why specific tabs are grouped into a workspace. | Evaluate generated workspace groupings for rationale presence and semantic relevance to constituent tabs. | Rationale presence rate; semantic match rate | 100% rationale presence; $\geq$ 95% semantic match |
