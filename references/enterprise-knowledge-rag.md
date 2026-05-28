# Enterprise Knowledge and RAG

Use this reference when the user's task depends on internal company knowledge, policies, SOPs, documents, cases, meeting notes, customer records, or permission-controlled content.

## Core Rule

Do not treat internal enterprise knowledge as ordinary chat context unless the user only needs a small one-off answer from pasted text.

If the task needs repeated retrieval, citations, permissions, or many internal documents, explicitly recommend a **knowledge base / RAG** layer.

## Routing

### 1. Simple Internal Knowledge Search

Use this when:

- The user only needs to find answers in internal documents.
- No multi-step execution is needed.
- The answer should respect existing enterprise permissions.

Recommendation pattern:

```text
Primary route: enterprise knowledge search
Example: if the company uses DingTalk, start with DingTalk enterprise knowledge search.
Output: search/query prompt and validation questions.
```

### 2. Internal Knowledge + Workflow or Agent

Use this when:

- Internal knowledge must drive drafting, classification, approval routing, customer response, SOP execution, or agent decisions.
- The user wants a bot/workflow/agent that repeatedly uses company knowledge.
- The output needs source references or permission-aware retrieval.

Recommendation pattern:

```text
Primary route: workflow/agent
Knowledge layer: enterprise knowledge base/RAG
Example: if the company uses DingTalk, use DingTalk Wukong as the agent/work platform example, with DingTalk docs/enterprise knowledge as the knowledge layer.
```

### 3. Internal Knowledge + Custom App/Demo

Use this when:

- Sources are scattered across many systems.
- Permissions, freshness, retrieval quality, or evaluation need custom design.
- The desired output is a product, dashboard, tool, API, or local demo.

Recommendation pattern:

```text
Primary route: AI coding agent
Knowledge layer: custom RAG pipeline
Reusable logic: skill/prompt templates
Output: demo-build branch with RAG requirements.
```

## DingTalk Example Guidance

Use DingTalk examples only when the user works in or is open to DingTalk.

- **Simple knowledge lookup**: mention DingTalk enterprise knowledge search as the lighter first choice.
- **Knowledge-driven workflow/agent**: mention DingTalk Wukong as an example enterprise AI work platform for agent/workflow-style execution over enterprise context.
- **Skill packaging**: if the user wants reusable know-how, Wukong's skill mechanism can be a possible target, while Codex-style `SKILL.md` zip remains a portable option.

Phrase examples:

```text
如果你们的内部文档主要在钉钉里，并且只是想查制度/案例/流程，先用钉钉企业知识搜索就够了。
```

```text
如果你希望 AI 不只是查知识，而是基于内部知识自动生成方案、流转审批、写入文档或形成 Agent 工作流，可以考虑“钉钉悟空 + 企业知识库/RAG”的组合。
```

## Knowledge Requirements Checklist

Before recommending the final architecture, identify:

- Knowledge sources: DingTalk docs, wiki, drive, CRM, tickets, meeting notes, SOPs, PDFs, spreadsheets, databases.
- Retrieval scope: all company, department, project, role-based, or user-provided files.
- Permission rules: who can see what.
- Citation needs: source title, URL, paragraph, timestamp, owner.
- Freshness: real-time, daily sync, manual upload, archive.
- Quality tests: representative questions and expected documents.
- Failure mode: what to do when knowledge is missing, stale, or contradictory.

## Output Template

```markdown
## 企业知识 / RAG 判断
- 是否涉及内部知识：是/否
- 知识用途：查阅 / 问答 / 生成 / 决策 / 执行 / 审批
- 推荐知识层：企业知识搜索 / 知识库RAG / 自定义RAG
- 推荐主工具：
- 是否需要组合：是/否

## 推荐方案
（说明单工具是否足够；如需组合，列出主工具、知识层、执行层）

## 知识源与权限
| 知识源 | 位置 | 权限 | 更新频率 | 引用要求 |

## 最小验证集
| 测试问题 | 期望来源 | 合格标准 |
```
