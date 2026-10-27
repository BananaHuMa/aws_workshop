---
title: "Proposal"
date: 2026-09-30
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# Enterprise AI Legal & Security Assistant
## A Unified AWS Serverless RAG Solution for Automated Compliance & Legal Retrieval

### 1. Executive Summary
The Enterprise AI Legal & Security Assistant is designed for the FCAJ bootcamp to enable businesses to securely query internal legal documents (e.g., Vietnam's Decree 13/PDPD) and proactively detect compliance violations in newly uploaded contracts. The system leverages a Hybrid, Event-Driven AWS Serverless architecture. As the RAG Architect (Person 1), the focus is on building a robust Document Ingestion and Knowledge Base pipeline that guarantees exact, hallucination-free legal context retrieval through deterministic metadata filtering, bilingual smart chunking, and strict dual-threshold confidence guardrails, all while adhering to a strict $200 project budget.

### 2. Problem Statement
**What’s the Problem?**
Manual legal compliance checks are slow, error-prone, and expensive. Standard off-the-shelf RAG systems fail when processing real-world legal documents: they break complex Vietnamese legal formatting (e.g., splitting "Điều 1" from "Khoản 2"), mix up contexts between government decrees and private contracts, and hallucinate when faced with low-relevance data. Furthermore, processing PDFs in serverless environments often triggers cross-platform compilation errors and timeout crashes.

**The Solution**
The platform uses an event-driven AWS architecture. When a document is uploaded to Amazon S3, it triggers an AWS Lambda function that employs a **Universal Smart Chunker**. This chunker uses specialized bilingual regex (for Vietnamese "Điều/Khoản" and English "Article/Section") with a robust paragraph-based fallback. It redacts PII, stamps metadata (`document_type`, `contract_id`), and saves clean JSON chunks to a processed S3 bucket. Amazon Bedrock Knowledge Base (using Titan Text Embeddings V2 and OpenSearch Serverless) indexes this data. Retrieval is strictly controlled via Metadata Filtering and a Dual-Threshold Guardrail (rejecting scores < 0.50) to guarantee zero cross-contamination and prevent AI hallucinations.

**Benefits and Return on Investment**
The solution establishes a production-grade, reusable ingestion pipeline that guarantees high-precision legal retrieval. It eliminates manual document parsing, ensures strict data privacy via PII redaction, and prevents costly AI hallucinations through deterministic metadata isolation. The architecture is heavily optimized to stay strictly under the $200 bootcamp budget by using pure-Python dependencies (`pypdf`) to avoid complex build pipelines and optimizing chunk sizes to minimize Bedrock token usage.

### 3. Solution Architecture
The platform employs a serverless AWS architecture to manage document ingestion and retrieval. Data is uploaded to a Raw S3 bucket, triggering a Lambda function that extracts, chunks, redacts, and tags the data. Processed JSON chunks are stored in a Processed S3 bucket, which serves as the data source for an Amazon Bedrock Knowledge Base. The architecture is detailed below:

*(Placeholder for Architecture Diagram: S3 Raw -> EventBridge -> Lambda (pypdf + Smart Chunker + PII Redaction) -> S3 Processed -> Bedrock Knowledge Base (Titan Embeddings V2 + OpenSearch Serverless) -> Bedrock Retrieve API with Metadata Filters)*

**AWS Services Used**
- **Amazon S3**: Dual-bucket architecture for raw document storage and processed JSON chunk storage.
- **AWS Lambda**: Event-driven compute for PDF text extraction, smart chunking, and metadata tagging.
- **Amazon Bedrock Knowledge Base**: The core RAG engine for vector storage and semantic retrieval.
- **Amazon OpenSearch Serverless**: The underlying vector database (provisioned via Bedrock Quick Create).
- **Amazon Titan Text Embeddings V2**: Multilingual embedding model to accurately vectorize both Vietnamese and English legal text.

**Component Design**
- **Data Ingestion**: S3 Event Notifications trigger the Lambda function upon file upload to specific folders (`decrees/` or `contracts/`).
- **Data Processing**: Lambda uses `pypdf` (pure Python) to extract text, applies a Universal Smart Chunker (Regex + Paragraph Fallback), redacts PII, and stamps metadata.
- **Data Storage**: Clean, hierarchical JSON chunks are saved to the Processed S3 bucket.
- **Knowledge Base**: Bedrock syncs the S3 bucket, generating embeddings and storing vectors with flat metadata for filtering.
- **Retrieval & Guardrails**: The backend API calls the Bedrock `Retrieve` API with strict `document_type` metadata filters and enforces a dual-threshold confidence score (0.65 for inclusion, 0.50 absolute floor) to prevent hallucinations.

### 4. Technical Implementation
**Implementation Phases**
This project follows a structured 4-phase development cycle:
- **Phase 1: Local Prototyping & Validation**: Develop and test the Universal Smart Chunker and Mock Bedrock API locally using ChromaDB and real Vietnamese/English PDFs to validate regex and fallback logic.
- **Phase 2: AWS Ingestion Pipeline Deployment**: Deploy the Lambda function, resolve cross-platform dependency issues by building a custom `pypdf` Lambda Layer, configure IAM least-privilege policies, and tune compute resources (512MB RAM, 30s timeout) to prevent crashes.
- **Phase 3: Bedrock Knowledge Base Integration**: Provision the Bedrock Knowledge Base, connect the Processed S3 bucket, select Titan Text Embeddings V2, and execute the initial data sync.
- **Phase 4: Universal Dynamic Evaluation & Handoff**: Run the automated self-evaluation script against the live Bedrock KB to prove retrieval precision (>75%), then hand off the `retrieve_with_dynamic_filter` API contract to Person 2 (Prompt Engineer).

**Technical Requirements**
- **Ingestion Engine**: Python 3.12, `pypdf` (for cross-platform compatibility), `boto3`, and advanced Regex for bilingual legal hierarchy parsing.
- **RAG Evaluation**: Custom Python script for Universal Dynamic Self-Evaluation (sampling chunks, generating queries, and verifying 60-character fingerprint retrieval) to prove mathematical precision without hardcoded bias.
- **Security**: Regex-based PII redaction (emails, phone numbers) prior to vectorization.

### 5. Timeline & Milestones
**Project Timeline**
- **Week 1**: Local prototyping, regex refinement, and ChromaDB mock testing.
- **Week 2**: AWS Lambda deployment, custom Layer creation, IAM configuration, and S3 trigger setup.
- **Week 3**: Amazon Bedrock Knowledge Base provisioning, data sync, and metadata filter validation.
- **Week 4**: Universal Dynamic Evaluation, performance tuning, final documentation, and handoff to the LLM/Prompt Engineering team.

### 6. Budget Estimation
The architecture is strictly optimized for the **$200 bootcamp budget limit**.
- **AWS Lambda**: ~$0.00/month (Well within the free tier for moderate document processing).
- **Amazon S3**: ~$0.05/month (Minimal storage for raw PDFs and processed JSON chunks).
- **Amazon Bedrock Knowledge Base (OpenSearch Serverless)**: ~$140.00/month (Minimum 4 OCUs for dev/testing. *Note: Can be paused between demo sessions to save costs, or swapped to Aurora PostgreSQL Serverless for lower baseline costs if required*).
- **Amazon Bedrock (Embeddings & Retrieval)**: ~$10.00 - $20.00/month (Optimized by strict Top-K=5 retrieval and small, semantically dense chunks to minimize token usage).
- **Total Estimated Monthly Cost**: ~$150.00 - $160.05, safely under the $200 cap.

### 7. Risk Assessment
**Risk Matrix**
- **PDF Extraction Failures (Scanned Images)**: Medium impact, medium probability.
- **Lambda Timeouts/Memory Crashes**: High impact, low probability (mitigated).
- **Cross-Platform Dependency Errors**: High impact, medium probability (mitigated).
- **AI Hallucination / Context Mixing**: High impact, medium probability (mitigated).

**Mitigation Strategies**
- **Extraction**: Use `pypdf` for reliable text-based PDF extraction. (Future enhancement: Add Amazon Textract for scanned images).
- **Compute**: Proactively tune Lambda to 512 MB memory and 30-second timeout to handle heavy parsing.
- **Dependencies**: Utilize 100% pure Python libraries (`pypdf`) and custom Lambda Layers to avoid Windows-to-Linux C-extension compilation errors.
- **Hallucination**: Enforce strict Metadata Filtering (`document_type`) and Dual-Threshold Guardrails (rejecting retrieval scores < 0.50) to ensure the LLM only receives highly relevant, isolated context.

### 8. Expected Outcomes
**Technical Improvements:** 
- Automated, metadata-tagged chunking of complex, messy legal documents.
- Deterministic retrieval isolation (zero cross-contamination between decrees and contracts).
- A mathematically proven retrieval precision score via Universal Dynamic Self-Evaluation.

**Long-term Value:**
- A reusable, enterprise-grade serverless ingestion pipeline template that can be adapted for any legal, healthcare, or financial compliance RAG system.
- A robust foundation for Person 2 and Person 3 to build a highly accurate, citation-backed chatbot UI.