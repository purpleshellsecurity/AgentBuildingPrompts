# Agent Standards Prompts

Two prompts for building and evaluating AI agents (built with OpenAI models) against production-readiness practices drawn from Microsoft's agent-building guidance and OpenAI's own documentation.

## Files

- **`agent_builder_walkthrough_prompt.md`** — walks you through building an agent, starting from the actual problem you're solving, not the tech stack.
- **`agent_standards_evaluator_prompt.md`** — audits an agent's code and architecture against the same standards before you ship.

## Why these exist

Building an agent is easy. Building one that's grounded, safe, cost-controlled, and won't fall over in production is a different job. These two prompts cover that gap end to end:

```
Problem  →  Build  →  Audit design  →  Ship
 (builder)              (evaluator)
```

## 1. Builder walkthrough prompt

Use this first, especially if you're starting from scratch. Paste it into a conversation with an LLM and work through it phase by phase:

1. Define the problem in plain language
2. Decide: single agent, multi-agent, or a plain workflow
3. Identify data, tools, and integrations
4. Choose a runtime (OpenAI Agents SDK/API vs. Microsoft Agent Framework)
5. Build a minimal working version
6. Layer in production-readiness (caching, retries, guardrails)
7. Architect for scale and safety
8. Set up governance (if running more than one or two agents)
9. Hand off to the evaluator prompt before shipping

**Usage:**
```
Paste the full contents of agent_builder_walkthrough_prompt.md as your first message to an LLM,
then describe the task you're trying to automate.
```

## 2. Standards evaluator prompt

Once your agent is built, use this prompt to audit the actual code and architecture — things like whether prompts are versioned, whether there's a rollback plan, and whether basic governance is in place.

**Usage:**
```
Paste the full contents of agent_standards_evaluator_prompt.md as your first message to an LLM,
then attach or paste in:
  - Your agent's source code / configuration
  - A short description of the architecture and deployment setup
  - (Optional) sample transcripts/logs of the agent running
```

It returns a structured report: an executive summary, per-category tables (Pass / Partial / Fail / N/A with evidence), and a list of anything it couldn't verify from what you gave it.

## Standards covered

Both prompts are built around five areas:

| Area | Source |
|---|---|
| Tool/function-calling correctness | OpenAI function-calling guide |
| Framework & architecture choice | OpenAI Agents SDK/API docs, Microsoft Agent Framework docs |
| Production-readiness (caching, resilience, guardrails, rollout) | Microsoft Marketplace AI agent best practices |
| Reliability, cost, responsible AI | Azure Well-Architected Framework — AI workloads |
| Governance (multi-agent inventory, identity, incident response) | Azure Cloud Adoption Framework — governing AI agents |

## License

Use, modify, and adapt freely for your own projects.
