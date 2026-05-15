# Awesome Recursive Language Models

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Scope: Recursive AI Systems](https://img.shields.io/badge/scope-recursive%20AI%20systems-blue)](#awesome-recursive-language-models)
[![Updated: 2026](https://img.shields.io/badge/updated-2026-brightgreen)](#awesome-recursive-language-models)

> Resources on recursive language models, recursive inference, recursive reasoning architectures, and self-calling AI systems.

Recursive systems matter because they allow models and agents to decompose context, call sub-processes, refine intermediate outputs, verify assumptions, and organise longer-horizon computation.

## Taxonomy

| Pattern | Description | Example resources |
| --- | --- | --- |
| Self-recursive inference | Model calls itself on bounded sub-contexts. | RLM, λ-RLM |
| Tree recursion | Expands and evaluates branches. | ToT, LATS, MCTS methods |
| Graph recursion | Reasoning states form reusable graph structures. | GoT |
| Iterative refinement | Output-feedback-revision loops. | Self-Refine, Reflexion |
| Recursive architectures | Recurrent or weight-shared reasoning modules. | HRM, TRM, RSM |
| Recursive retrieval | Hierarchical abstraction over context. | RAPTOR |
| Recursive self-improvement | System modifies policy, code, prompts, or search process. | STOP, Gödel Agent, Polaris |
| Simulation recursion | Agents recursively plan, reflect, update beliefs, and interact. | Generative Agents, AgentSociety, SOTOPIA |

## Contents

- [Taxonomy](#taxonomy)
- [Core Papers](#core-papers)
- [Recursive Language Models](#recursive-language-models)
- [Recursive Reasoning Architectures](#recursive-reasoning-architectures)
- [Inference-Time Recursion](#inference-time-recursion)
- [Recursive Agents and Tool Environments](#recursive-agents-and-tool-environments)
- [Recursive Evaluation and Verification](#recursive-evaluation-and-verification)
- [Recursive Planning and Search](#recursive-planning-and-search)
- [RL and Self-Improving Systems](#rl-and-self-improving-systems)
- [Simulation Recursion and Social Simulation](#simulation-recursion-and-social-simulation)
- [Benchmarks and Evaluation Tasks](#benchmarks-and-evaluation-tasks)
- [Open-Source Implementations](#open-source-implementations)
- [Contributing](#contributing)
- [Maintainer Notes](#maintainer-notes)

## Core Papers

- [Recursive Language Models](https://arxiv.org/abs/2512.24601) - Introduces RLMs as an inference strategy where an LLM uses an external environment to inspect, decompose, and recursively call itself over long prompts. (2025)
- [Reasoning Language Models: A Blueprint](https://arxiv.org/abs/2501.11223) - Provides a modular blueprint for reasoning language models, covering chains, trees, graphs, nested reasoning, search, reinforcement learning, supervision, and test-time compute. (2025)
- [Recursive Models for Long-Horizon Reasoning](https://arxiv.org/abs/2603.02112) - Formalises recursive model self-invocation for long-horizon reasoning under bounded context and evaluates recursive reasoning on Boolean satisfiability. (2026)
- [Recursion of Thought: A Divide-and-Conquer Approach to Multi-Context Reasoning with Language Models](https://arxiv.org/abs/2306.06891) - Introduces recursive multi-context reasoning where model outputs can trigger subproblem contexts beyond a single sequence window. (2023)
- [Tree of Thoughts: Deliberate Problem Solving with Large Language Models](https://arxiv.org/abs/2305.10601) - Frames reasoning as search over intermediate "thought" states with generation, self-evaluation, and selection. (2023)
- [Self-Refine: Iterative Refinement with Self-Feedback](https://arxiv.org/abs/2303.17651) - Uses the same LLM as generator, feedback provider, and refiner in an inference-time improvement loop. (2023)
- [Self-Taught Optimizer (STOP): Recursively Self-Improving Code Generation](https://arxiv.org/abs/2310.02304) - Studies a scaffolding programme that uses a language model to modify code that can call itself for further improvement. (2023)

## Recursive Language Models

See the core papers above for recursive self-invocation and multi-context recursion.

- [Recursive Language Models](https://alexzhang13.github.io/blog/2025/rlm/) - Project blog post explaining RLMs, REPL environments, recursive subcalls, and early long-context experiments. (2025)
- [The Y-Combinator for LLMs: Solving Long-Context Rot with Lambda-Calculus](https://arxiv.org/abs/2603.20105) - Introduces λ-RLM, a typed functional approach to recursive language-model inference with explicit control flow, termination guarantees, and cost bounds. (2026)
- [RAPTOR: Recursive Abstractive Processing for Tree-Organized Retrieval](https://arxiv.org/abs/2401.18059) - Builds a recursive tree of clustered summaries so retrieval can operate over both local chunks and higher-level abstractions. (2024)

## Recursive Reasoning Architectures

See Tree of Thoughts in the core papers for the canonical tree-search framing.

- [Graph of Thoughts: Solving Elaborate Problems with Large Language Models](https://arxiv.org/abs/2308.09687) - Represents LLM-generated units of reasoning as graph nodes that can be transformed, scored, aggregated, and looped. (2023)
- [Algorithm of Thoughts: Enhancing Exploration of Ideas in Large Language Models](https://arxiv.org/abs/2308.10379) - Prompts models with algorithmic reasoning trajectories to encourage structured exploration with recurrent dynamics. (2023)
- [Cumulative Reasoning with Large Language Models](https://arxiv.org/abs/2308.04371) - Coordinates proposer, verifier, reporter, and halter roles in an iterative reasoning process. (2023)
- [Everything of Thoughts: Defying the Law of Penrose Triangle for Thought Generation](https://arxiv.org/abs/2311.04254) - Combines thought generation with reinforcement learning and Monte Carlo Tree Search for multi-solution problem solving. (2023)
- [THREAD: Thinking Deeper with Recursive Spawning](https://aclanthology.org/2025.naacl-long.427/) - Frames generation as threads that recursively spawn child threads for task solving and question answering. (2025)
- [Hierarchical Reasoning Model](https://arxiv.org/abs/2506.21734) - Proposes a recurrent reasoning architecture with high-level and low-level modules operating at different timescales for sequential reasoning tasks. (2025)
- [Less is More: Recursive Reasoning with Tiny Networks](https://arxiv.org/abs/2510.04871) - Proposes Tiny Recursive Model, a small-network architecture that recursively refines latent state and answers on puzzle tasks. (2025)
- [Form Follows Function: Recursive Stem Model](https://arxiv.org/abs/2603.15641) - Introduces a recursive reasoning model trained as a stable depth-agnostic transition operator, with test-time recursion and convergence behaviour as a reliability signal. (2026)

## Inference-Time Recursion

- [Scaling LLM Test-Time Compute Optimally can be More Effective than Scaling Model Parameters](https://arxiv.org/abs/2408.03314) - Studies how search, revision, and verifier-guided strategies allocate extra inference-time compute. (2024)
- [Large Language Monkeys: Scaling Inference Compute with Repeated Sampling](https://arxiv.org/abs/2407.21787) - Analyses repeated sampling as a test-time compute strategy whose value depends on verification and selection. (2024)
- [Test-time Recursive Thinking: Self-Improvement without External Feedback](https://arxiv.org/abs/2602.03094) - Proposes an inference-time recursive thinking framework that uses rollout strategies, accumulated knowledge, and self-generated verification signals for self-improvement. (2026)
- [Self-Evaluation Guided Beam Search for Reasoning](https://arxiv.org/abs/2305.00633) - Integrates self-evaluation into stochastic beam search for multi-step reasoning. (2023)
- [What, How, Where, and How Well? A Survey on Test-Time Scaling in Large Language Models](https://arxiv.org/abs/2503.24235) - Surveys test-time scaling methods, including search, verifier-guided reasoning, and adaptive deliberation. (2025)
- [A Survey of Efficient Reasoning for Large Reasoning Models: Language, Multimodality, and Beyond](https://arxiv.org/abs/2503.21614) - Surveys inefficient reasoning patterns in large reasoning models, including redundant traces, over-analysis, and methods for improving reasoning efficiency. (2025)

## Recursive Agents and Tool Environments

- [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629) - Interleaves reasoning traces, actions, and observations in a loop for tasks that require external interaction. (2022)
- [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) - Converts task feedback into verbal reflection stored in memory for later attempts. (2023)
- [Language Agent Tree Search Unifies Reasoning Acting and Planning in Language Models](https://arxiv.org/abs/2310.04406) - Combines reflection, acting, and planning through Monte Carlo Tree Search over agent trajectories. (2024)
- [Voyager: An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) - Uses environment feedback, self-verification, and an expanding skill library for lifelong embodied exploration. (2023)
- [Toolformer: Language Models Can Teach Themselves to Use Tools](https://arxiv.org/abs/2302.04761) - Trains models to decide when and how to call tools using self-supervised API-call annotations. (2023)

## Recursive Evaluation and Verification

- [Maieutic Prompting: Logically Consistent Reasoning with Recursive Explanations](https://arxiv.org/abs/2205.11822) - Builds a recursive tree of explanations and solves consistency as a satisfiability problem. (2022)
- [Let's Verify Step by Step](https://arxiv.org/abs/2305.20050) - Compares process supervision with outcome supervision and releases step-level feedback data for mathematical reasoning. (2023)
- [V-STaR: Training Verifiers for Self-Taught Reasoners](https://arxiv.org/abs/2402.06457) - Iteratively trains reasoners and verifiers from self-generated reasoning data. (2024)
- [Pride and Prejudice: LLM Amplifies Self-Bias in Self-Refinement](https://arxiv.org/abs/2402.11436) - Examines self-bias risks in self-refinement loops and the role of external feedback. (2024)

## Recursive Planning and Search

- [Reasoning with Language Model is Planning with World Model](https://arxiv.org/abs/2305.14992) - Uses an LLM as both agent and world model inside Monte Carlo Tree Search for reasoning and planning. (2023)
- [LiteSearch: Efficacious Tree Search for LLM](https://arxiv.org/abs/2407.00320) - Proposes a tree-search method that allocates expansion based on history and value guidance. (2024)
- [Monte Carlo Tree Search Boosts Reasoning via Iterative Preference Learning](https://arxiv.org/abs/2405.00451) - Uses MCTS to collect step-level preference data for iterative reasoning improvement. (2024)

## RL and Self-Improving Systems

See STOP in the core papers for recursively self-improving code-generation scaffolds.

- [Toward Self-Improvement of LLMs via Imagination, Searching, and Criticizing](https://arxiv.org/abs/2404.12253) - Combines generated candidate reasoning paths, search, and critique for self-improvement without extra annotations. (2024)
- [ReGenesis: LLMs can Grow into Reasoning Generalists via Self-Improvement](https://arxiv.org/abs/2410.02108) - Uses self-synthesised reasoning paths as training data to improve reasoning generalisation. (2024)
- [Gödel Agent: A Self-Referential Agent Framework for Recursive Self-Improvement](https://arxiv.org/abs/2410.04444) - Proposes a self-referential agent framework for recursively modifying its own behaviour. (2024)
- [Polaris: A Gödel Agent Framework for Small Language Models through Experience-Abstracted Policy Repair](https://arxiv.org/abs/2603.23129) - Proposes an auditable recursive self-improvement loop where an agent analyses failures, abstracts experience, and applies minimal policy repairs. (2026)
- [LADDER: Self-Improving LLMs through Recursive Problem Decomposition](https://arxiv.org/abs/2503.00735) - Uses recursive generation of easier problem variants to create a difficulty gradient for self-guided learning and test-time reinforcement learning. (2025)
- [A Simple Framework for Intrinsic Reward-Shaping for RL using LLM Feedback](https://alexzhang13.github.io/assets/pdfs/Reward_Shaping_LLM.pdf) - Iteratively generates and refines intrinsic reward functions with LLM feedback for reinforcement learning environments. (2025)
- [AlphaEvolve: A coding agent for scientific and algorithmic discovery](https://arxiv.org/abs/2506.13131) - Describes an evolutionary coding agent that uses LLMs, automated evaluators, and iterative programme improvement. (2025)

## Simulation Recursion and Social Simulation

- [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) - Introduces LLM-based agents with memory, reflection, and planning for simulating believable individual and emergent social behaviour. (2023)
- [AgentSociety](https://arxiv.org/abs/2502.08691) - Introduces a large-scale simulator for LLM-driven social agents, supporting population-level interactions and computational social experiments. (2025)
- [SocioVerse](https://arxiv.org/abs/2504.10157) - Proposes an LLM-agent-driven world model for large-scale social simulation, with alignment components for users, environments, interactions, and behavioural patterns. (2025)
- [SOTOPIA-S4: a user-friendly system for flexible, customizable, and large-scale social simulation](https://arxiv.org/abs/2504.16122) - Presents a scalable system for customisable multi-turn and multi-party LLM-based social simulation with APIs and a web interface. (2025)
- [GASim: A Graph-Accelerated Hybrid Framework for Social Simulation](https://arxiv.org/abs/2605.07692) - Proposes a graph-accelerated hybrid framework for scalable social simulation with LLM-driven core agents, graph memory, and graph message passing. (2026)
- [Designing Reliable Experiments with Generative Agent-Based Modeling: A Comprehensive Guide Using Concordia by Google DeepMind](https://arxiv.org/abs/2411.07038) - Provides a practical guide to designing, running, and validating generative agent-based modelling experiments using Concordia. (2024)

## Benchmarks and Evaluation Tasks

- [PRM800K](https://github.com/openai/prm800k) - OpenAI's process-supervision dataset of step-level feedback labels for mathematical reasoning. (2023)
- [SWE-bench](https://www.swebench.com/) - A software-engineering benchmark frequently used to study agent loops, retries, verification, and inference-time scaling. (2023)
- [WebShop](https://github.com/princeton-nlp/WebShop) - A simulated e-commerce environment used by ReAct and LATS for action-observation agent evaluation. (2022)
- [BrowseComp-Plus](https://arxiv.org/abs/2508.06600) - A fixed-corpus benchmark for evaluating deep-research agents, retrieval, citation accuracy, and context-engineering choices under controlled conditions. (2025)
- [SOTOPIA: Interactive Evaluation for Social Intelligence in Language Agents](https://arxiv.org/abs/2310.11667) - Provides an open-ended environment and evaluation framework for social intelligence in language agents across collaborative, competitive, and goal-driven interactions. (2023)
- [LIFELONG SOTOPIA: Evaluating Social Intelligence of Language Agents Over Lifelong Social Interactions](https://arxiv.org/abs/2506.12666) - Evaluates language agents across multi-episode social interactions, measuring social intelligence over longer interaction histories. (2025)

## Open-Source Implementations

- [princeton-nlp/tree-of-thought-llm](https://github.com/princeton-nlp/tree-of-thought-llm) - Official implementation of Tree of Thoughts with tasks, prompts, and trajectories. (2023)
- [spcl/graph-of-thoughts](https://github.com/spcl/graph-of-thoughts) - Official Graph of Thoughts implementation for graph-structured reasoning operations. (2023)
- [lapisrocks/LanguageAgentTreeSearch](https://github.com/lapisrocks/LanguageAgentTreeSearch) - Official LATS repository with reasoning, acting, and planning experiments. (2024)
- [noahshinn/reflexion](https://github.com/noahshinn/reflexion) - Official Reflexion implementation for verbal reinforcement learning in language agents. (2023)
- [parthsarthi03/raptor](https://github.com/parthsarthi03/raptor) - Official RAPTOR implementation for recursive tree-organised retrieval. (2024)
- [maitrix-org/llm-reasoners](https://github.com/maitrix-org/llm-reasoners) - Library for advanced reasoning algorithms, including planning-style and tree-search methods. (2023)
- [alexzhang13/rlm](https://github.com/alexzhang13/rlm) - Official RLM inference library with REPL and sandbox environments for recursive language-model calls. (2026)
- [alexzhang13/rlm-minimal](https://github.com/alexzhang13/rlm-minimal) - Minimal reference implementation of RLMs with REPL environments for experimentation. (2026)
- [lambda-calculus-LLM/lambda-RLM](https://github.com/lambda-calculus-LLM/lambda-RLM) - Official implementation of λ-RLM for typed recursive language-model inference. (2026)
- [Jasmine0201/GASim](https://github.com/Jasmine0201/GASim) - Official implementation of GASim for graph-accelerated hybrid social simulation. (2026)

## Contributing

![We love contributors](assets/We%20love%20Contributors%20%E2%80%94%20section%20title%20banner.png)

### We love Contributors

Thrilled to have you here. <br>
Whether it's a quick typo fix, a fresh resource,
a doc polish, or a sweeping overhaul â€” every contribution helps this list grow.
Jump in and join the community â€” PRs of every size are welcome.<br>

[Read the contributing guide](CONTRIBUTING.md) [good first issues](https://github.com/natnew/awesome-recursive-language-models/issues?q=is%3Aissue%20is%3Aopen%20label%3A%22good%20first%20issue%22)

