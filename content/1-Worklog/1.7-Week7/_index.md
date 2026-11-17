---
title: "Week 7 Worklog"
date: 2026-11-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Finalize local RAG pipeline prototyping and validate retrieval accuracy before AWS deployment.
* Deploy, troubleshoot, and optimize the serverless data ingestion pipeline on AWS (Lambda, S3, Bedrock).
* Draft, architect, and initiate the technical implementation of the "Legal RAG Platform (Decree 13/2023/NĐ-CP)" proposal.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | - **Local RAG Prototyping & Validation:** <br>&emsp; + Validate pipeline using ChromaDB & multilingual `sentence-transformers` to mimic AWS behavior <br>&emsp; + Develop Universal Smart Chunking Engine (Tier 1: bilingual regex for VN/EN legal hierarchies; Tier 2: fallback paragraph chunker) <br>&emsp; + Implement Dual-Threshold Guardrails (>0.65 to include, <0.50 returns `NO_EVIDENCE_FOUND`) <br>&emsp; + Build Universal Dynamic Self-Evaluation engine (60-char fingerprint matching) | 26/10/2026 | 26/10/2026 | Internal Project Docs |
| 2 | - **AWS Deployment & Engineering Resolutions:** <br>&emsp; + Architect dual-bucket S3 routing (`raw-docs` vs `processed-chunks`) for deterministic metadata stamping <br>&emsp; + Resolve Lambda Layer cross-platform compilation crisis by pivoting from `pdfplumber` to pure-Python `pypdf` <br>&emsp; + Tune Lambda compute resources to 512 MB RAM and 30s Timeout to prevent PDF parsing crashes <br>&emsp; + Configure least-privilege IAM policies and S3 Event Notifications | 27/10/2026 | 27/10/2026 | AWS Lambda & IAM Docs |
| 3 | - **Amazon Bedrock Knowledge Base Integration:** <br>&emsp; + Configure Knowledge Base to ingest pre-chunked JSON directly from S3 <br>&emsp; + Select Amazon Titan Text Embeddings V2 for native multilingual semantic search accuracy <br>&emsp; + Provision Amazon OpenSearch Serverless via Bedrock Quick Create <br>&emsp; + Successfully sync and index 255+ perfectly structured, metadata-tagged JSON chunks | 28/10/2026 | 28/10/2026 | Amazon Bedrock Docs |
| 4 | - **Legal RAG Proposal (Phase 1 & 2):** <br>&emsp; + Define scope and Serverless RAG data flow for Decree 13/2023/NĐ-CP <br>&emsp; + Draft strict System Prompts for absolute context constraint (zero hallucination) <br>&emsp; + Provision DynamoDB `LegalArticles` table <br>&emsp; + Develop Python Lambda function for context retrieval and Groq API (`qwen/qwen3.8-27b`) integration | 29/10/2026 | 29/10/2026 | Internal Project Docs |
| 5 | - **Legal RAG Proposal (Phase 3 & 4):** <br>&emsp; + Configure API Gateway (CORS headers, standardized error handling for 400, 429, 502/504) <br>&emsp; + Deploy S3 Static Website and integrate frontend chat UI with backend API <br>&emsp; + Execute end-to-end testing (via `curl` and web UI), verify LLM accuracy, and finalize $0-cost deployment | 30/10/2026 | 30/10/2026 | AWS API Gateway Docs |

### Week 7 Achievements:

* Successfully validated the local RAG pipeline, achieving mathematically proven retrieval accuracy (**Average Precision > 0.75**) using the Universal Dynamic Self-Evaluation method, eliminating hardcoded bias.
* Resolved critical AWS deployment hurdles, including cross-platform Lambda Layer compilation errors and compute timeout crashes, ensuring a stable, production-ready serverless ingestion pipeline.
* Successfully integrated Amazon Bedrock Knowledge Base with **Titan Text Embeddings V2** and OpenSearch Serverless, indexing 255+ perfectly structured, metadata-tagged chunks with **zero cross-contamination** between document types.
* Drafted and structured the comprehensive technical proposal for the **"Legal RAG Platform (Decree 13/2023/NĐ-CP)"**, defining a highly scalable, $0-cost Serverless architecture (S3, API Gateway, Lambda, DynamoDB, Groq API).
* Delivered the `retrieve_with_dynamic_filter` API contract to the broader team, guaranteeing safe fallback responses (`NO_EVIDENCE_FOUND`) and providing raw S3 URIs for clickable UI citations, ensuring a smooth handoff for the Prompt Engineering and UI phases.