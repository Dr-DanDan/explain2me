---
name: explain2me
description: Explain concepts, code flows, and comparisons with plain language and focused visuals. Use when the user asks for an intuitive explanation, a beginner-friendly walkthrough, or a diagram that makes a topic easier to understand.
license: MIT
---

# Explain2me

Make the requested topic understandable at the user's level, with a visual that carries the explanation.

## Establish the topic

Use the topic supplied with the invocation, or the current discussion. Ask one focused question if neither identifies what to explain. Match the user's language and infer their background from context; otherwise assume a beginner without using a childish tone.

When explaining a particular codebase or document, inspect the relevant source before describing its behavior. Keep hypothetical examples distinct from observed behavior.

## Choose a useful visual

Start with the central idea in one or two sentences. Choose the smallest representation that explains the relationship:

| Topic | Useful representation |
| --- | --- |
| Logic or an algorithm | Pseudocode with a small worked example |
| File ownership or call hierarchy | A shallow file tree or call tree |
| Interactions, order, or data flow | A Mermaid flowchart or sequence diagram |
| Differences between approaches | A compact comparison table or annotated diff |
| A spatial concept or visual interaction | A self-contained HTML page |

Use an everyday analogy when it helps, connect it to the actual mechanism, and identify any simplification that could mislead. Label technical terms where they first become necessary. Keep each visual beside the short explanation it supports.

## Deliver

For HTML, use inline CSS and SVG with readable labels, sufficient contrast, and a responsive layout. Include interaction only when changing a value or stepping through a process helps explain it. Keep the page usable without a network connection.

Use the requested destination for saved artifacts; otherwise use `output/explain2me-<topic>.html` in the current project. Preserve existing files by choosing a new filename when needed. Preview the page when the environment supports it, check labels and layout, and provide a link to the artifact. If a preview cannot run, say so.

Keep the final explanation focused on the user's question and make the key mechanism visible in the diagram or example.
