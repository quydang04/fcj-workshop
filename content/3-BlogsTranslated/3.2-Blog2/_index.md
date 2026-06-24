---
title: "Blog 2"
date: 2026-04-20
weight: 2
chapter: false
pre: "<b>3.2. </b>"
---

## Building Reliable Multi-Step Workflows with AWS Lambda Durable Functions

Modern applications often need to handle processes involving multiple sequential steps – such as order processing, user onboarding, or orchestrating AI workflows that make multiple calls to LLMs and external tools. Previously, doing this on AWS Lambda required stitching together Step Functions, SQS, and DynamoDB for state management, resulting in complex infrastructure. At re:Invent 2025, AWS introduced **AWS Lambda Durable Functions** – allowing you to write entire workflows as sequential code within a single Lambda function, while maintaining fault tolerance and long-term pause capabilities.

### What is AWS Lambda Durable Functions?

Durable Functions are regular Lambda functions with **durable execution** mode enabled. This feature extends Lambda's programming model with two new primitives: **step** and **wait**, enabling automatic progress saving (checkpointing), recovery after failures, and pausing execution for up to one year without incurring compute costs while waiting. No additional infrastructure or custom state management code is needed.

The underlying mechanism is **checkpoint and replay**: when a failure occurs, Lambda reruns the function from the beginning but skips completed steps (already checkpointed) and reuses saved results, ensuring no progress is lost.

### Problems with Traditional Lambda

With standard Lambda, your code runs from start to finish in a single invocation and is completely stateless. This creates three major limitations when building complex workflows:

1. **State loss on failure:** If an error occurs at any step, the entire function must be retried from scratch; all state must be manually saved to DynamoDB or S3.
2. **Time limits:** A single execution maxes out at 15 minutes, unsuitable for long-running processes or those requiring human approval.
3. **Manual idempotency:** Developers must protect against duplicate invocations and build safe deployment strategies themselves.

### How It Works: Checkpoint & Replay

Durable Functions solve these problems with two core primitives in the open-source Durable Execution SDK:

- **Step – `context.step()`:** Wraps a block of business logic for automatic checkpointing and retry. Once a step completes, it is skipped during subsequent replays.
- **Wait – `context.wait()` / callback:** Pauses execution for a time period or until an external signal (e.g., human approval). While waiting, the function is terminated with no compute charges, then automatically resumes.

The architecture diagram below illustrates an AI workflow using Durable Functions: a client calls through API Gateway to a Lambda function (with durable execution enabled); the function uses `step()` to call Bedrock (LLM) and save results – each step is automatically checkpointed; uses `wait()`/callback to pause for approval then resume; execution state is emitted to EventBridge and CloudWatch for monitoring.

![AI workflow architecture with AWS Lambda Durable Functions](/images/3-Blog/3.2-Blog2/image1.png)

### Key Highlights & Core Benefits

- **Automatic fault tolerance:** The SDK handles checkpointing and retries with configurable backoff, ensuring idempotency (only one execution runs per request even if upstream retries).
- **Pause for up to one year:** Perfect for human-in-the-loop workflows, approval processes, or scheduled processing – no compute charges while waiting.
- **Same Lambda experience:** Still a Lambda function with the same event handler and integrations; just enable the durable execution toggle when creating the function.
- **Multi-language support:** SDK supports JavaScript, TypeScript, Python, and Java (Java in Developer Preview).

### Ideal Use Cases

- **Multi-step AI workflows:** Orchestrate chains of LLM calls, tool invocations, and result processing with safety against individual call failures.
- **Order processing & payments:** Maintain transaction state across failures with automatic retry; orchestrate authorization, fraud checks, and settlement.
- **Human-in-the-loop approvals:** Document review, leave request approval – pause and wait for human decisions before proceeding.
- **Scheduled / long-running tasks:** Multi-day onboarding, subscription trials, delayed notifications, time-window batch processing.

### Code Example (Python)

After enabling durable execution and adding the SDK, use `DurableContext` to wrap each business logic step:

```python
def handler(event, context):
    # Step 1: call LLM - automatically checkpointed
    summary = context.step("summarize", lambda: call_llm(event))

    # Step 2: wait for approval (no compute cost while waiting)
    decision = context.wait_for_callback("approval")

    # Step 3: only runs when approved
    if decision == "approved":
        context.step("persist", lambda: save_result(summary))
```

> Note: Although the total workflow can span up to one year, each Lambda container still runs for a maximum of 15 minutes between checkpoint/wait points.

### Release Status

Lambda Durable Functions was announced on December 2, 2025 (re:Invent 2025), initially available (GA) in US East (Ohio) with Python and Node.js runtimes, later expanding to more regions. The Java SDK Developer Preview launched on February 26, 2026.

### Conclusion

AWS Lambda Durable Functions eliminates the gap between Lambda's simplicity and the complexity of workflow orchestration systems. Instead of stitching together Step Functions, SQS, and DynamoDB, you write sequential logic in a single function and let the SDK handle checkpointing, retries, and pausing. This is the ideal choice for multi-step AI workflows, order processing, and approval-based processes.

### References

- [Build multi-step applications and AI workflows with AWS Lambda durable functions (AWS News Blog)](https://aws.amazon.com/blogs/aws/build-multi-step-applications-and-ai-workflows-with-aws-lambda-durable-functions/)
- [Building fault-tolerant applications with AWS Lambda durable functions (AWS Compute Blog)](https://aws.amazon.com/blogs/compute/building-fault-tolerant-applications-with-aws-lambda-durable-functions/)
- [AWS Lambda durable functions – Product page](https://aws.amazon.com/lambda/durable-functions/)
