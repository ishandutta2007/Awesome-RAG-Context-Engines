# Awesome-RAG-Context-Engines

## Top RAG & Context Engines Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Deep Document Understanding, Layout-Aware Parsing & Grounded Generation*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **RAG & Context Engines**. These tools provide the retrieval and context layer between your documents and an LLM — handling parsing, chunking, embedding, indexing, and retrieval so the model receives high-fidelity evidence rather than noisy text.

**Examples** include RAGFlow, Vectara, Pinecone Nexus, Weaviate, Qdrant, Chroma, Elasticsearch Vector Database, Zilliz, Marqo, and SciPhi R2R (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, vision-native document parsing, and transparent retrieval — ideal for teams prioritizing data sovereignty, avoiding vendor lock-in, and building context engines they can audit and control.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Vectara](https://www.vectara.com/)**  
  **RAG-as-a-Service through a single API.** Handles document ingestion, chunking, embedding, retrieval, reranking, and generation with built-in hallucination detection and citation extraction [citation:15]. **Deployment options include SaaS, VPC, and on-premise** for data sovereignty [citation:15]. Founded by former Google executives with deep search and ML expertise [citation:15]. **Limitations**: credit-based pricing requires usage tracking; proprietary vector database may limit portability [citation:15].

- **[Pinecone Nexus](https://www.pinecone.io/)**  
  **The retrieval-native RAG platform from the managed vector database leader.** Distills sources into **curated artifacts** — summaries, topics, entities, events — that are pre-computed and easy to retrieve [citation:4]. At query time, the model **writes Python against a retrieval SDK** to read artifacts, run semantic and keyword search, walk relationship graphs, and query structured tables [citation:4]. **Only distilled evidence enters the prompt**, keeping context small and every claim traceable [citation:4]. **Handles exact counts and enumerations** via SQL over typed artifact tables [citation:4]. **Best for large, messy corpora** where answer quality matters more than ingestion speed.

- **[Weaviate Cloud](https://weaviate.io/)**  
  **Managed vector database with a turnkey RAG path.** **Query Agent** handles ingest, chunk, retrieve, and answer on Weaviate Cloud [citation:5]. For full control, use `col.query.hybrid(...)` to combine vector and BM25 retrieval with filters, then send results to any LLM [citation:5]. **Free to start across the entire product suite** as of June 2026 [citation:5].

- **[Elasticsearch Vector Database](https://www.elastic.co/)**  
  **Serverless vector search for RAG and agents, built on the platform where your data already lives.** **`vectordb_document` index mode** is on by default with **bfloat16 storage** (half the disk footprint of float32), excluded source vectors, and parallel merging [citation:9]. **Better Binary Quantization (BBQ)** shrinks vector memory footprints by up to 32x while preserving recall [citation:9]. **Auto-calibration** tunes quantization per segment and retunes on merge — QPS improved by an average of **16.7%** across 18 datasets [citation:9]. **Managed GPU inference** via Elastic Inference Service with native Jina AI embedding and reranking models [citation:9].

- **[SciPhi R2R](https://www.sciphi.ai/)**  
  **Enterprise-grade RAG infrastructure with agentic RAG, ingestion, and document management.** **HybridRAG combines knowledge graphs and vector retrieval** for context-rich responses; claims **150% improved accuracy** [citation:11]. **Universal document processing across 40+ formats**; **granular permissions down to document level** [citation:11]. **R2R** is the open-source core — available as a self-hostable API server.

## Open-Source GitHub Projects

- **[RAGFlow](https://github.com/infiniflow/ragflow)**  
  **The leading open-source RAG engine with deep document understanding** — Apache 2.0 licensed, **133,000+ GitHub stars** [citation:14]. **DeepDoc vision-native layout parsing** uses YOLOv8-based layout detection to segment documents before OCR — preserving column/row coordinate mappings for tables and auto-rotating scanned tables [citation:1]. **Template-based chunking** (Law, Manual, Book, Paper, Resume, Table) matches parsing strategy to document semantics [citation:13]. **Hybrid retrieval** (BM25 + dense vector RRF) with **pixel-exact bounding box citations** linking answers to specific visual regions [citation:1]. **Graph RAG support** for capturing relationships across documents [citation:13]. **Native integration** with frontier models including Claude, GPT, Gemini, DeepSeek, Gemma, and Qwen [citation:1]. **April 2026 release** added prebuilt ingestion pipelines, sandbox code execution, and chart generation [citation:1]. **Trade-offs**: **high resource requirements** — 16GB+ RAM and GPU recommended for production parsing latency below 2 seconds per page [citation:1][citation:13]. **Best for legal, financial, healthcare, and technical document Q&A** where table extraction and citation-grade answers matter [citation:1][citation:13].

- **[Qdrant](https://github.com/qdrant/qdrant)**  
  **The leading open-source vector database for filter-heavy RAG workloads.** **Native hybrid search** — dense vector plus BM25 sparse via **RRF fusion** using Qdrant's built-in fastembed integration [citation:6]. **`QdrantRAG`** provides a complete RAG interface with `add_directory`, hybrid/vector/BM25 search modes, and configurable chunking [citation:6]. **Sub-millisecond query latency** with optional GPU acceleration.

- **[Chroma](https://github.com/chroma-core/chroma)**  
  **The lightweight, developer-friendly vector database for RAG prototyping** — Apache 2.0 licensed [citation:7]. **`pip install chromadb`** and you're running locally in seconds; **persistent storage** avoids data loss without manual index or cluster configuration [citation:7]. **Four-function core API**: create collection, add documents, query, and get by ID [citation:7]. **Chroma Cloud** powers serverless vector, hybrid, and full-text search with **$5 free credits** to start [citation:7]. **Best for beginners and mid-scale RAG** — migrate to Qdrant or Milvus beyond single-machine capacity.

- **[Zilliz / Milvus](https://github.com/milvus-io/milvus)**  
  **The open-source distributed vector database for billion-scale workloads.** **Zilliz Cloud** is the fully managed service with enterprise-grade performance and scalability [citation:8]. **Vectorize integration** automates RAG pipelines — connecting data sources, selecting embedding models, and keeping vector indexes updated as source data evolves [citation:8]. **Best for teams needing managed Milvus** with automated pipeline maintenance.

- **[Marqo](https://github.com/marqo-ai/marqo)**  
  **AI-native search and product discovery platform.** **Hybrid search** combining lexical and neural retrieval; **typeahead search** for intelligent query suggestions from partial input [citation:10]. **Base64 image embedding caching** cuts vectorization time from ~10ms to ~1ms for reused images [citation:10]. **Best for e-commerce and domain-specific applications** where catalog-specific intelligence improves relevance.

### Additional Strong Open-Source Options

- **LlamaIndex** — Purpose-built data framework for RAG with 160+ connectors, indexing strategies, and query engines.
- **Haystack** — Typed, explicit-component framework for production RAG with auditable DAG pipelines.
- **Kotaemon** — Local-first RAG UI with visual citations and multi-vector retrieval.
- **Verba** — Weaviate's open-source RAG application with sensible defaults for quick starts.
- **R2R (self-hosted)** — SciPhi's open-source agentic RAG core with hybrid search and knowledge graphs [citation:11].

**Frameworks for building custom systems**: Combine **RAGFlow** for vision-native document parsing with pixel-exact citations, **Qdrant** for filter-heavy hybrid retrieval, **Chroma** for rapid prototyping, **Elasticsearch Vector Database** for serverless vector search on existing Elastic infrastructure, and **Pinecone Nexus** for curated-artifact retrieval with exact counts — to build a context engine tailored to your document complexity, citation requirements, and infrastructure constraints.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- RAG and context engines differ significantly in document parsing quality, retrieval approach, and infrastructure requirements. **RAGFlow's DeepDoc vision parsing has the best document understanding in the OSS RAG space** but requires 16GB+ RAM and GPU for production latency [citation:1][citation:13]. **Pinecone Nexus replaces chunk retrieval with curated artifacts and code-based evidence gathering** — solving exact counts and traceability [citation:4]. **Chroma is for prototyping** — migrate beyond single-machine capacity [citation:7]. **Vector search returns semantically similar content, not necessarily relevant content** — document structure and retrieval strategy matter as much as the embedding model.
- Self-hosted open-source solutions require proper document parsing configuration, embedding model selection, and retrieval quality evaluation against your specific document corpus.

---

**Made for AI engineers, RAG developers, and teams building document intelligence and context systems.**
Let's make RAG and context engines more open, traceable, and document-aware.
