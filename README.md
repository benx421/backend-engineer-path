# Backend Engineer Path

## Read This First

Just so we're clear, I will not be 'nice'. If you haven't already started getting rejection emails, they will soon start coming in. There's no nice way to say "unfortunately, we won't be moving on with your application".

The tech job market is hard because it's supposed to be hard. More often than not, the road will be rough. If you have a few minutes to spare, read [Tai Solarin's "May Your Road Be Rough"](https://megaiconmagazine.com/may-your-road-be-rough-by-tai-solarin/).

It's okay to be confused and not know exactly what to do or in what order to study. That's why I wrote this guide.

**Set realistic expectations:** You're most likely not going to get an entry-level job that pays a lot of money. In fact, money shouldn't be your motivation at this point. You should sincerely want to learn and push yourself.

Perhaps if you were on this path 6 years ago, you wouldn't need to learn as much to get your first job. Times have changed. The entry-level engineer position no longer exists the way it used to. An intern is now expected to perform at junior engineer proficiency. Senior is the new mid-level. You can either complain about how companies no longer invest in training juniors, or dedicate more time to levelling up.

This path is a no-nonsense guide to becoming a backend engineer. It's project-based and set at a high difficulty level. The idea is to simulate actual engineering responsibilities and make you learn by doing.

Backend engineering is abstract. Reading about concepts you can't relate to is boring. Instead of reading about concurrency, you'll build a project that teach you concurrency. When you come across the formal term later, the principle will already be familiar.

**You don't become a software engineer by reading about software or watching tutorials.** You need to write and build software. AI can generate code. You still need to understand what it generated, why it breaks, and how to fix it. That requires writing code yourself.

I've created 3 projects that will prepare you for your first job or help fill knowledge gaps you have. Complete the project first. I know it will be hard. You'll learn from debugging and fixing broken code. After implementation, go through the resources section. Things will make more sense, and you can refactor your implementation accordingly.

**Pick one programming language and stick with it for all three projects.** Jumping between languages dilutes your learning.

Request a code review when you're done, and I'll take a look at my convenience. I'll provide reference implementations in Go, Python or Java.

## Projects

### Project 1: [tweet-audit](https://github.com/benx421/tweet-audit)

**What you'll learn:**

- File I/O operations for parsing large datasets (X archive format)
- HTTP client patterns and third-party API integration (Google Gemini)
- Rate limiting and backpressure handling
- Concurrent processing patterns (batching vs sequential vs full async)
- Error recovery strategies (retry logic, checkpointing, partial failures)
- State management (tracking processed tweets, resumable workflows)
- Configuration management and secrets handling
- Writing testable code with external dependencies

**Core task:** Process your X (Twitter) archive, evaluate each tweet against your alignment criteria using Gemini AI, and generate a CSV of flagged tweets for deletion.

**Resources:**

1. **Language fundamentals:**
   - [Exercism](https://exercism.org/): Complete the track for your chosen language (Go, Python, or Java). Focus on: file I/O, HTTP clients, error handling, concurrency basics.

2. **API integration patterns:**
   - [Google Gemini API Documentation](https://ai.google.dev/docs)
   - [HTTP client best practices: timeouts, retries, exponential backoff](https://developer.mozilla.org/en-US/docs/Web/HTTP/Connection_management_in_HTTP_1.x)
   - [Retry patterns in distributed systems](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/)

3. **Concurrency and batching:**
   - Go: [Go Concurrency Patterns](https://go.dev/blog/pipelines) (worker pools, pipelines)
   - Python: [Python asyncio documentation](https://docs.python.org/3/library/asyncio.html) or [multiprocessing](https://docs.python.org/3/library/multiprocessing.html)
   - Java: [Java Concurrency in Practice](https://jcip.net/): Chapter 6 (Task Execution)
   - [Bulkhead pattern for API rate limiting](https://learn.microsoft.com/en-us/azure/architecture/patterns/bulkhead)

4. **Error handling and resilience:**
   - [Release It! (Chapter 5: Stability Patterns)](https://pragprog.com/titles/mnee2/release-it-second-edition/): Circuit breakers, timeouts
   - [Checkpoint-based recovery for long-running processes](https://martinfowler.com/articles/patterns-of-distributed-systems/log-segmentation.html)
   - [Idempotency patterns](https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/)

**Full project specification:** [github.com/benx421/tweet-audit](https://github.com/benx421/tweet-audit)

### Project 2: [payment-gateway](https://github.com/benx421/payment-gateway)

**What you'll learn:**

- State machine design for payment lifecycles (authorize → capture → refund)
- Idempotency patterns (duplicate requests don't create duplicate charges)
- Retry strategies (distinguish transient failures from permanent ones)
- Distributed transaction coordination (your state vs. the bank's state)
- Failure recovery (what happens if you crash mid-transaction?)
- Error mapping (translating external failures to meaningful client responses)

**Core task:** You will build a payment gateway for FicMart, a fictional e-commerce platform. You'll integrate with a mock bank API that randomly fails, adds latency, and enforces strict state rules. The bank will fail, but your gateway must not fail.

**Resources:**

Read these *while* you build.

1. **Idempotency:**
   - [Implementing Stripe-like Idempotency Keys in Postgres](https://brandur.org/idempotency-keys): Read this when you're designing your idempotency layer. It's the gold standard.

2. **Distributed transactions:**
   - [Designing Data-Intensive Applications, Chapter 9](https://dataintensive.net/): Read when you're confused about what happens when your gateway and the bank disagree.

3. **Failure handling and resilience:**
   - [Timeouts, retries, and backoff with jitter](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/): Read when your retry logic isn't working.
   - [Release It!](https://pragprog.com/titles/mnee2/release-it-second-edition/): Read when you want to understand why systems fail in production.

4. **State machines and domain modeling:**
   - [Domain Modeling Made Functional](https://pragprog.com/titles/swdddf/domain-modeling-made-functional/): Read if your payment states are becoming a mess of booleans and flags.

**Full project specification:** [github.com/benx421/payment-gateway](https://github.com/benx421/payment-gateway)

### Project 3: Traced (Coming Soon)

You'll build a high-throughput trace ingestion API that receives spans from a configurable mock service and displays them in a provided dashboard. Your system must handle massive concurrent writes, manage race conditions, and provide query capabilities within a configurable rolling time window.

**What you'll learn:**

- High-throughput data ingestion
- Time-series data storage patterns
- Handling race conditions under load
- Partitioning strategies
- Query optimisation for recent data

*Full specification and resources will be released when complete.*

## Submitting Work

These projects are deliberately challenging. They simulate real engineering work, not tutorial-level exercises.

Request code reviews when you're done. Include your `TRADEOFFS.md` explaining your architectural decisions. I'll review at my convenience and provide feedback on both your implementation and your reasoning.

**I'll prioritise code review requests for Python, Go, or Java implementations**, but this doesn't mean I won't review other languages. If you implement in TypeScript or anything else, I'll still look at it, but expect slower turnaround times.

This shouldn't take forever. Good luck, and may your road be rough!
