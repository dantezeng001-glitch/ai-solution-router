# Decision Tree

Use this after discovery to route the user to the simplest reliable AI solution.

## First Principle: Single Tool First, Combination When Needed

Prefer a single tool when it can complete the task reliably.

Recommend a combination only when at least one condition is true:

- The task needs a knowledge source plus an execution tool, such as internal policy retrieval plus workflow execution.
- The task has distinct phases that require different environments, such as browser research plus coding implementation.
- The task needs persistent reusable instructions plus a tool, such as a Skill plus AI coding agent.
- The task needs strict routing/approval plus AI generation, such as workflow platform plus AI chat/model node.
- The task needs internal knowledge permissioning, citations, or RAG in addition to generation or execution.

When recommending a combination, name the layers:

```text
Primary tool: the place where the user works
Knowledge layer: knowledge base/RAG/search if needed
Execution layer: workflow/browser/coding agent if needed
Reusable logic layer: skill/prompt template if needed
```

## Step 1: Cost - Is This Easy Enough for Chat?

Choose **AI Chat** when:

- The user can describe the task in one short prompt.
- The input is small enough to paste into a chat.
- A few rounds of clarification are enough.
- The output is text, outline, classification, rewrite, draft, summary, brainstorming, or simple table.
- Even if frequent, the task does not require strict repeatability or tool integration.

Logic:

> If a few chat turns reliably produce the result, do not add workflow or agent complexity.

Examples:

- Rewrite an email.
- Summarize a meeting transcript.
- Generate campaign ideas.
- Draft a weekly report from pasted notes.
- Analyze a small table pasted into chat.

Output:

- Recommended chat tool category: general AI chat.
- A ready-to-use prompt.
- Optional prompt variables and examples.
- If internal knowledge is needed, add a knowledge search/RAG note instead of pretending pasted context is enough.

## Step 2: Path - Are the Steps Fixed?

Choose **Skill** when:

- The job is repeatable but still benefits from AI judgment.
- There are templates, SOPs, examples, rubrics, style rules, or domain context.
- The user wants consistent outputs across future sessions.
- The process can tolerate some agent discretion.

Choose **Workflow** when:

- The steps are strict and should not be skipped or reordered.
- Inputs/outputs are structured.
- There are approvals, routing rules, database writes, notifications, or integrations.
- The result needs observability, permissions, or repeated operation by non-experts.
- The user wants a deployed bot or automation in Dify, Coze, DingTalk bot/AI assistant, Zapier/Make/n8n, internal automation, or similar platforms.

Logic:

> If the path is known, constrain the AI. Use a skill for flexible repeatable judgment. Use a workflow for strict execution.

Output for Skill:

- Skill name.
- Trigger conditions.
- Workflow.
- References or templates needed.
- Example user prompts.

Output for Workflow:

- Node map.
- Node inputs/outputs.
- Decision rules.
- Human approval points.
- Error handling.
- Test cases.

## Knowledge Overlay: Does It Need Internal Enterprise Knowledge?

Apply this overlay at any step. It can change a single-tool recommendation into a small combination.

Choose **enterprise knowledge search** when:

- The user mainly wants to find answers in internal documents, policies, SOPs, meeting notes, or past cases.
- The task is question-answering or citation, not multi-step execution.
- The user already works in an enterprise collaboration suite.

Example recommendation:

- If the company uses DingTalk and the need is simple internal knowledge lookup, recommend DingTalk enterprise knowledge search / enterprise search first.
- Reason: the knowledge, permissions, and collaboration context are already inside the enterprise workspace.

Choose **knowledge base/RAG + workflow/agent** when:

- Internal knowledge must drive decisions, routing, drafting, classification, or repeated automation.
- The output needs source citations, permission control, or stable retrieval from many internal docs.
- The user wants a bot, workflow, or agent that answers or acts based on company knowledge.

Example recommendation:

- If the company uses DingTalk and wants to build an internal-knowledge-driven workflow or agent, recommend DingTalk Wukong as an example AI work platform, with the company's DingTalk documents/knowledge as the knowledge layer.
- For non-DingTalk stacks, recommend a RAG-capable workflow/agent platform or custom RAG service plus the chosen workflow/agent tool.

Choose **custom RAG + coding agent** when:

- The knowledge sources are scattered, large, permission-sensitive, or need custom indexing/evaluation.
- The user needs a bespoke app, demo, retrieval pipeline, or integration with existing systems.

Output for knowledge/RAG cases:

- Knowledge source inventory.
- Retrieval/citation requirements.
- Permission and privacy constraints.
- Recommended base tool plus knowledge layer.
- A small validation test: 5-10 representative questions with expected source documents.

## Step 3: Workspace - Where Does the Heavy Adaptive Work Happen?

Choose **AI Browser Agent** when:

- The work happens mainly on websites or web apps.
- It requires searching, comparing web pages, clicking, filling forms, copying data, downloading files, or lightweight web-based data analysis.
- The user needs their logged-in browser session or browser-visible context.
- It does not require deep codebase editing.

Examples:

- Gather supplier info from several websites.
- Use a web admin panel to create records.
- Compare web search results and extract a shortlist.
- Fill repeated web forms with human review.

Tool examples:

- GPT agent/agent mode.
- AI browser tools.
- Browser automation agents such as Tabbit-like tools.
- In Codex, use browser automation when local or web inspection is needed.

Output:

- Tool category.
- Browser-agent task prompt.
- Preconditions: login, pages, data, stop rules.

Choose **AI Coding Agent + Skills** when:

- The work involves a codebase, multi-file edits, app/demo creation, local scripts, data pipelines, complex notebooks, or multi-file analysis.
- The desired output is runnable software, a demo, a data processing tool, a script, or a repeatable technical artifact.
- The task benefits from reading files, editing files, running tests, verifying outputs, and packaging deliverables.

Examples:

- Build an internal dashboard demo.
- Turn a PRD into a working app.
- Process many CSV/Excel/PDF files with scripts.
- Add an AI feature to an existing product.
- Create a local tool with sample data and mock services.

Tool examples:

- Codex, Claude Code, Cursor, Windsurf, or similar coding agents.
- Pair with a dedicated skill when the workflow is repeatable.

Output:

- Coding-agent handoff prompt.
- Suggested project structure.
- Demo/verification plan.
- If the goal is product development, use the demo-build branch.

## Recommendation Confidence

Use these labels:

- **High confidence**: one route clearly wins and alternatives are weaker.
- **Medium confidence**: one route wins, but one missing detail could change it.
- **Low confidence**: ask another question before recommending.

Always state what would change the recommendation.
