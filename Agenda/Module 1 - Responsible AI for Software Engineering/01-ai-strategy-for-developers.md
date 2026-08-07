Understand the fundamentals of the technology. I'm not saying you need to understand every detail, but you should clearly know the aspects that are relevant to your work: what it can do, how to use it effectively, what can improve in the future, what are its fundamental limitations, and what the newest developments are.

## Scope: What we mean when we say "AI"

Artificial intelligence is an umbrella field covering many approaches and technologies. This is a simplified map; in practice, several fields overlap:

```text
Artificial Intelligence            Systems performing tasks associated with human intelligence
|-- Machine Learning                Systems that learn patterns from data
|   |-- Supervised Learning         Learns from examples with known answers
|   |-- Unsupervised Learning       Finds structures in data without labeled answers
|   |-- Reinforcement Learning      Learns actions through rewards and penalties
|   `-- Deep Learning               Uses multilayer neural networks to learn complex patterns
|       |-- Computer Vision         Interprets images and video
|       |-- Speech Processing       Recognizes, understands, or generates speech
|       `-- Generative AI           Creates new content from learned patterns
|           |-- Image/Video Models  Generate or transform visual content
|           `-- LLMs                Understand and generate language and code
|-- Robotics                        Connects perception and decisions to physical actions
|-- Planning and Search             Explores possible actions to reach a goal
`-- Expert Systems                  Applies explicit human-authored rules to a narrow domain
```

Today, when people say "AI," they often really mean **large language models (LLMs)** such as GPT, Claude, or Gemini. LLMs are behind many of the technologies currently receiving attention, including chatbots, coding assistants, copilots, and autonomous agents. This common shorthand is useful, but it is important to remember that LLMs are only one part of the broader AI field.

In **agentic software engineering**, we are more specifically discussing **LLM-powered agents**. These systems can receive a goal, inspect a codebase, plan a solution, use development tools, edit files, run tests, evaluate the results, and iterate toward completing the task.

The LLM provides language understanding, code generation, and reasoning capabilities. The surrounding agentic system adds the context, tools, memory, permissions, and execution loop needed to take action.

Throughout this training, we may use "AI" as convenient shorthand, but the more precise meaning is **LLM-powered agentic systems applied to software engineering**.

## Fundamentals: How LLMs work

LLMs are neural networks based on the **Transformer** architecture. They are trained on enormous amounts of text and code by repeatedly predicting the next token:

> "The developer fixed the bug and ran the..." -> `tests`

To predict well, a model must learn grammar, concepts, facts, relationships, code structures, and common reasoning patterns. Its knowledge is encoded statistically across billions of parameters: it is closer to a **lossy compression of patterns in human knowledge** than a verified database. Post-training then teaches the model to follow instructions and behave like an assistant.

For a deeper, accessible explanation, watch Andrej Karpathy's [Intro to Large Language Models](https://www.youtube.com/watch?v=zjkBMFhNj_g).

## What it can do for developers

This will be demonstrated in **Module 4: AI Across the Software Development Lifecycle**, including codebase onboarding, requirements analysis, design exploration, feature implementation, test generation, debugging, refactoring, code review, security review, documentation, DevOps, and incident response.

## How to use it effectively

This will be covered through:

- **Module 2: AI Developer Productivity Fundamentals:** AI-assisted workflows, prompt and context engineering, repository instructions, plan-first development, and model selection.
- **Module 3: Harness Mastery:** tools, agents, permissions, integrations, automation, and best practices for agentic development.
- **Module 5: Safe Agentic Development:** task decomposition, human approval checkpoints, secure automation, and validation-first development.

## Current limitations

- **Hallucination, largely intrinsic:** Next-token prediction rewards plausible language, not verified truth. Therefore, a model can invent a nonexistent library method and provide convincing documentation for it.

- **Limited grounding, intrinsic to text-only training:** The model learns mainly from words describing reality rather than directly experiencing reality. It can learn that "car," "traffic," "walking," and "car wash" are related, but it has never owned a car, driven through traffic, or physically washed one. Its understanding comes from patterns in text, so it may fail to connect language to the practical constraints of a situation.

  For example:

  > "The car wash is nearby, but traffic is heavy. Should I drive or walk?"

  The model may recognize:

  ```text
  Nearby destination + heavy traffic -> Walk
  ```

  But overlook the physical purpose:

  ```text
  The car needs washing -> The car must be taken there -> Drive
  ```

  Human concepts are grounded in physical experience, goals, and cause and effect. An LLM's concepts are primarily learned through relationships between tokens. This is why it can discuss a situation fluently while occasionally missing something practically obvious.

- **Finite context, architectural and operational:** The model can only reason over information available within its context window, and it may not use every included detail reliably. Therefore, it can violate an architectural constraint documented in a file it did not receive or overlooked.

- **Non-determinism, usually intentional:** Models commonly sample from several probable next tokens rather than always selecting one. Therefore, the same prompt may generate a correct SQL query in one run and a faulty one in another.

- **Prompt sensitivity, largely intrinsic:** Every change to the prompt changes the token sequence on which the model conditions its output. Therefore, "fix this function" may trigger a broad rewrite, while "make the smallest change that passes this test" produces a targeted patch.

- **Long-task drift, partly intrinsic and systemic:** Generated actions become context for later actions, early mistakes compound, and the model has no inherently persistent goal state. Therefore, an agent may begin a refactoring while preserving compatibility but eventually change public APIs.

- **Unreliable confidence, largely intrinsic:** Token probability indicates how plausible the wording is, not whether the underlying claim is true. Therefore, a model may confidently claim that a regular expression handles every edge case even though it fails on Unicode input.

- **Training-data errors and bias, data-dependent:** Models learn patterns from imperfect human text and code. Therefore, they may recommend an outdated or insecure authentication pattern simply because it appears frequently in public repositories.

- **Outdated knowledge, not fundamental:** Knowledge encoded in model weights remains mostly fixed after training. Therefore, a model may claim that version `3.x` is current when `4.x` was released after its training cutoff. Retrieval and tools can address this.

- **Specification dependence, not unique to LLMs:** A model can only optimize the goal and constraints it receives or successfully infers. Therefore, when asked only to "make login faster," it might remove a security check because security was left implicit.

- **Verification gaps, systemic:** Automated checks only verify the behaviors they cover. Therefore, generated code may pass every existing test but fail in production under concurrent requests because concurrency was never tested.

- **Security risks, mixed:** LLMs process instructions and untrusted content through the same natural-language channel. Therefore, a malicious instruction hidden in an issue or README may persuade an agent to read a secret and send it externally. Restricted permissions can limit the damage.

- **Opaque reasoning, largely intrinsic to current neural networks:** Knowledge and computation are distributed across billions of numerical parameters rather than explicit, inspectable rules. Therefore, a model may consistently reject one valid implementation without developers being able to identify the precise internal reason.

- **Cost and latency, implementation-related:** Large models and agentic loops require substantial computation for every token and tool interaction. Therefore, an agent that repeatedly rereads the repository and reruns the full test suite may spend minutes and millions of tokens on a small change.

## What can improve

Models can become more capable and reliable through better training data, larger or more efficient architectures, improved reasoning methods, longer context windows, multimodal input, stronger post-training, and better uncertainty calibration.

Systems can improve further by adding repository context, retrieval, memory, specialized tools, automated verification, human review, and permission to abstain when evidence is insufficient.

## Fundamental limitations

Open-ended generation is optimized for plausible output rather than truth. Better models can reduce hallucinations, but developers should never assume that an unrestricted answer is automatically correct. Reliable systems must ground important claims in evidence and verify consequential outputs.

Current LLMs also do not have human experience, persistent goals, or consistently grounded physical and social understanding. They show real and remarkable capabilities, but those capabilities remain uneven: a model may solve a difficult coding problem and fail a simple everyday situation.

## Staying current without burning out

This is a young, fast-moving field with significant potential impact and investment from many companies. Models, tools, and development practices are improving quickly, so developers should make a reasonable effort to stay informed. Understanding the important advances helps us recognize new opportunities, adapt our practices, and remain competitive.

That does not mean following every model release, tool, feature, benchmark, or social-media announcement. Trying to keep up with everything creates anxiety, burnout, and fear of missing out, while much of what appears exciting today will be replaced or forgotten shortly afterward.

A healthier strategy is to review the field periodically, experiment selectively, and focus on developments that remain useful after the initial hype. If you invest a reasonable amount of time from time to time, you will catch the advances that matter once the dust settles, while avoiding much of the noise.

The goal is not to know everything first. It is to stay informed enough to recognize durable changes and apply them effectively when they become relevant to your work.
