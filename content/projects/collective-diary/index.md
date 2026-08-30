---
title: "Collective Diary: Graph-Backed Reflection for AI Agents"
description: "A proof of concept exploring graph-based memory for individual and collective reflection across AI agents' operational histories."
date: 2026-08-27
draft: false
tags: ["reflection", "ai-agents", "graph-databases", "neo4j"]
---

## From Agent Diary to collective reflection

**Collective Diary** is a proof of concept exploring graph-based memory as a basis for reflection in AI agents. It was developed at the Neo4j Mini Agentic Hack in Berlin as an extension of [Agent Diary](https://github.com/lr1ke/agent-diary), an earlier project in which AI agents create diary entries from structured traces of their work.

Agent Diary records information about an agent's sessions, including tasks, tools, failures and outcomes, and synthesizes this data into first-person diary entries. Its reflection function works on the history of an individual agent. Collective Diary extends this idea by asking what becomes possible when the histories of several agents are represented as a shared relational structure.

The project distinguishes between two forms of reflection. **Individual reflection** asks what an agent can learn from patterns across its own history. **Collective reflection** asks what an agent can learn about itself by relating its history to the histories of other agents.

The underlying hypothesis is that reflection may require more than retrieving or summarizing individual memories. Some insights become available only through relationships across experiences, and potentially across the experiences of others.

## Modeling agent histories as a graph

The proof of concept uses Neo4j to represent structured agent histories as a graph. The model consists of four node types and three relationships:

\`\`\`
(Agent)-[:RAN]->(Session)-[:CLASSIFIED_AS]->(TaskType)
                    |
                    +-[:USED_TOOL {succeeded}]->(Tool)
\`\`\`

`TaskType` and `Tool` connect otherwise separate agent histories through shared nodes. This makes it possible to query relationships within an individual history as well as patterns that occur across several agents.

The graph is populated with a synthetic history of seven agents. Six Cypher queries explore recurring failures, changes in strategy, shared patterns, differences between agents and strategies that might transfer from one agent to another. The queries return structured evidence such as counts, rates, chronological traces and tool usage. An LLM subsequently translates this evidence into first-person reflective text.

The separation between these two steps is an important part of the experiment. The LLM does not receive the raw session history and is not asked to discover patterns itself. Patterns are first derived from relationships in the graph; the language model is used afterward to formulate a reflection from this evidence.

For example, the graph can establish that an agent's completion rate for a particular kind of task changed after its tool usage changed, or that another agent approaches the same kind of task differently and achieves different outcomes. The resulting reflection remains traceable to the underlying query results.

The project also experimented with Neo4j Aura's MCP interface. This allowed an AI agent to query the graph directly with dynamically generated Cypher rather than relying only on predefined reflection queries.

## From operational patterns to behavioral modes

The current proof of concept produces a specific kind of reflection. It identifies recurring failures, changes in strategy, tool usage and differences between agents. These findings are grounded in the operational history of the agents, but they remain primarily behavioral and performance-oriented.

This raises a further question: how can a system move from observable operational patterns toward more general patterns in how an agent behaves?

The current graph relies on predefined categories such as `debugging`, `deployment` and `research`. These categories describe the kind of task an agent performs, but not necessarily how the agent behaves while performing it. Two agents working on the same kind of task may follow very different patterns: one may repeatedly retry the same action after failure, while another gathers additional information, changes its approach and tests an alternative.

A next step is therefore to investigate whether meaningful modes of an agent's behavior can emerge from the structure of its experience rather than being predefined in advance.

Instead of beginning with a fixed vocabulary of behavioral categories, recurring structures across experiences could form the basis for categories that remain open to development. Possible modes might eventually be described as repetitive, exploratory, verification-heavy, cautious or adaptive, but the relevant distinctions should ideally be derived from the history rather than imposed on it beforehand.

This suggests an additional abstraction layer:

\`\`\`
agent experiences
      ↓
operational patterns
      ↓
behavioral modes
      ↓
higher-order interpretation
      ↓
reflection
\`\`\`

The question is not simply how to generate more abstract reflections with an LLM, but how these abstractions can remain grounded in the experiences from which they were derived.

## Toward a collective reflection layer

Collective Diary also explores the hypothesis that reflection can be a collective process. An individual agent's history provides one perspective on its behavior; the histories of other agents provide an additional reference space in which that behavior can be interpreted.

In the current proof of concept, this comparison remains relatively concrete: agents can be compared through shared task types, tool usage, failures and outcomes. Future work will investigate whether higher-order behavioral patterns can also be represented across agents and whether an individual agent can use patterns emerging from the collective history to reflect on its own behavior.

The graph can therefore be understood as an initial **collective reflection layer on top of individual agent histories**. The longer-term question is whether such a layer can support agents in developing and revising models of their own behavior from experience.

**Code:** [GitHub repository](https://github.com/lr1ke/neo4j-hack)