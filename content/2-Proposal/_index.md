---
title: "Proposal"
date: 2026-10-15
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
In this section, you need to summarize the contents of the project that you **plan** to conduct.

# Automated Legal RAG Platform (Decree 13/2023/ND-CP)
## A Serverless LLM Solution for Real-Time Legal Data Retrieval and Analysis

### 1. Executive Summary
The Automated Legal RAG Platform is designed to assist users and team members in quickly retrieving and analyzing complex legal regulations in Vietnam, specifically focusing on Decree 13/2023/ND-CP on personal data protection. The platform leverages a comprehensive Serverless architecture on AWS combined with a powerful Large Language Model via Groq API (qwen/qwen3.8-27b). This solution delivers highly accurate, context-aware queries, eliminating AI hallucination, while minimizing operational costs to nearly $0 by fully utilizing the AWS Free Tier.

### 2. Problem Statement
**What’s the Problem?**
Legal documents such as Decree 13/2023/ND-CP are lengthy, dry, and difficult for non-experts to manually navigate and search. Standard general-purpose AI tools (like the free tier of ChatGPT) often lack deep knowledge of Vietnamese law and tend to provide vague answers without an accurate legal basis. Furthermore, building a self-hosted AI system is typically hardware-intensive and requires complex server management.

**The Solution**
Implement an automated RAG (Retrieval-Augmented Generation) pipeline: When a user asks a question, the system scans the database to retrieve the most accurate legal clauses and injects them into the System Prompt. The LLM then processes this information to deliver an answer with clear legal citations. The platform utilizes Amazon DynamoDB to store extracted legal clauses (`LegalArticles`), AWS Lambda for backend RAG logic processing combined with Amazon API Gateway for a stable API Endpoint, Groq API with the `qwen/qwen3.8-27b` model for intelligent natural language generation, and an Amazon S3 Static Website for intuitive user interaction.

**Benefits and Return on Investment (ROI)**
The solution guarantees high accuracy by strictly following provided legal context, ensuring transparency and valid grounding. It achieves extreme cost optimization by operating entirely on a Serverless model, maximizing the AWS Free Tier to keep monthly maintenance costs at $0. Additionally, the decoupled architecture ensures high scalability, allowing for the easy addition of new legal frameworks (e.g., Cybersecurity Law, IT Law) to DynamoDB in the future.

### 3. Solution Architecture
The system employs a Serverless architecture, seamlessly connecting the Frontend, Backend, and external LLM. Data flows from the user interface through the API Gateway to the Lambda function, which retrieves context from DynamoDB and queries the Groq API. The architecture is detailed below:

*(Placeholder for Architecture Diagram: S3 Static Website -> API Gateway -> AWS Lambda (RAG Logic) -> Amazon DynamoDB (LegalArticles) & Groq API (qwen/qwen3.8-27b))*

**AWS Services & Technologies Used**
- **Amazon S3 Static Website**: Stores and serves the static website interface (index.html, CSS, JS) to users.
- **Amazon API Gateway**: Provides a public HTTP/REST API, handles CORS, and acts as the entry point for client requests to Lambda.
- **AWS Lambda (Python)**: Executes the backend source code to process RAG logic, retrieve data from DynamoDB, and interact with the Groq API.
- **Amazon DynamoDB (LegalArticles)**: Stores the structure of legal clauses, supporting high-speed keyword queries.
- **Groq API (qwen/qwen3.8-27b)**: Synthesizes and analyzes natural language based on the injected legal context.

**Component Design**
- **User Interface (Frontend)**: Users access the website from S3 and type questions into the chat box. The browser sends an HTTPS POST Request containing the question to the API Gateway.
- **Gateway (API Gateway)**: Receives the request, checks CORS security headers, and forwards the data payload to the Lambda function.
- **Data Retrieval (DynamoDB)**: Lambda executes the `retrieve_legal_context` function to scan and search for relevant clauses in the `LegalArticles` table (e.g., penalty regulations related to Citizen ID cards and personal data).
- **Augmentation & Generation (Groq API)**: Lambda packages the user's question along with the retrieved legal context into a strictly constrained System Prompt, then calls the Groq API.
- **Response Flow**: Groq returns the result to Lambda, which formats the data into a standard JSON structure and sends it back via API Gateway to be displayed on the user's chat interface.

### 4. Technical Implementation
**Implementation Phases**
This project follows a structured 3-phase development cycle:
- **Phase 1: Prompt Setup & RAG Mechanism**: Build the System Prompt defining the AI's role as a legal expert and establish Context Constraints to absolutely prevent information fabrication (hallucination).
- **Phase 2: Backend & Database Deployment**: Create the DynamoDB table `LegalArticles`. Write Python code on AWS Lambda integrating data retrieval functions and Groq API calls. Configure API Gateway, enable CORS Headers, and build standardized error handling (returning code 400 for invalid data, 502/504 for system errors, and handling code 429 for Groq API rate limits).
- **Phase 3: Testing & Refinement**: Use the `curl` command to send test HTTP POST requests or test directly on the web interface, and verify logs on Amazon CloudWatch.

**Technical Requirements**
- **Backend Engine**: Python for AWS Lambda, `boto3` for DynamoDB and AWS service integration, and HTTP clients for Groq API calls.
- **Database Schema**: DynamoDB `LegalArticles` table optimized for high-speed keyword queries and context retrieval.
- **Prompt Engineering**: Strictly constrained System Prompt enforcing responses based *only* on the provided DynamoDB context.

### 5. Timeline & Milestones
**Project Timeline**
- **Week 1**: Research & Design phase. Define the legal scope (Decree 13/2023/ND-CP), design the RAG data flow, and draft the System Prompt.
- **Week 2**: Development & Deployment phase. Build the DynamoDB database, complete the Lambda function, configure the API Gateway, and set up the S3 static website.
- **Week 3**: Integration & Testing phase. Connect the frontend with the API Gateway, test the accuracy of answers from the Groq LLM, optimize error handling, and finalize documentation.

### 6. Budget Estimation
The architecture is strictly optimized to operate at **$0 monthly cost** by fully utilizing free tiers.
- **Amazon S3**: $0.00/month (Within Free Tier limits for static website hosting).
- **Amazon API Gateway**: $0.00/month (Free for the first 1 million requests/month).
- **AWS Lambda**: $0.00/month (Free for the first 1 million requests/month).
- **Amazon DynamoDB**: $0.00/month (Free for 25GB storage, 25 WCU / 25 RCU).
- **Groq API**: $0.00/month (Free tier utilized for the open-source model `qwen/qwen3.8-27b`).
- **Total Project Investment**: $0.00 (0 VNĐ) / month.

### 7. Risk Assessment
**Risk Matrix**
- **API Overload (Rate Limit 429 from Groq API)**: Medium impact, medium probability.
- **AI Hallucination**: High impact, medium probability (mitigated).
- **Browser CORS Errors**: High impact, low probability (mitigated).

**Mitigation Strategies**
- **API Overload**: Implement robust Error Handling mechanisms and display friendly notification messages on the chat interface when the system temporarily exceeds call frequency limits.
- **AI Hallucination**: Tighten the System Prompt with strict rules requiring the use of *only* the legal context provided by DynamoDB, strictly forbidding external deduction or fabrication.
- **CORS Errors**: Fully configure CORS Headers (`Access-Control-Allow-Origin: *`, `POST`, `OPTIONS`) directly within the API Gateway settings to ensure seamless browser-to-backend communication.

### 8. Expected Outcomes
**Technical Improvements:** 
- Successfully deploy a complete, auto-scaling, and stable Serverless Backend.
- Optimize operational costs to an absolute minimum ($0) through strategic use of AWS Free Tier and Groq's free tier.
- Eliminate AI hallucinations via strict RAG context injection and constrained System Prompts.

**Long-term Value:**
- Provide a standardized API endpoint and an intuitive chat interface to quickly and accurately query core regulations within Decree 13/2023/ND-CP.
- Effectively serve academic research and practical study needs.
- Create a highly scalable foundation that allows for the seamless integration of additional legal frameworks (e.g., Cybersecurity Law, IT Law) in the future.