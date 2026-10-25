| Decision | Requirement / Constraint | Alternatives Considered | Selected Option | Trade-off Accepted |
| :---- | :---- | :---- | :---- | :---- |
| **Include local vector embedding pipeline** | Tabs must be intelligently categorized into semantic workspaces (O2, NFR2)  | Remote cloud LLM embedding APIs; rigid manual folders; pure keyword matching  | Local client-side vector embeddings (e.g., Transformers.js)  | Limited by client-side model size, but guarantees strict local data privacy and zero cloud data leakage.  |
| **Stop scope at ranking and visualization (Read-only MVP)** | The system must prevent unintended destructive actions or data loss on active user tabs (RAI2)  | Full automated tab closing/hibernation; manual bookmarking folders  | Read-only workspace grouping and suggestion display  | Users must manually execute tab actions, but it completely eliminates the risk of accidental data loss and ensures 12-week feasibility. |
| **Include multi-dimensional ranking algorithm** | Tab organization must balance topic similarity, recency, and user priority weights (O2)  | Semantic similarity vector distance only; recency-only sorting  | Combined heuristic and vector-based scoring model  | Requires tuning multiple weight parameters, but produces much more practical, workflow-aligned clusters. |
| **Implement asynchronous background processing** | System responsiveness and latency must meet performance thresholds without lagging the browser (NFR1)  | Continuous real-time vectorization; synchronous main-thread execution  | Asynchronous background batch processing | Slight indexing delay on startup, but ensures smooth browser performance and meets p90 latency targets. |

Traceability Matrix

| Objective | Requirement | Evaluation Criterion | Architecture Element | Later Evidence |
| :---- | :---- | :---- | :---- | :---- |
| **\[O1\]** | **\[FR1 / FR2 / RAI4\]** | **\[Rationale Transparency & Metadata Traceability\]** | **\[Modular classification pipeline & metadata tracker\]** | **\[100% rationale presence; \>= 95% semantic match rate in evaluation test suite\]** |
| **\[O2\]** | **\[FR3 / NFR2\]** | **\[Workspace Categorization Correctness\]** | **\[Multi-dimensional ranking algorithm & local vector store\]** | **\[\>= 85% correct categorization rate on curated test workload\]** |
| **\[O3\]** | **\[NFR1\]** | **\[Execution and Response Latency\]** | **\[Asynchronous background batching engine\]** | **\[p90 latency \< 2,000 ms measured across test workload\]** |
