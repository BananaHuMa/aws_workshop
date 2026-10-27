---
title: "Event 3"
date: 2026-10-27
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
# Summary Report: "AWS First Cloud Journey AI - Technical Deep Dives"

### Event Objectives

- Explore building Vietnamese voice-AI contact centers on AWS using cascade and duplex architectures.
- Understand AWS Resource Access Manager (RAM) for secure, multi-account resource sharing and landing zone design.
- Learn about securing web applications with AI-powered autonomous security agents.
- Introduce Amazon Bedrock AgentCore runtime and memory architecture.

### Speakers

- **Kiet Tran** – AI Engineer, Revve AI
- **Thinh Nguyen** – DevSecOps/Cloud Engineer
- **Xuan An** – Leader, AWS Student Builder Group HCMUTE

### Key Highlights

#### Building a Vietnamese Voice-AI Contact Center (Revve AI)
- **The Problem**: Contact centers face traffic peaks, repetitive tasks, and limited QA sampling. Human turn-taking gap is ~200ms.
- **Three Architectures**: 
  - **Cascade (ASR → LLM → TTS)**: Text in the middle acts as a checkpoint. Strong control/guardrails, best for Vietnamese (production today).
  - **Speech-to-Speech (S2S)**: One model, audio in → audio out (e.g., Nova 2 Sonic). Lower latency, keeps tone, but limited Vietnamese support.
  - **Full Duplex S2S**: Two streams always open (e.g., Gemini Live). Lowest latency, backchanneling, but weakest control and mostly English-only.
- **Revve on AWS Architecture**: One region, inside customer's account. Uses EKS, GPU nodes (G6/L4) for speech, and Bedrock via PrivateLink for LLM.
- **Bank POC Results**: 799 test calls, 93% intent match on 871 labelled turns, 35/35 outbound outcomes classified right.
- **Four Lessons Paid For**: 
  1. Benchmark turn detection in your own language (Vietnamese vs English padding mismatch).
  2. Normalize numbers before TTS (e.g., "500K" → "ca").
  3. Use a small judge model to check sentences before TTS to prevent bad output.
  4. Latency budget picks the model (Self-hosted Gemma: 0.24s vs Hosted: 1.15-1.95s).

#### AWS Resource Access Manager (RAM) Fundamentals
- **The Multi-Account Challenge**: Without sharing, resources (Transit GW, DNS rules) are duplicated in every account, leading to drift and high costs. AWS RAM allows creating once and sharing everywhere.
- **Core Concepts**: A resource share is a Regional container holding **Resources** (ARNs), **Managed Permissions** (what consumers can do), and **Principals** (who gets access: accounts, OUs, org).
- **Deep Dive**: 
  - RAM is Regional; global resources (like Cloud WAN) are shared from us-east-1 only.
  - AZ names are mapped randomly per account; always use **AZ IDs** (e.g., `use1-az4`) in IaC for shared subnets.
- **Enterprise Blueprint**: Management account enables org sharing. Infrastructure and Security OUs share resources (Subnets, TGW, Firewall policies) to the Workloads OU (Prod/Non-prod/Data & AI) automatically via membership.
- **Operations**: Monitor with EventBridge (alert on external principals) and CloudTrail (source of truth). Manage as code using CloudFormation or Terraform.

#### Securing Web Apps with AWS Security Agent
- **The Security Bottleneck**: Manual pentests are time-consuming (weeks), expensive ($5k-$20k/engagement), and inconsistent.
- **The Frontier Agent**: Powered by Amazon Bedrock. Features autonomous reasoning, full lifecycle coverage (Design Review → Code Security → Active Pentesting), and verifiable findings (attempts real exploitation).
- **Capabilities**:
  - **Design Review**: Upload Markdown/Terraform, verify against Managed Packs (PCI DSS, NIST CSF). Free Tier: 200 reviews/month.
  - **Code Review**: Integrated into GitHub/GitLab PRs, comments on code, suggests auto-fixes. Free Tier: 1,000 PR reviews/month.
  - **Automated Pentesting**: Multi-step exploit chains (IDOR → XSS), authenticates like a real user, provides attack graphs.
- **Pricing**: $50 per Task-Hour (pay-as-you-go). Real-world case study: $1,500 - $2,500 total cost vs $10,000 for a pentest team.
- **Critical Limitations**: Auth blocks (MFA, Biometrics, mTLS stop the agent), difficulty detecting business-logic fraud without deep context, and task-hour accumulation in complex apps.

#### Amazon Bedrock AgentCore
- **Introduction**: AWS Bedrock AgentCore Unpacked: Master Class on Runtime and Memory Architecture. *(Note: Only title slide provided)*

### Key Takeaways

#### Voice AI Strategy
- **Control vs. Naturalness**: For enterprise/banking in Vietnamese, the **Cascade** architecture is the only production-ready choice due to the need for text-based guardrails and language support. Duplex is on the horizon for pilots.
- **Latency Budget**: The choice of LLM (self-hosted vs. hosted) is dictated by the acceptable latency budget.

#### Multi-Account Architecture
- **Share, don't duplicate**: Use AWS RAM to maintain one resource, one owner, and one policy set.
- **Lean on Organizations**: Use OU-targeted, invitation-free, membership-driven access for automated scaling.
- **Least Privilege**: Layer RAM managed permissions with consumer IAM policies and SCPs.

#### AI in Security
- **Shift Left**: AI agents can perform design and code reviews early in the SDLC, significantly reducing the cost and time of security audits.
- **Verifiable Findings**: Unlike standard LLM chatbots, security agents that attempt real exploitation provide proof of vulnerability.

### Applying to Work

- **Voice AI**: Evaluate cascade architectures for customer service automation, ensuring Vietnamese STT/TTS models are benchmarked locally.
- **Cloud Infrastructure**: Implement AWS RAM for shared VPCs, Transit Gateways, and DNS rules across development and production accounts. Pin shared subnets to AZ IDs in Terraform/CloudFormation.
- **DevSecOps**: Integrate AI security agents into GitHub/GitLab workflows for automated PR reviews and design verification against compliance frameworks.
- **Agent Development**: Explore Amazon Bedrock AgentCore for building advanced AI agents with persistent memory and runtime management.

### Event Experience

Attending the **AWS First Cloud Journey AI** event was extremely valuable, providing a comprehensive view of how AI and modern cloud architectures are solving real-world enterprise problems. Key experiences included:

#### Learning from industry practitioners
- **Kiet Tran** shared hard-won lessons from deploying Vietnamese voice AI in a top-tier bank, highlighting the importance of language-specific benchmarking and the trade-offs between cascade and duplex models.
- **Thinh Nguyen** demonstrated how AI is transforming the security landscape, moving from manual, expensive pentests to autonomous, verifiable agent-based testing.

#### Deep technical architecture insights
- The **AWS RAM** session provided a clear blueprint for enterprise landing zones, emphasizing the critical detail of using AZ IDs instead of AZ names for cross-account subnet sharing.
- The **Revve on AWS** architecture diagram illustrated a practical, secure deployment model using PrivateLink for Bedrock and GPU nodes for speech processing within the customer's own account.

#### Practical takeaways
- Learned that **latency budgets dictate model selection** in voice AI; a 0.24s self-hosted model is vastly different from a 1.95s hosted model in a conversational context.
- Understood the **defense-in-depth** approach in AWS RAM, where consumer IAM and SCPs still apply on top of the shared resource permissions.
- Recognized the **limitations of AI security agents**, particularly their inability to bypass MFA or understand deep business logic, reinforcing the need for human oversight in complex scenarios.

#### Some event photos
![alt text](../../images/event3.1.png)

> Overall, the event provided a dense, technical deep dive into cutting-edge AWS services, from voice AI and resource sharing to autonomous security agents, reshaping my understanding of how to build secure, scalable, and intelligent systems on the cloud.