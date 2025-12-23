# 🚀 LLM/AI Engineer Bootcamp - Lộ Trình 8 Tuần

## 📋 Tổng Quan

**Mục tiêu:** Từ Junior AI Engineer → Senior AI Engineer  
**Thời gian:** 8 tuần (khoảng 15-20 giờ/tuần)  
**Yêu cầu:** Nền tảng Python, đã có kinh nghiệm với RAG Chatbot cơ bản

---

## 📅 Lịch Trình Tổng Quan

| Tuần | Chủ Đề | Độ Khó |
|------|--------|--------|
| 1 | Foundations: Embeddings & Vector Search | ⭐⭐ |
| 2 | Vector Databases & Indexing Algorithms | ⭐⭐⭐ |
| 3 | Advanced RAG Techniques | ⭐⭐⭐ |
| 4 | Prompt Engineering & Reasoning Patterns | ⭐⭐⭐ |
| 5 | Function Calling, Tool Use & MCP | ⭐⭐⭐⭐ |
| 6 | LangChain, LangGraph & GraphRAG | ⭐⭐⭐⭐ |
| 7 | Multi-Agent Systems & Evaluation | ⭐⭐⭐⭐⭐ |
| 8 | Production, Optimization & Deployment | ⭐⭐⭐⭐⭐ |

---

## 📚 TUẦN 1: Foundations - Embeddings & Vector Search

### 🎯 Mục tiêu tuần 1
- Hiểu sâu về cách hoạt động của Embeddings
- Phân biệt được Bi-encoder vs Cross-encoder
- Nắm vững thuật toán BM25 và Sparse Retrieval
- Hiểu về Reranking và khi nào cần sử dụng

### 📖 Nội dung chi tiết

#### 1.1 Text Embeddings Fundamentals
**Lý thuyết:**
- Embedding là gì? Tại sao cần vector hóa văn bản?
- Word2Vec, GloVe → Sentence Transformers → Modern Embedding Models
- Cosine Similarity vs Euclidean Distance vs Dot Product
- Dimensionality và ảnh hưởng đến performance

**Thực hành:**
- Sử dụng `sentence-transformers` library
- So sánh các model: `all-MiniLM-L6-v2`, `all-mpnet-base-v2`, `bge-large`, `e5-large`
- Benchmark embedding models trên dataset của bạn

**Tài liệu tham khảo:**
- 📘 [Sentence Transformers Documentation](https://www.sbert.net/)
- 📘 [MTEB Leaderboard - Embedding Benchmarks](https://huggingface.co/spaces/mteb/leaderboard)
- 📘 [Understanding Embeddings - Pinecone](https://www.pinecone.io/learn/vector-embeddings/)
- 🎥 [Sentence Embeddings - HuggingFace Course](https://huggingface.co/learn/nlp-course/chapter5/6)

#### 1.2 Bi-encoder vs Cross-encoder
**Lý thuyết:**
- **Bi-encoder:** Encode query và document độc lập → so sánh vectors
  - Ưu điểm: Nhanh, có thể pre-compute document embeddings
  - Nhược điểm: Không capture được interaction giữa query-document
- **Cross-encoder:** Encode (query, document) cùng lúc → output relevance score
  - Ưu điểm: Chính xác hơn
  - Nhược điểm: Chậm, không thể pre-compute

**Thực hành:**
```python
# Notebook: week1_bi_cross_encoder.ipynb
# - Implement bi-encoder search
# - Implement cross-encoder reranking
# - So sánh accuracy và latency
```

**Tài liệu tham khảo:**
- 📘 [Bi-encoder vs Cross-encoder - SBERT](https://www.sbert.net/examples/applications/cross-encoder/README.html)
- 📘 [Cross-Encoders Paper](https://arxiv.org/abs/1910.14424)
- 💻 [GitHub: sentence-transformers examples](https://github.com/UKPLab/sentence-transformers/tree/master/examples)

#### 1.3 BM25 Algorithm & Sparse Retrieval
**Lý thuyết:**
- TF-IDF fundamentals
- BM25 formula và các hyperparameters (k1, b)
- Sparse vs Dense Retrieval
- Khi nào BM25 tốt hơn Dense Retrieval?

**Thực hành:**
- Implement BM25 từ scratch
- Sử dụng `rank_bm25` library
- So sánh BM25 vs Dense trên different query types

**Tài liệu tham khảo:**
- 📘 [BM25 Explained - Elastic](https://www.elastic.co/blog/practical-bm25-part-2-the-bm25-algorithm-and-its-variables)
- 📘 [Okapi BM25 Wikipedia](https://en.wikipedia.org/wiki/Okapi_BM25)
- 💻 [rank_bm25 GitHub](https://github.com/dorianbrown/rank_bm25)

#### 1.4 Reranking Models & Strategies
**Lý thuyết:**
- Two-stage retrieval: Retrieve → Rerank
- Cohere Rerank, BGE Reranker, ColBERT
- Late Interaction Models (ColBERT)
- Reciprocal Rank Fusion (RRF)

**Thực hành:**
- Implement reranking pipeline
- Sử dụng Cohere Rerank API
- Sử dụng open-source rerankers (bge-reranker)

**Tài liệu tham khảo:**
- 📘 [Cohere Rerank](https://docs.cohere.com/docs/rerank-2)
- 📘 [ColBERT Paper](https://arxiv.org/abs/2004.12832)
- 💻 [BGE Reranker - HuggingFace](https://huggingface.co/BAAI/bge-reranker-large)
- 📘 [Reciprocal Rank Fusion](https://plg.uwaterloo.ca/~gvcormac/cormacksigir09-rrf.pdf)

### 📝 Bài tập tuần 1
1. **Notebook 1:** Implement embedding search với sentence-transformers
2. **Notebook 2:** So sánh Bi-encoder vs Cross-encoder performance
3. **Notebook 3:** Implement Hybrid Search (BM25 + Dense + Reranking)
4. **Mini Project:** Xây dựng search engine cho Vietnamese documents

---

## 📚 TUẦN 2: Vector Databases & Indexing Algorithms

### 🎯 Mục tiêu tuần 2
- Hiểu các thuật toán indexing: HNSW, IVF, PQ
- Thành thạo sử dụng PostgreSQL với pgvector
- Làm việc với Milvus và Qdrant
- Hiểu trade-offs giữa accuracy và speed

### 📖 Nội dung chi tiết

#### 2.1 Indexing Algorithms Deep Dive
**Lý thuyết:**
- **Flat Index:** Brute-force, chính xác 100%
- **IVF (Inverted File Index):** Clustering-based, giảm search space
- **HNSW (Hierarchical Navigable Small World):** Graph-based, state-of-the-art
- **PQ (Product Quantization):** Compression, giảm memory
- **ScaNN (Google):** Combining multiple techniques

**Thực hành:**
- Implement IVF từ cơ bản với NumPy
- Sử dụng FAISS library cho các index types
- Benchmark accuracy vs latency vs memory

**Tài liệu tham khảo:**
- 📘 [FAISS Documentation](https://github.com/facebookresearch/faiss/wiki)
- 📘 [HNSW Paper](https://arxiv.org/abs/1603.09320)
- 📘 [Understanding HNSW - Pinecone](https://www.pinecone.io/learn/series/faiss/hnsw/)
- 🎥 [Vector Search Explained - James Briggs](https://www.youtube.com/watch?v=t9cfHwLCJjM)

#### 2.2 PostgreSQL + pgvector
**Lý thuyết:**
- Tại sao dùng PostgreSQL cho vector search?
- pgvector extension: installation và configuration
- Index types: ivfflat, hnsw
- Hybrid search với full-text search + vector search

**Thực hành:**
- Setup PostgreSQL + pgvector với Docker
- CRUD operations với vectors
- Optimize queries với proper indexing
- Implement hybrid search

**Tài liệu tham khảo:**
- 📘 [pgvector GitHub](https://github.com/pgvector/pgvector)
- 📘 [pgvector Performance Tips](https://github.com/pgvector/pgvector#performance)
- 💻 [Supabase pgvector Guide](https://supabase.com/docs/guides/ai/vector-columns)

#### 2.3 Milvus
**Lý thuyết:**
- Milvus architecture: Proxy, Query Node, Data Node
- Collection, Partition, Segment concepts
- Index types trong Milvus
- Scalar filtering + vector search

**Thực hành:**
- Deploy Milvus với Docker Compose
- Sử dụng pymilvus SDK
- Implement filtered search
- Multi-vector search

**Tài liệu tham khảo:**
- 📘 [Milvus Documentation](https://milvus.io/docs)
- 💻 [Milvus GitHub](https://github.com/milvus-io/milvus)
- 📘 [PyMilvus Examples](https://github.com/milvus-io/pymilvus/tree/master/examples)

#### 2.4 Qdrant
**Lý thuyết:**
- Qdrant architecture và features
- Payload filtering
- Quantization trong Qdrant
- Multi-tenancy support

**Thực hành:**
- Deploy Qdrant locally
- Sử dụng qdrant-client
- Implement advanced filtering
- Batch operations và optimization

**Tài liệu tham khảo:**
- 📘 [Qdrant Documentation](https://qdrant.tech/documentation/)
- 💻 [Qdrant GitHub](https://github.com/qdrant/qdrant)
- 📘 [Qdrant Examples](https://github.com/qdrant/examples)

### 📝 Bài tập tuần 2
1. **Notebook 1:** FAISS index types comparison
2. **Notebook 2:** Build RAG với PostgreSQL + pgvector
3. **Notebook 3:** Milvus advanced features
4. **Mini Project:** Benchmark 3 vector DBs trên cùng dataset

---

## 📚 TUẦN 3: Advanced RAG Techniques

### 🎯 Mục tiêu tuần 3
- Master các kỹ thuật Query Transformation
- Hiểu và implement Query Decomposition
- Multi-Query Retrieval strategies
- Contextual Compression và Parent-Child Retrieval

### 📖 Nội dung chi tiết

#### 3.1 Query Transformation Techniques
**Lý thuyết:**
- **Query Rewriting:** Sử dụng LLM để rewrite query rõ ràng hơn
- **HyDE (Hypothetical Document Embeddings):** Generate hypothetical answer → embed
- **Step-back Prompting:** Hỏi câu hỏi tổng quát hơn trước
- **Query Expansion:** Thêm synonyms, related terms

**Thực hành:**
- Implement HyDE retrieval
- Step-back prompting với OpenAI/Anthropic
- Query rewriting pipeline

**Tài liệu tham khảo:**
- 📘 [HyDE Paper](https://arxiv.org/abs/2212.10496)
- 📘 [Step-back Prompting Paper](https://arxiv.org/abs/2310.06117)
- 💻 [LangChain Query Transformation](https://python.langchain.com/docs/how_to/#query-analysis)

#### 3.2 Query Decomposition
**Lý thuyết:**
- Khi nào cần decompose query?
- Sub-question generation
- Sequential vs Parallel decomposition
- Answer synthesis từ sub-answers

**Thực hành:**
- Implement query decomposition pipeline
- Handle complex multi-hop questions
- Combine answers từ multiple sources

**Tài liệu tham khảo:**
- 📘 [Self-Ask Paper](https://arxiv.org/abs/2210.03350)
- 📘 [Query Decomposition - LlamaIndex](https://docs.llamaindex.ai/en/stable/examples/query_transformations/query_decomposition/)

#### 3.3 Multi-Query Retrieval
**Lý thuyết:**
- Generate multiple query variations
- Parallel retrieval
- Result fusion strategies (RRF, weighted)
- Deduplication và ranking

**Thực hành:**
- Implement multi-query generator
- Parallel search với async
- Custom fusion strategies

**Tài liệu tham khảo:**
- 📘 [Multi-Query Retriever - LangChain](https://python.langchain.com/docs/how_to/MultiQueryRetriever/)
- 📘 [RAG Fusion](https://github.com/Raudaschl/RAG-Fusion)

#### 3.4 Advanced Chunking & Retrieval Strategies
**Lý thuyết:**
- **Parent-Child Retrieval:** Retrieve child, return parent
- **Sentence Window Retrieval:** Expand context around matched sentence
- **Contextual Compression:** Compress retrieved docs to relevant parts
- **Semantic Chunking:** Chunk based on semantic similarity
- **Late Chunking:** Embed full document, chunk later

**Thực hành:**
- Implement parent-child với metadata
- Sentence window với overlap
- Contextual compression với LLM

**Tài liệu tham khảo:**
- 📘 [Chunking Strategies - Pinecone](https://www.pinecone.io/learn/chunking-strategies/)
- 📘 [Parent Document Retriever - LangChain](https://python.langchain.com/docs/how_to/parent_document_retriever/)
- 📘 [Late Chunking - Jina AI](https://jina.ai/news/late-chunking-in-long-context-embedding-models/)

#### 3.5 Self-RAG & Corrective RAG
**Lý thuyết:**
- **Self-RAG:** Model tự quyết định khi nào cần retrieve
- **CRAG (Corrective RAG):** Evaluate retrieval quality, self-correct
- Relevance scoring
- Iterative refinement

**Thực hành:**
- Implement Self-RAG với relevance checks
- CRAG pipeline với fallback strategies

**Tài liệu tham khảo:**
- 📘 [Self-RAG Paper](https://arxiv.org/abs/2310.11511)
- 📘 [CRAG Paper](https://arxiv.org/abs/2401.15884)
- 💻 [LangGraph CRAG Example](https://langchain-ai.github.io/langgraph/tutorials/rag/langgraph_crag/)

### 📝 Bài tập tuần 3
1. **Notebook 1:** Implement HyDE và Step-back prompting
2. **Notebook 2:** Multi-Query RAG với fusion
3. **Notebook 3:** Parent-Child Retrieval system
4. **Mini Project:** Build Advanced RAG pipeline với tất cả techniques

---

## 📚 TUẦN 4: Prompt Engineering & Reasoning Patterns

### 🎯 Mục tiêu tuần 4
- Master advanced prompt engineering techniques
- Hiểu sâu về Chain-of-Thought và variations
- Implement ReAct pattern
- Few-shot learning strategies

### 📖 Nội dung chi tiết

#### 4.1 Advanced Prompt Engineering
**Lý thuyết:**
- Anatomy của một good prompt
- System prompt design patterns
- Role-playing và persona
- Output formatting (JSON mode, structured output)
- Prompt injection và defense

**Thực hành:**
- Thiết kế system prompts cho different use cases
- Implement structured output với Pydantic
- Test prompt robustness

**Tài liệu tham khảo:**
- 📘 [OpenAI Prompt Engineering Guide](https://platform.openai.com/docs/guides/prompt-engineering)
- 📘 [Anthropic Prompt Engineering](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- 📘 [Prompt Engineering Guide](https://www.promptingguide.ai/)
- 💻 [Instructor - Structured Outputs](https://github.com/jxnl/instructor)

#### 4.2 Chain-of-Thought (CoT) & Variations
**Lý thuyết:**
- **Zero-shot CoT:** "Let's think step by step"
- **Few-shot CoT:** Examples với reasoning steps
- **Auto-CoT:** Automatic example generation
- **Self-Consistency:** Multiple reasoning paths → vote
- **Tree of Thoughts (ToT):** Explore multiple branches

**Thực hành:**
- Implement CoT cho math problems
- Self-consistency với sampling
- Simple ToT implementation

**Tài liệu tham khảo:**
- 📘 [Chain-of-Thought Paper](https://arxiv.org/abs/2201.11903)
- 📘 [Self-Consistency Paper](https://arxiv.org/abs/2203.11171)
- 📘 [Tree of Thoughts Paper](https://arxiv.org/abs/2305.10601)
- 💻 [ToT Implementation](https://github.com/princeton-nlp/tree-of-thought-llm)

#### 4.3 ReAct Pattern (Reasoning + Acting)
**Lý thuyết:**
- Thought → Action → Observation loop
- When to use ReAct vs pure reasoning
- Tool selection strategies
- Error handling trong ReAct

**Thực hành:**
- Implement ReAct từ scratch
- ReAct với multiple tools
- Handle tool failures gracefully

**Tài liệu tham khảo:**
- 📘 [ReAct Paper](https://arxiv.org/abs/2210.03629)
- 💻 [ReAct Prompting - LangChain](https://python.langchain.com/docs/how_to/agent_executor/)
- 🎥 [ReAct Explained](https://www.youtube.com/watch?v=Eug2clsLtFs)

#### 4.4 Advanced Reasoning Patterns
**Lý thuyết:**
- **Plan-and-Execute:** Plan first, then execute
- **Reflection:** Self-critique và improve
- **Least-to-Most Prompting:** Decompose → solve simple → build up
- **PAL (Program-Aided Language):** Generate code to solve problems

**Thực hành:**
- Implement reflection loop
- Plan-and-execute agent
- PAL cho complex calculations

**Tài liệu tham khảo:**
- 📘 [Reflexion Paper](https://arxiv.org/abs/2303.11366)
- 📘 [Plan-and-Execute - LangChain](https://python.langchain.com/docs/how_to/plan_and_execute_agent/)
- 📘 [PAL Paper](https://arxiv.org/abs/2211.10435)

#### 4.5 Few-shot Learning & In-Context Learning
**Lý thuyết:**
- Example selection strategies
- Dynamic few-shot selection
- Example ordering effects
- Semantic similarity based selection

**Thực hành:**
- Build few-shot example selector
- Dynamic example injection based on query
- Optimize number of examples

**Tài liệu tham khảo:**
- 📘 [In-Context Learning Survey](https://arxiv.org/abs/2301.00234)
- 💻 [Few-shot Prompting - LangChain](https://python.langchain.com/docs/how_to/few_shot_examples/)

### 📝 Bài tập tuần 4
1. **Notebook 1:** Advanced prompt engineering với structured outputs
2. **Notebook 2:** Chain-of-Thought và Self-Consistency
3. **Notebook 3:** ReAct agent từ scratch
4. **Mini Project:** Build reasoning agent cho complex Q&A

---

## 📚 TUẦN 5: Function Calling, Tool Use & MCP

### 🎯 Mục tiêu tuần 5
- Master Function Calling với OpenAI và Anthropic
- Thiết kế và implement custom tools
- Hiểu Model Context Protocol (MCP)
- Build agentic workflows với tools

### 📖 Nội dung chi tiết

#### 5.1 Function Calling Fundamentals
**Lý thuyết:**
- Function calling vs traditional prompting
- JSON Schema cho function definitions
- Parallel function calling
- Forced function calling vs auto

**Thực hành OpenAI:**
```python
# Define functions với proper schemas
# Handle function responses
# Parallel function calls
# Streaming với function calls
```

**Tài liệu tham khảo:**
- 📘 [OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)
- 📘 [OpenAI Cookbook - Function Calling](https://cookbook.openai.com/examples/how_to_call_functions_with_chat_models)

#### 5.2 Anthropic Tool Use
**Lý thuyết:**
- Tool use format của Claude
- Tool choice modes
- Computer use capabilities
- Best practices

**Thực hành:**
- Implement tools với Anthropic SDK
- Handle tool results
- Multi-turn với tools

**Tài liệu tham khảo:**
- 📘 [Anthropic Tool Use](https://docs.anthropic.com/en/docs/build-with-claude/tool-use)
- 📘 [Anthropic Computer Use](https://docs.anthropic.com/en/docs/build-with-claude/computer-use)

#### 5.3 Custom Tool Design Patterns
**Lý thuyết:**
- Tool design principles
- Error handling trong tools
- Async tools
- Tool composition
- Security considerations

**Thực hành:**
- Build custom tools: Web search, Calculator, Code executor
- Database query tool
- API integration tools
- File operation tools

**Tài liệu tham khảo:**
- 📘 [LangChain Custom Tools](https://python.langchain.com/docs/how_to/custom_tools/)
- 💻 [Tool Design Patterns](https://github.com/langchain-ai/langchain/tree/master/libs/langchain/langchain/tools)

#### 5.4 Model Context Protocol (MCP)
**Lý thuyết:**
- MCP là gì và tại sao cần?
- MCP Architecture: Hosts, Clients, Servers
- Resources, Prompts, Tools trong MCP
- Transport layer (stdio, SSE)

**Thực hành:**
- Setup MCP server
- Implement custom MCP tools
- Connect MCP với Claude Desktop
- Build MCP server cho database access

**Tài liệu tham khảo:**
- 📘 [MCP Official Documentation](https://modelcontextprotocol.io/introduction)
- 💻 [MCP GitHub](https://github.com/modelcontextprotocol)
- 💻 [MCP Python SDK](https://github.com/modelcontextprotocol/python-sdk)
- 📘 [MCP Servers Examples](https://github.com/modelcontextprotocol/servers)

#### 5.5 Agentic Tool Patterns
**Lý thuyết:**
- Tool selection strategies
- Tool chaining
- Fallback mechanisms
- Human-in-the-loop cho sensitive tools

**Thực hành:**
- Build agent với multiple tools
- Implement tool retry logic
- Add confirmation cho critical actions

**Tài liệu tham khảo:**
- 📘 [Building Effective Agents - Anthropic](https://www.anthropic.com/research/building-effective-agents)
- 💻 [OpenAI Assistants API](https://platform.openai.com/docs/assistants/overview)

### 📝 Bài tập tuần 5
1. **Notebook 1:** Function calling với OpenAI - multiple tools
2. **Notebook 2:** Anthropic tool use implementation
3. **Notebook 3:** Build MCP server từ scratch
4. **Mini Project:** Build agent với web search, calculator, và code execution

---

## 📚 TUẦN 6: LangChain, LangGraph & GraphRAG

### 🎯 Mục tiêu tuần 6
- Thành thạo LangChain components
- Master LangGraph state management
- Implement Human-in-the-loop
- Hiểu và build GraphRAG

### 📖 Nội dung chi tiết

#### 6.1 LangChain Deep Dive
**Lý thuyết:**
- LangChain Expression Language (LCEL)
- Chains, Runnables, RunnablePassthrough
- Prompt templates và output parsers
- Callbacks và streaming

**Thực hành:**
- Build complex chains với LCEL
- Custom output parsers
- Streaming implementations
- Error handling patterns

**Tài liệu tham khảo:**
- 📘 [LangChain Documentation](https://python.langchain.com/docs/introduction/)
- 📘 [LCEL Conceptual Guide](https://python.langchain.com/docs/concepts/lcel/)
- 💻 [LangChain GitHub](https://github.com/langchain-ai/langchain)

#### 6.2 LangGraph Fundamentals
**Lý thuyết:**
- Graph-based workflow orchestration
- StateGraph và State management
- Nodes và Edges
- Conditional routing
- Checkpointing và persistence

**Thực hành:**
- Build simple state machine
- Conditional branching
- Parallel execution
- Persistence với SQLite/PostgreSQL

**Tài liệu tham khảo:**
- 📘 [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- 📘 [LangGraph Tutorials](https://langchain-ai.github.io/langgraph/tutorials/)
- 💻 [LangGraph GitHub](https://github.com/langchain-ai/langgraph)

#### 6.3 Human-in-the-Loop Patterns
**Lý thuyết:**
- Interrupt và resume workflows
- Approval gates
- Edit state before continuing
- Timeout handling

**Thực hành:**
- Implement approval workflow
- Human feedback integration
- State editing before resumption

**Tài liệu tham khảo:**
- 📘 [LangGraph Human-in-the-loop](https://langchain-ai.github.io/langgraph/concepts/human_in_the_loop/)
- 💻 [HITL Examples](https://langchain-ai.github.io/langgraph/how-tos/#human-in-the-loop)

#### 6.4 Memory Management in Conversations
**Lý thuyết:**
- Short-term vs Long-term memory
- Conversation buffer memory
- Summary memory
- Entity memory
- Vector store memory

**Thực hành:**
- Implement different memory types
- Memory với checkpointing
- Cross-session memory
- Memory trimming strategies

**Tài liệu tham khảo:**
- 📘 [LangGraph Memory](https://langchain-ai.github.io/langgraph/concepts/memory/)
- 📘 [Memory How-tos](https://langchain-ai.github.io/langgraph/how-tos/#memory)

#### 6.5 GraphRAG
**Lý thuyết:**
- Knowledge Graphs cho RAG
- Entity extraction
- Relationship extraction
- Community detection
- Global vs Local search

**Thực hành:**
- Build knowledge graph từ documents
- Implement entity và relation extraction
- Query knowledge graph
- Combine với vector search

**Tài liệu tham khảo:**
- 📘 [Microsoft GraphRAG](https://microsoft.github.io/graphrag/)
- 💻 [GraphRAG GitHub](https://github.com/microsoft/graphrag)
- 📘 [GraphRAG Paper](https://arxiv.org/abs/2404.16130)
- 💻 [Neo4j + LangChain](https://python.langchain.com/docs/integrations/graphs/neo4j/)

### 📝 Bài tập tuần 6
1. **Notebook 1:** LangChain LCEL mastery
2. **Notebook 2:** LangGraph state management
3. **Notebook 3:** Human-in-the-loop workflow
4. **Mini Project:** Build GraphRAG system với Neo4j

---

## 📚 TUẦN 7: Multi-Agent Systems & Evaluation

### 🎯 Mục tiêu tuần 7
- Thiết kế và build Multi-Agent systems
- Hiểu các orchestration patterns
- Master RAG Evaluation với RAGAS
- Setup Observability với LangSmith/Phoenix

### 📖 Nội dung chi tiết

#### 7.1 Multi-Agent Architectures
**Lý thuyết:**
- Supervisor pattern
- Hierarchical agents
- Collaborative agents
- Competitive agents (debate)
- Swarm intelligence

**Thực hành:**
- Build supervisor agent
- Agent handoffs
- Message passing between agents

**Tài liệu tham khảo:**
- 📘 [LangGraph Multi-Agent](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)
- 📘 [Multi-Agent Tutorials](https://langchain-ai.github.io/langgraph/tutorials/#multi-agent-systems)
- 📘 [Multi-Agent Collaboration Paper](https://arxiv.org/abs/2308.08155)

#### 7.2 Agent Orchestration Frameworks
**Lý thuyết:**
- **LangGraph:** Graph-based orchestration
- **AutoGen:** Microsoft's multi-agent framework
- **CrewAI:** Role-based agent teams
- **Agent Protocol (A2A):** Standardization

**Thực hành:**
- Build agents với AutoGen
- CrewAI team setup
- Compare orchestration approaches

**Tài liệu tham khảo:**
- 💻 [AutoGen GitHub](https://github.com/microsoft/autogen)
- 📘 [AutoGen Documentation](https://microsoft.github.io/autogen/)
- 💻 [CrewAI GitHub](https://github.com/crewAIInc/crewAI)
- 📘 [CrewAI Documentation](https://docs.crewai.com/)

#### 7.3 RAG Evaluation với RAGAS
**Lý thuyết:**
- RAG evaluation metrics:
  - **Faithfulness:** Answer grounded in context?
  - **Answer Relevancy:** Answer relevant to question?
  - **Context Precision:** Retrieved context relevant?
  - **Context Recall:** All needed info retrieved?
- Synthetic test data generation

**Thực hành:**
- Setup RAGAS evaluation
- Generate synthetic QA pairs
- Evaluate different RAG configurations
- Compare retrieval strategies

**Tài liệu tham khảo:**
- 📘 [RAGAS Documentation](https://docs.ragas.io/)
- 💻 [RAGAS GitHub](https://github.com/explodinggradients/ragas)
- 📘 [RAGAS Metrics](https://docs.ragas.io/en/stable/concepts/metrics/)

#### 7.4 Observability & Tracing
**Lý thuyết:**
- Tại sao cần observability cho LLM apps?
- Tracing concepts
- Latency analysis
- Cost tracking
- Error monitoring

**LangSmith:**
- Setup LangSmith tracing
- Analyze traces
- Evaluate runs
- Datasets và testing

**Arize Phoenix:**
- Setup Phoenix
- Trace visualization
- Embedding analysis
- Span analysis

**Tài liệu tham khảo:**
- 📘 [LangSmith Documentation](https://docs.smith.langchain.com/)
- 📘 [LangSmith Tutorials](https://docs.smith.langchain.com/tutorials)
- 💻 [Arize Phoenix GitHub](https://github.com/Arize-ai/phoenix)
- 📘 [Phoenix Documentation](https://docs.arize.com/phoenix)

#### 7.5 Evaluation Best Practices
**Lý thuyết:**
- LLM-as-judge
- Pairwise comparison
- Rubric-based evaluation
- Human evaluation integration
- Continuous evaluation pipeline

**Thực hành:**
- Build evaluation pipeline
- LLM-as-judge implementation
- A/B testing setup

**Tài liệu tham khảo:**
- 📘 [LLM as Judge Paper](https://arxiv.org/abs/2306.05685)
- 📘 [Evaluation Best Practices - Anthropic](https://www.anthropic.com/research/evaluating-ai-systems)

### 📝 Bài tập tuần 7
1. **Notebook 1:** Multi-agent supervisor system
2. **Notebook 2:** AutoGen multi-agent conversation
3. **Notebook 3:** RAGAS evaluation pipeline
4. **Mini Project:** Build và evaluate multi-agent research assistant

---

## 📚 TUẦN 8: Production, Optimization & Deployment

### 🎯 Mục tiêu tuần 8
- Hiểu và apply Fine-tuning techniques
- Master Quantization methods
- Implement Caching và Rate limiting
- Deploy production-ready LLM applications

### 📖 Nội dung chi tiết

#### 8.1 Context Window Optimization
**Lý thuyết:**
- Long context challenges
- Chunking strategies revisited
- Context compression techniques
- Sliding window attention
- Lost in the middle problem

**Thực hành:**
- Implement context compression
- Optimize for long documents
- Handle context overflow gracefully

**Tài liệu tham khảo:**
- 📘 [Lost in the Middle Paper](https://arxiv.org/abs/2307.03172)
- 📘 [LLMLingua - Context Compression](https://github.com/microsoft/LLMLingua)

#### 8.2 Fine-tuning Techniques
**Lý thuyết:**
- **Full Fine-tuning:** Update all parameters
- **LoRA (Low-Rank Adaptation):** Inject trainable low-rank matrices
- **QLoRA:** Quantized LoRA
- **PEFT (Parameter Efficient Fine-tuning):** Various methods
- When to fine-tune vs prompt engineering

**Thực hành:**
- Fine-tune với HuggingFace PEFT
- LoRA configuration và hyperparameters
- Evaluation fine-tuned models

**Tài liệu tham khảo:**
- 📘 [LoRA Paper](https://arxiv.org/abs/2106.09685)
- 📘 [QLoRA Paper](https://arxiv.org/abs/2305.14314)
- 💻 [HuggingFace PEFT](https://github.com/huggingface/peft)
- 📘 [PEFT Documentation](https://huggingface.co/docs/peft)
- 📘 [Fine-tuning Guide - OpenAI](https://platform.openai.com/docs/guides/fine-tuning)

#### 8.3 Quantization Methods
**Lý thuyết:**
- Tại sao cần quantization?
- **GPTQ:** Post-training quantization
- **AWQ (Activation-aware Weight Quantization)**
- **GGUF:** Format cho llama.cpp
- **bitsandbytes:** 8-bit và 4-bit quantization
- Trade-offs: accuracy vs memory vs speed

**Thực hành:**
- Load quantized models với transformers
- Quantize custom model
- Benchmark quantized vs full precision

**Tài liệu tham khảo:**
- 📘 [GPTQ Paper](https://arxiv.org/abs/2210.17323)
- 📘 [AWQ Paper](https://arxiv.org/abs/2306.00978)
- 💻 [AutoGPTQ](https://github.com/AutoGPTQ/AutoGPTQ)
- 💻 [AutoAWQ](https://github.com/casper-hansen/AutoAWQ)
- 📘 [bitsandbytes](https://github.com/TimDettmers/bitsandbytes)

#### 8.4 Caching Strategies
**Lý thuyết:**
- Semantic caching
- Exact match caching
- KV cache optimization
- Cache invalidation strategies
- Distributed caching

**Thực hành:**
- Implement semantic cache với Redis
- GPTCache integration
- Cache hit rate optimization

**Tài liệu tham khảo:**
- 💻 [GPTCache](https://github.com/zilliztech/GPTCache)
- 📘 [LangChain Caching](https://python.langchain.com/docs/how_to/llm_caching/)
- 📘 [Redis Semantic Cache](https://redis.io/docs/interact/search-and-query/query/vector-search/)

#### 8.5 Rate Limiting & Queue Management
**Lý thuyết:**
- Rate limiting strategies
- Token bucket algorithm
- Request queuing
- Backpressure handling
- Celery + Redis for async tasks

**Thực hành:**
- Implement rate limiter
- Setup Celery với Redis
- Async LLM calls với queuing
- Handle API rate limits gracefully

**Tài liệu tham khảo:**
- 📘 [Celery Documentation](https://docs.celeryq.dev/)
- 💻 [Celery GitHub](https://github.com/celery/celery)
- 📘 [Redis Rate Limiting](https://redis.io/glossary/rate-limiting/)

#### 8.6 Production Deployment
**Lý thuyết:**
- Docker containerization best practices
- FastAPI/Flask API design
- Health checks và monitoring
- Load balancing
- Auto-scaling strategies

**Thực hành:**
- Dockerize LLM application
- Build production API với FastAPI
- Setup monitoring với Prometheus/Grafana
- Deploy to AWS (ECS/EKS)

**Tài liệu tham khảo:**
- 📘 [FastAPI Best Practices](https://fastapi.tiangolo.com/deployment/)
- 📘 [Docker Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- 📘 [AWS ECS Documentation](https://docs.aws.amazon.com/ecs/)
- 💻 [LangServe - LangChain Deployment](https://github.com/langchain-ai/langserve)

#### 8.7 Technical Skills: Git, Docker, AWS
**Git Advanced:**
- Git flow workflow
- Rebasing vs Merging
- Git hooks cho code quality
- Conventional commits

**Docker:**
- Multi-stage builds
- Docker Compose for development
- Volume management
- Network configuration

**AWS:**
- EC2, ECS, Lambda basics
- S3 for storage
- SQS for queuing
- CloudWatch for monitoring
- IAM best practices

**Tài liệu tham khảo:**
- 📘 [Git Best Practices](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- 📘 [Docker Documentation](https://docs.docker.com/)
- 📘 [AWS Well-Architected Framework](https://aws.amazon.com/architecture/well-architected/)

### 📝 Bài tập tuần 8
1. **Notebook 1:** Fine-tune model với LoRA
2. **Notebook 2:** Quantization comparison
3. **Notebook 3:** Caching và Rate limiting implementation
4. **Final Project:** Deploy production-ready RAG chatbot với đầy đủ features

---

## 🎯 Final Project: Production RAG Chatbot

### Yêu cầu
Xây dựng một production-ready RAG chatbot với các features:

1. **Advanced RAG:**
   - Hybrid search (BM25 + Dense + Reranking)
   - Query transformation
   - Parent-child retrieval

2. **Agentic Features:**
   - Function calling cho external tools
   - Human-in-the-loop approval
   - Multi-turn conversation memory

3. **Production Features:**
   - Docker containerization
   - Caching layer
   - Rate limiting
   - Monitoring và tracing
   - API với authentication

4. **Evaluation:**
   - RAGAS evaluation pipeline
   - A/B testing capability

---

## 📖 Tài Liệu Tham Khảo Tổng Hợp

### Books
- 📕 [Building LLM Apps - O'Reilly](https://www.oreilly.com/library/view/building-llm-apps/9781835462317/)
- 📕 [LangChain AI Handbook](https://www.pinecone.io/learn/series/langchain/)

### Courses
- 🎓 [DeepLearning.AI - LangChain Courses](https://www.deeplearning.ai/courses/)
- 🎓 [HuggingFace NLP Course](https://huggingface.co/learn/nlp-course)
- 🎓 [Full Stack LLM Bootcamp](https://fullstackdeeplearning.com/llm-bootcamp/)

### GitHub Repositories
- 💻 [LangChain](https://github.com/langchain-ai/langchain)
- 💻 [LangGraph](https://github.com/langchain-ai/langgraph)
- 💻 [LlamaIndex](https://github.com/run-llama/llama_index)
- 💻 [Instructor](https://github.com/jxnl/instructor)
- 💻 [RAG Techniques](https://github.com/NirDiamant/RAG_Techniques)

### Newsletters & Blogs
- 📰 [The Batch - DeepLearning.AI](https://www.deeplearning.ai/the-batch/)
- 📰 [Chip Huyen's Blog](https://huyenchip.com/blog/)
- 📰 [LangChain Blog](https://blog.langchain.dev/)

---

## 💡 Tips Học Tập

1. **Mỗi ngày dành 2-3 giờ học:** Consistency quan trọng hơn intensity
2. **Học lý thuyết trước, thực hành sau:** Hiểu WHY trước khi làm HOW
3. **Build projects thực tế:** Không chỉ copy code, mà customize cho use case riêng
4. **Tham gia community:** Discord LangChain, Reddit r/LocalLLaMA
5. **Document quá trình học:** Viết blog/notes về những gì đã học
6. **Review code của người khác:** Học từ open-source projects
7. **Mock interviews:** Practice explaining concepts

---

## 📊 Checklist Kiến Thức Senior AI Engineer

### Foundations
- [ ] Giải thích được cách embeddings hoạt động
- [ ] So sánh được bi-encoder vs cross-encoder
- [ ] Implement được BM25 từ scratch
- [ ] Thiết kế được hybrid search system

### Vector Databases
- [ ] Giải thích được HNSW, IVF algorithms
- [ ] Setup và optimize được pgvector
- [ ] Làm việc được với Milvus/Qdrant
- [ ] Benchmark và choose đúng database

### RAG Advanced
- [ ] Implement được HyDE, Multi-Query
- [ ] Thiết kế được Parent-Child retrieval
- [ ] Build được Self-RAG/CRAG system
- [ ] Optimize được cho production

### Prompt Engineering
- [ ] Master Chain-of-Thought patterns
- [ ] Implement được ReAct agents
- [ ] Thiết kế được complex prompts
- [ ] Handle được edge cases

### Tool Use & MCP
- [ ] Function calling với OpenAI/Anthropic
- [ ] Build được custom tools
- [ ] Setup được MCP servers
- [ ] Thiết kế được secure tool systems

### LangGraph & Agents
- [ ] Master state management
- [ ] Implement Human-in-the-loop
- [ ] Build multi-agent systems
- [ ] GraphRAG implementation

### Evaluation & Observability
- [ ] Setup RAGAS evaluation
- [ ] Configure LangSmith/Phoenix
- [ ] Build evaluation pipelines
- [ ] Monitor production systems

### Production
- [ ] Fine-tune với LoRA/PEFT
- [ ] Apply quantization techniques
- [ ] Implement caching strategies
- [ ] Deploy với Docker/AWS

---

**Chúc bạn học tập hiệu quả và sớm trở thành Senior AI Engineer! 🚀**

*Roadmap được thiết kế bởi AI, cần điều chỉnh theo tiến độ và mục tiêu cá nhân.*
