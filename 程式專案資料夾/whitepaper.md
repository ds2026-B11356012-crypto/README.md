# Whitepaper: Medical RAG System

## 1. 問題背景

醫療知識具有以下特性：
- 高專業性
- 多義性（同一症狀對應多疾病）
- 上下文依賴性強（年齡、病史）

---

## 2. 表徵（Representation）挑戰

### 問題
自然語言轉換為向量時會面臨：
- 專有名詞語意壓縮
- 症狀描述差異（如：chest pain vs tightness）

### 解法
- 使用高語意 embedding（BGE-M3）
- Chunk overlap 保留上下文

---

## 3. Hallucination 問題

### 問題
LLM 可能生成未經驗證的醫療建議。

### 解法

1. Retrieval Grounding  
限制回答必須基於檢索資料。

2. Reranking  
提高輸入資料相關性。

3. Citation 機制  
要求輸出附帶來源。

---

## 4. Cold Start 問題

### 問題
新疾病或資料不足情境。

### 解法
- 接入外部知識庫（如 Wikipedia）
- 使用 LLM fallback 機制

---

## 5. 創新點

- Hybrid Search 提升醫療術語匹配
- Reranking 降低 hallucination
- 結合 RAGAS 進行量化評估

---

## 6. 結論

本系統透過 RAG 架構，有效提升醫療知識檢索能力，
並降低生成式模型的不確定性，達到可靠的診斷輔助效果。
