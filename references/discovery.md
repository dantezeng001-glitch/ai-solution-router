# Discovery

Use this before recommending tools. The goal is to understand the user's real job well enough to route it with 95% confidence.

## Opening Question

Ask:

```text
你先用一个具体例子讲讲：这件事现在通常怎么发生，从你拿到什么输入开始，到你希望得到什么结果结束？
```

Then ask one follow-up at a time.

## Confidence Checklist

Reach 95% confidence when you can answer:

- What exact job is the user trying to finish?
- What input does the user start with?
- What output counts as success?
- How often does the job happen?
- How much time, attention, or frustration does it currently cost?
- Is the current path fixed, semi-fixed, or exploratory?
- Are there SOPs, templates, examples, or past cases?
- Does the work happen mostly in chat, documents, spreadsheets, browser/web apps, code, local files, or multiple systems?
- Does the task require login/session context, mouse clicks, web research, data analysis, or code changes?
- Does the task depend on internal company knowledge, policies, SOPs, documents, past cases, customer records, or permission-controlled content?
- What risks matter: accuracy, privacy, compliance, cost, external dependencies, user confirmation?
- What level of automation does the user want: suggestion, draft, execution, or end-to-end delivery?

If only one or two low-risk details remain unclear, proceed and mark them as assumptions.

## Follow-Up Question Pool

Use these as a pool, not a questionnaire.

### Cost

- "这件事做一次大概需要多久？最累的部分是什么？"
- "如果 AI 只通过聊天帮你，你觉得几轮对话能不能完成？"
- "它是偶尔做，还是每天/每周反复做？"

### Path

- "这件事有没有固定步骤、模板、SOP 或以前做过的优秀案例？"
- "如果换一个人来做，能不能按同一套步骤稳定完成？"
- "哪些环节需要临场判断或自由探索？"

### Workspace

- "这件事主要在哪儿发生：聊天框、文档/表格、网页后台、浏览器搜索、代码项目，还是多个系统之间？"
- "需要 AI 真正点击网页、登录系统、下载资料、改文件或跑代码吗？"
- "输入输出是单个文本，还是一堆文件/表格/网页/代码？"

### Internal Knowledge

- "这件事需要引用公司内部文档、制度、历史案例、客户资料或知识库吗？"
- "你只是想搜索答案，还是要让这些内部知识参与到工作流/Agent 的判断和执行里？"
- "这些知识现在放在哪里：钉钉文档/知识库、飞书、企业微信、Notion、网盘、CRM，还是散落在文件夹里？"
- "输出需要标明引用来源吗？是否有权限隔离或保密要求？"

### Risk and Boundary

- "AI 输出之后，你希望它只给建议，还是直接执行？哪些地方必须你确认？"
- "这个任务如果做错，代价是什么？只是返工，还是会影响客户、合规或业务决策？"

## Stop Conditions

Proceed to routing when:

- You know enough to place the task on the cost/path/workspace decision tree.
- You can explain why at least two other routes are less suitable.
- You can generate a concrete next artifact, not just name a tool.

If the user says "不要问太多，先给判断", ask one final high-leverage question, then produce a provisional recommendation with assumptions.
