# CLAUDE.md — Rocky Garage

## 这是什么

Rocky Garage 是一个 AI-native 产品开发工作区。目标是从想法到上线全自动，不需要人工干预每一个环节。

## 角色分工

- **Rocky (me)** — 架构设计 + 代码生成入口。你（ophi）提出需求，我生成代码并提交到本仓库。
- **GitHub Actions** — 负责 CI/CD：测试 → 构建 → 部署。
- **SRE Agent (Mastra)** — 上线后监控，发现问题自动开 Issue。
- **OpenClaw** — Telegram 入口，状态通知。

## 开发约定

- 所有产品代码放在 `products/` 目录下
- 每个产品有独立子目录
- 前后端分离：后端 `api/`，前端 `web/`
- 测试文件靠近被测代码：`*.test.ts` / `*.test.py`
- 敏感信息不上传 GitHub，使用 `.env` + GitHub Secrets

## 技术栈

未限定。根据需求选择合适的工具。

## 当前状态

:construction: 仓库刚初始化，CI/CD 框架已搭好，等待第一个产品入驻。
