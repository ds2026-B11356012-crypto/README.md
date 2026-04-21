# System Specifications

##  Data Specification

### 資料來源
- 醫療百科（如症狀、疾病說明）
- 公開醫學資料庫

### Chunking Strategy
- 方法：語義切分 + 固定長度
- Chunk Size：300 tokens
- Overlap：50 tokens

### 設計原因
避免語意斷裂，提高檢索準確性。

---

##  Performance Metrics

| 指標 | 目標 |
|------|------|
| Latency | < 2 秒 |
| Top-K | 5 |
| Recall@5 | > 80% |

---

## 🧪 Evaluation Framework

使用以下工具：

### 1. RAGAS
評估：
- Faithfulness（是否忠於資料）
- Relevance（相關性）
- Answer Completeness（完整度）

### 2. TruLens
監控：
- LLM 輸出品質
- 檢索品質

---

##  評估流程

Query → Retrieve → Generate → Compare with Ground Truth
