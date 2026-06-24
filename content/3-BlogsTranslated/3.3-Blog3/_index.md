---
title: "Blog 3"
date: 2026-04-20
weight: 3
chapter: false
pre: "<b>3.3. </b>"
---

## OpenSearch Serverless NextGen: Vector Search with Scale-to-Zero for AI Agent Applications

AI agent applications have a very unique load pattern: an agent might fire hundreds of vector queries while reasoning through a task, then go silent for hours. With traditional search infrastructure, you still pay for unused capacity during those idle periods. On May 28, 2026, AWS announced the next generation of **Amazon OpenSearch Serverless** (called NextGen) – a search and vector engine redesigned from the ground up to serve exactly this kind of unpredictable workload.

### What is OpenSearch Serverless NextGen?

NextGen is the new architecture of Amazon OpenSearch Serverless, a fully managed search and vector engine. The core innovation is that it **completely decouples compute and storage** through a shared storage layer, allowing compute capacity to scale independently from data volume. This enables the service to provision resources in seconds and scale down to zero when the application is idle.

AWS names the two architectures: existing collections are now called **Classic**, while the new architecture is **NextGen** and is the default when creating new collections via the Console. In API/CLI, you specify `--generation NEXTGEN` (or `--generation CLASSIC` to keep the old architecture).

### Problems with the Classic Architecture

The original Serverless architecture always maintained a minimum of two OpenSearch Compute Units (OCUs) running constantly. This makes sense for a production search engine with steady load, but is wasteful for agent-style workloads:

- **Paying while idle:** Compute is always provisioned at minimum level, so you still incur costs even with zero queries.
- **Compute tied to storage:** Cannot scale compute independently based on demand without affecting stored data.
- **Slow scaling:** Resource provisioning measured in minutes, unable to keep up with sudden load spikes from agentic workflows.

### How NextGen Works: Decoupling Compute & Storage

The foundational change in NextGen is separating compute from storage. A new shared storage layer is accessed by both Indexing OCUs and Search OCUs, allowing OCUs to scale up and down regardless of how much data is stored. You can have multiple indexes with data without incurring compute costs when not actively indexing or searching.

The architecture diagram below illustrates how NextGen serves an AI agent: the agent creates embeddings via Bedrock and writes to Indexing OCUs; vector queries go through Search OCUs. Both Indexing and Search OCUs (compute tier) scale independently and share a common Shared Storage Layer, enabling scale-to-zero when idle.

![Amazon OpenSearch Serverless NextGen architecture](/images/3-Blog/3.3-Blog3/image1.png)

### Key Highlights & Core Benefits

- **True scale-to-zero:** When no requests arrive within the idle window (10 minutes), the service releases compute and brings OCUs to 0 – stopping compute charges. When traffic returns, capacity recovers in approximately 10 seconds.
- **20x faster scaling:** Provisions resources in seconds and scales capacity 20x faster than the previous generation, handling even the most unpredictable agentic workflows.
- **Up to 60% cost savings:** For workloads with significant idle time, the new architecture reduces infrastructure costs by up to 60% compared to provisioning clusters for peak load.
- **AI-native integration:** Built-in integration with AI development platforms like Vercel and Kiro; part of OpenSearch Agent Skills for direct use in Claude Code, Cursor, and Codex via natural language commands.

### Ideal Use Cases

- **Vector backend for AI agents:** Store and query vector embeddings for RAG and semantic search, paying only when the agent actually queries.
- **Semantic Search:** Maintain vector indexes for natural language queries, replacing self-managed vector databases.
- **Unpredictable workloads:** E.g., e-commerce platforms scaling 10x during flash sales then dropping to zero – instant scaling without pre-provisioning for peaks.
- **Dev/test environments:** Express Create quickly spins up a collection with default policies, useful for experimentation.

### Release Status

The next generation of OpenSearch Serverless was announced on May 28, 2026 and is already GA. At launch, two collection types are supported: full-text search and vector search. Collections can be created via Console, AWS SDK, and AWS CLI; AWS CloudFormation support will follow.

> Note: Shared storage still incurs storage charges per GB/month even when compute has scaled to zero, so the 20x and 60% figures are conditional, tied to specific baselines and workloads with significant idle time.

### Conclusion

OpenSearch Serverless NextGen addresses the exact cost challenge of the AI agent era: bursty load followed by silence. By decoupling compute and storage to enable scale-to-zero, it allows deploying production-ready search and vector backends in minutes, paying only for actual usage. This is a natural fit for RAG and semantic search architectures without the need to self-manage a separate vector database.

### References

- [Introducing the next generation of Amazon OpenSearch Serverless (AWS News Blog)](https://aws.amazon.com/blogs/aws/introducing-the-next-generation-of-amazon-opensearch-serverless-for-building-your-agentic-ai-applications/)
- [The next generation of Amazon OpenSearch Serverless (AWS Big Data Blog)](https://aws.amazon.com/blogs/big-data/the-next-generation-of-amazon-opensearch-serverless-built-from-the-ground-up-for-agents/)
- [Amazon OpenSearch Service Pricing](https://aws.amazon.com/opensearch-service/pricing/)
