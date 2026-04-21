# Architecture Design

 系統流程

[Raw Medical Data]
    ↓
[ETL / Cleaning]
    ↓
[Chunking Strategy]
    ↓
========================
 Representation Boundary
 (Text → Embedding)
========================
    ↓
[Embedding Model (BGE-M3)]
    ↓
[Vector Database (FAISS)]
    ↓
[Hybrid Retriever (BM25 + Vector)]
    ↓
[Reranker Model]
    ↓
[LLM Generator]
    ↓
[Final Answer]

---



### 1. Representation Boundary
Chunking 後資料透過 Embedding 轉換為向量，此為非結構化資料轉換的關鍵邊界。

### 2. Hybrid Search
結合：
- Keyword Search（BM25）
- Semantic Search（Embedding）

提升醫療術語命中率。

### 3. Reranking
在 Retriever 與 LLM 之間加入 reranker，
確保輸入 LLM 的內容高度相關。

---


User Query
→ Query Embedding
→ Vector Search (Top-K)
→ BM25 Search
→ Merge Results
→ Rerank
→ LLM Generate
