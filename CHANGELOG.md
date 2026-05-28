# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [2.0.0] - 2026-05-28

### Changed (Breaking) — 决策模型重构

**旧模型（串行漏斗）：** Cost → Path → Workspace 三步顺序筛选，第一个命中就退出。

**新模型（三轴独立判断 + 交叉组合）：**
- **Decision A 执行环境**（文本 / Browser Agent / Coding Agent）— 基于技术硬约束，无主观判断
- **Decision B 控制级别**（Prompt / Skill / Workflow）— 基于 AI 是否唯一执行者
- **Knowledge Overlay 知识叠加层**（无 / RAG / 企业知识）— 独立评估，叠加到主路线上
- 最终路线 = A × B × C，自然组合，不需要额外判断"要不要组合"

**核心边界标准重定义：**
- Skill ↔ Workflow 边界从"步骤是否固定"改为"AI 是否是唯一执行者"——需要读写外部系统 / 跳步会出事 / 需要审批才进入 Workflow 方向
- 每条边界从主观判断（"几轮聊天能搞定吗？"）改为不可回避的事实判断（"交付物是文字还是文件/代码？"）
- 每条边界新增双重检验：需求测试（任务需要吗？）+ 难度门槛（搭得起且值得搭吗？）

**难度维度嵌入决策树：**
- 方案按实现难度排序：Prompt(★) < Browser Agent(★★) < Skill(★★★) < Coding Agent(★★★~★★★★) < RAG(★★★★) < Workflow(★★★★★)
- 方案越重，升级门槛越高——Browser Agent 无额外门槛，Workflow 需要"需求三题任一命中 + 频率≥每周 + 有人维护"
- 不满足门槛时提供具体降级方案（如 Skill + 人工兜底），而非简单的"不推荐"

### Added

- **Route Confirmation 检查点**（Workflow Step 3）：路由结果落地前强制用户确认/调整/拒绝，Skill ↔ 用户之间不再 one-shot
- **升降级触发器**：每条路线附带"什么时候该升级/降级到另一条路线"的信号表
- **Discovery 快速通道**：用户首条消息覆盖 4 维度中 3 个时直接跳到路由
- **用户能力评估**：Discovery 问题池新增 Capability 维度（能搭工作流吗？能验收代码吗？能维护 RAG 吗？）
- **4 个 Edge Case 处理规则**：用户中途变更需求、用户拒绝路由、信息不足超 5 题、用户自带工具偏好
- **Output Templates 分轻重**：高置信单路线用 Lightweight 模板，中低置信或组合方案用 Full 模板

### Changed

- **Frontmatter**：加入中文触发词（AI工具选型、该用什么AI、用什么工具、需求分析、AI方案推荐等）
- **Workflow 每步标注 Input/Output**：从 4 步扩展为 5 步，每步有显式输入输出规格
- **enterprise-knowledge-rag.md 重写**：三 Tier 渐进结构（企业原生搜索 → 知识库 RAG → 自定义 RAG），对齐 decision-tree.md 难度门槛，落实平台中立原则
- **Decision Summary 精简**：SKILL.md 中不再重复 decision-tree.md 的完整逻辑，改为摘要表格 + 指向 reference
- **demo-build-branch.md / product-demo-templates.md**：标记为可选扩展模块，主 skill 路由完即交出 handoff prompt，不再默认加载

### Removed

- "95% confidence" 模糊指标——替换为可操作的 Confidence Checklist 引用
- 串行漏斗决策树（Cost → Path → Workspace）
- 钉钉特定推荐话术模板（改为平台中立的多生态示例）

## [1.0.0] - 2026-05-28

### Added

- Discovery 流程：逐个提问至 95% 置信度的需求发现机制
- 决策路由：成本 → 路径固定性 → 执行环境三维度决策树
- 六种方案类型支持：AI Chat / Skill / Workflow / Knowledge Base RAG / Browser Agent / Coding Agent
- 组合推荐逻辑：单工具优先，多层需求时推荐组合方案
- 7 个参考文档：decision-tree、discovery、output-templates、skill-creation-guide、enterprise-knowledge-rag、demo-build-branch、product-demo-templates
- OpenAI agent 配置（agents/openai.yaml）
