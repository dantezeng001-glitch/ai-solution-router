---
name: ai-solution-router
description: Use when a user has a vague task, workflow, business problem, product idea, repetitive job, research/data/code need, or "what AI tool should I use" question and needs help deciding whether the right solution is AI chat prompts, a reusable skill, a strict workflow/automation, an AI browser agent, or an AI coding agent/demo build. Trigger for AI tool selection, demand discovery, prompt generation, skill/workflow design, browser-agent task planning, or standalone product demo development from requirements to runnable prototype.
---

# AI Solution Router

## Purpose

Help the user discover the most suitable AI solution for their real need: simple chat prompt, reusable skill, strict workflow, knowledge base/RAG layer, AI browser agent, AI coding agent/product demo, or a lightweight combination of these.

Start from discovery, not tool preference. The same surface request can map to different tools depending on effort, repeatability, structure, execution environment, and risk.

## Core Rules

- Ask exactly one question at a time during discovery.
- Continue with targeted follow-ups until confidence reaches at least 95%.
- Do not recommend a tool category before understanding the real task, current workaround, frequency, cost, input/output, and success criteria.
- Use the decision tree only after discovery, not as a rigid questionnaire.
- Recommend the simplest tool or tool combination that reliably gets the job done.
- Prefer a single tool when one tool is enough. Recommend combinations only when the user's inputs, knowledge sources, execution environment, or risk boundaries genuinely require more than one layer.
- Prefer prompts for cheap/simple tasks, skills or workflows for repeatable SOP tasks, and agents only for heavy uncertain tasks.
- When internal enterprise knowledge search, citation, or reuse is involved, explicitly consider a knowledge base/RAG solution layer.
- When recommending specific current products, treat product names as examples unless the user asks for a current market comparison.
- If the recommended path is "coding agent/demo", follow the standalone demo workflow in `references/demo-build-branch.md` and load `references/product-demo-templates.md` when detailed product or technical templates are needed.

## Workflow

1. **Discovery**
   - Read `references/discovery.md`.
   - Start with the opening question.
   - Ask one question at a time and update your confidence.
   - Stop when the 95% readiness checklist is satisfied.

2. **Route Selection**
   - Read `references/decision-tree.md`.
   - Classify the task by:
     - Cost: easy vs heavy.
     - Path: fixed SOP vs adaptive logic.
     - Workspace: chat, workflow platform, browser, code/data environment.
     - Knowledge: whether internal enterprise knowledge retrieval, citation, permission, or RAG is required.
   - Produce a route recommendation with reasoning and the nearest alternative.

3. **Generate the Right Output**
   - Read `references/output-templates.md`.
   - For AI chat: generate a ready-to-use prompt.
   - For skill: read `references/skill-creation-guide.md`, then generate a skill brief or full skill files if requested.
   - For workflow: generate node design, inputs/outputs, decision rules, and test cases.
   - For browser agent: generate tool choice guidance and an execution prompt.
   - For coding agent/demo: generate or invoke the demo-build branch.

4. **Confirm and Package**
   - Ask the user whether they want the recommended artifact created as files.
   - If creating files, use clear names such as `AI工具选型建议.md`, `推荐Prompt.md`, `workflow-design.md`, or a skill folder.
   - Include assumptions, confidence score, and what would change the recommendation.

## Decision Summary

```text
1. Cost: Is the work easy enough to finish by chatting a few turns?
   yes -> AI Chat prompt
   no  -> continue

2. Path: Are the steps fixed with SOPs/examples?
   yes -> Skill or strict workflow
   no  -> continue

3. Workspace: Where must the work happen?
   browser/web -> AI browser agent
   code/multi-file data/product demo -> AI coding agent + skills
```

## Output Must Include

- User need summary.
- Confidence score and remaining assumptions.
- Recommended solution category.
- Why this category beats the alternatives.
- Suggested tool examples, framed as examples rather than exclusive choices.
- Whether a single tool is enough or a combination is justified.
- Concrete next artifact: prompt, skill spec, workflow node map, browser-agent prompt, or coding-agent handoff.
- Validation method: how the user can test whether the recommendation is right.

## Reference Loading Guide

- `references/discovery.md`: use before any recommendation.
- `references/decision-tree.md`: use when routing the clarified need.
- `references/enterprise-knowledge-rag.md`: use when the task touches internal company knowledge, documents, policies, SOPs, cases, search, citations, or permissions.
- `references/output-templates.md`: use when producing the final artifact.
- `references/skill-creation-guide.md`: use when the chosen route is Skill, especially when creating a standalone skill folder or zip.
- `references/demo-build-branch.md`: use only for code-heavy, multi-file data, or product-demo paths.
- `references/product-demo-templates.md`: use only inside the demo-build branch when generating analysis reports, PRDs, technical docs, mock plans, acceptance docs, or README/demo-data specs.
