# Awesome Agentic Patterns 🚀

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

A curated catalogue of awesome agentic AI patterns, architectures, and design principles for building autonomous AI systems.

> **Agentic AI** refers to AI systems that can autonomously pursue goals, make decisions, and take actions with minimal human intervention.

## Contents

- [Context & Memory](#context--memory)
- [Feedback Loops](#feedback-loops)
- [Learning & Adaptation](#learning--adaptation)
- [Orchestration & Control](#orchestration--control)
- [Reliability & Eval](#reliability--eval)
- [Security & Safety](#security--safety)
- [Tool Use & Environment](#tool-use--environment)
- [UX & Collaboration](#ux--collaboration)

---

## Context & Memory

Patterns for managing state, context, and memory in agentic systems.

### Sliding-Window Curation
- **Description**: Dynamically manage context window by curating relevant information
- **Use Case**: Long-running conversations where full history exceeds token limits
- **Example**: Keep recent N messages + summarized older context + key facts
- **Reference**: [LangChain Memory](https://python.langchain.com/docs/modules/memory/)

### Vector Cache
- **Description**: Store and retrieve information using vector embeddings
- **Use Case**: Semantic search over agent's knowledge base
- **Example**: Embed documents, store in vector DB, retrieve by semantic similarity
- **Tools**: [Pinecone](https://www.pinecone.io/), [Weaviate](https://weaviate.io/), [Chroma](https://www.trychroma.com/)

### Episodic Memory
- **Description**: Store and recall specific experiences or interactions
- **Use Case**: Learning from past mistakes, personalizing responses
- **Example**: Log successful/unsuccessful tool calls for future reference
- **Reference**: [MemGPT](https://github.com/cpacker/MemGPT)

---

## Feedback Loops

Patterns for incorporating feedback to improve agent performance.

### Compiler Feedback
- **Description**: Use compilation errors to fix code generation
- **Use Case**: Self-healing code writing agents
- **Example**: Generate code → compile → if error, feed error back to LLM → retry

### CI/CD Integration
- **Description**: Automated testing and deployment feedback
- **Use Case**: Agents that write and deploy code
- **Example**: Run tests on generated code, report failures to agent

### Human Review Loop
- **Description**: Incorporate human feedback into agent decisions
- **Use Case**: High-stakes decisions requiring human oversight
- **Example**: Propose action → wait for approval → execute

### Self-Healing Retries
- **Description**: Automatic retry with exponential backoff and error analysis
- **Use Case**: Resilient API calling, web scraping
- **Example**: Failed request → analyze error → adjust parameters → retry

---

## Learning & Adaptation

Patterns for agents that learn and improve over time.

### Agent RFT (Reinforcement Learning from Feedback)
- **Description**: Train agents using reinforcement learning from human or automated feedback
- **Use Case**: Aligning agent behavior with user preferences
- **Reference**: [RLHF](https://huggingface.co/blog/rlhf), [Direct Preference Optimization](https://github.com/eric-mitchell/direct-preference-optimization)

### Skill Libraries
- **Description**: Accumulate reusable skills or tools over time
- **Use Case**: Agents that grow more capable through experience
- **Example**: Successfully solve problem → extract reusable function → add to toolkit
- **Reference**: [Voyager](https://github.com/MineDojo/Voyager)

### Variance-Based RL
- **Description**: Explore actions with high uncertainty to maximize learning
- **Use Case**: Efficient exploration in unknown environments
- **Reference**: [UCB Algorithms](https://arxiv.org/abs/0912.3995)

---

## Orchestration & Control

Patterns for managing multiple agents and complex workflows.

### Task Decomposition
- **Description**: Break complex tasks into manageable subtasks
- **Use Case**: Multi-step problem solving
- **Example**: "Build a website" → design → frontend → backend → deploy
- **Reference**: [Plan-and-Solve Prompting](https://arxiv.org/abs/2305.04091)

### Sub-Agent Spawning
- **Description**: Create specialized sub-agents for specific tasks
- **Use Case**: Parallel execution, specialized expertise
- **Example**: Main agent spawns research agent + coding agent + review agent
- **Reference**: [AutoGen](https://github.com/microsoft/autogen), [CrewAI](https://github.com/joaomdmoura/crewAI)

### Tool Routing
- **Description**: Dynamically select appropriate tools for tasks
- **Use Case**: Agents with large tool sets
- **Example**: Vector search over tool descriptions → select top-k → execute

### Hierarchical Planning
- **Description**: Multi-level planning from high-level goals to concrete actions
- **Use Case**: Long-horizon tasks requiring strategic thinking
- **Example**: Mission → objectives → tasks → actions

---

## Reliability & Eval

Patterns for ensuring agent reliability and evaluation.

### Guardrails
- **Description**: Safety constraints and validation layers
- **Use Case**: Prevent harmful or incorrect actions
- **Example**: Output validation, input sanitization, action approval gates
- **Tools**: [Guardrails AI](https://github.com/guardrails-ai/guardrails), [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)

### Eval Harnesses
- **Description**: Standardized evaluation frameworks
- **Use Case**: Benchmarking agent performance
- **Example**: [AgentBench](https://github.com/THUDM/AgentBench), [WebArena](https://github.com/web-arena/web-arena)

### Structured Logging
- **Description**: Comprehensive logging of agent decisions and actions
- **Use Case**: Debugging, auditing, post-hoc analysis
- **Example**: Log all LLM calls, tool executions, and state changes

### Reproducibility
- **Description**: Ensure deterministic behavior when needed
- **Use Case**: Debugging, testing, compliance
- **Example**: Seed randomness, log all random choices, version dependencies

---

## Security & Safety

Patterns for secure and safe agent operation.

### Isolated VMs
- **Description**: Run agents in sandboxed environments
- **Use Case**: Untrusted code execution, security research
- **Tools**: [E2B](https://e2b.dev/), [Docker](https://www.docker.com/), [Firecracker](https://firecracker-microvm.github.io/)

### PII Tokenization
- **Description**: Automatically detect and redact personally identifiable information
- **Use Case**: Privacy-preserving agent interactions
- **Example**: Replace emails, phone numbers with tokens before LLM processing

### Security Scanning
- **Description**: Scan generated code and actions for vulnerabilities
- **Use Case**: Safe code generation
- **Tools**: [Bandit](https://bandit.readthedocs.io/), [Semgrep](https://semgrep.dev/)

### Capability Constraints
- **Description**: Limit what actions an agent can perform
- **Use Case**: Principle of least privilege
- **Example**: Read-only filesystem, restricted network access, limited tool set

---

## Tool Use & Environment

Patterns for interacting with external tools and environments.

### Shell Integration
- **Description**: Execute shell commands safely
- **Use Case**: System administration, development tasks
- **Safety**: Command validation, dry-run mode, allowlists

### Browser Automation
- **Description**: Control web browsers programmatically
- **Use Case**: Web scraping, testing, form filling
- **Tools**: [Playwright](https://playwright.dev/), [Selenium](https://www.selenium.dev/), [Puppeteer](https://pptr.dev/)

### Database Interaction
- **Description**: Query and modify databases
- **Use Case**: Data analysis, application development
- **Safety**: Read-only modes, query validation, prepared statements

### Code Execution
- **Description**: Safely execute generated code
- **Use Case**: Data analysis, algorithm implementation
- **Tools**: [Jupyter](https://jupyter.org/), [Code Interpreter API](https://platform.openai.com/docs/assistants/tools/code-interpreter)

### Sandboxing
- **Description**: Restricted execution environments
- **Use Case**: Safe execution of untrusted code
- **Tools**: [gVisor](https://gvisor.dev/), [seccomp](https://man7.org/linux/man-pages/man2/seccomp.2.html)

---

## UX & Collaboration

Patterns for human-agent interaction and collaboration.

### Prompt Hand-offs
- **Description**: Seamless transfer between different agent modes or personas
- **Use Case**: Multi-domain expertise, escalation paths
- **Example**: General assistant → specialized coding agent → human expert

### Staged Commits
- **Description**: Preview changes before finalizing
- **Use Case**: Preventing irreversible actions
- **Example**: "I'll make these changes. Review and approve?"

### Async Background Agents
- **Description**: Agents that work independently and report back
- **Use Case**: Long-running tasks, monitoring
- **Example**: "Research this topic and email me a summary in 1 hour"

### Progressive Disclosure
- **Description**: Start with high-level summary, allow drilling down
- **Use Case**: Managing information overload
- **Example**: Summary → key points → full details → raw data

### Confidence Indicators
- **Description**: Communicate uncertainty in agent responses
- **Use Case**: Appropriate trust calibration
- **Example**: Confidence scores, "I'm not sure, but...", citation of sources

---

## Contributing

Contributions are welcome! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details.

### Quick Start

1. Fork the repository
2. Create a new branch: `git checkout -b add-new-pattern`
3. Add your pattern with examples and references
4. Submit a Pull Request

### Pattern Template

When adding a new pattern, please use this template:

```markdown
### Pattern Name
- **Description**: Brief explanation of the pattern
- **Use Case**: When to use this pattern
- **Example**: Concrete example or pseudo-code
- **Reference**: Links to papers, implementations, or documentation
```

---

## Related Resources

### Libraries & Frameworks
- [LangChain](https://github.com/langchain-ai/langchain) - Building applications with LLMs
- [AutoGen](https://github.com/microsoft/autogen) - Multi-agent conversation framework
- [CrewAI](https://github.com/joaomdmoura/crewAI) - Multi-agent orchestration
- [LlamaIndex](https://github.com/run-llama/llama_index) - Data framework for LLMs

### Research Papers
- [ReAct: Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629)
- [Reflexion: Self-Reflective Agents](https://arxiv.org/abs/2303.11366)
- [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442)

### Other Awesome Lists
- [Awesome LLM Apps](https://github.com/Shubhamsaboo/awesome-llm-apps)
- [Awesome AI Agents](https://github.com/e2b-dev/awesome-ai-agents)
- [Awesome LangChain](https://github.com/kyrolabs/awesome-langchain)

---

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

---

<p align="center">
  <i>Built with 🤖 by the AI agent community</i>
</p>
