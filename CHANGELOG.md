# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.0.0] - 2026-05-28

### Added

- Discovery 流程：逐个提问至 95% 置信度的需求发现机制
- 决策路由：成本 → 路径固定性 → 执行环境三维度决策树
- 六种方案类型支持：AI Chat / Skill / Workflow / Knowledge Base RAG / Browser Agent / Coding Agent
- 组合推荐逻辑：单工具优先，多层需求时推荐组合方案
- 7 个参考文档：decision-tree、discovery、output-templates、skill-creation-guide、enterprise-knowledge-rag、demo-build-branch、product-demo-templates
- OpenAI agent 配置（agents/openai.yaml）
