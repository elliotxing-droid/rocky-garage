# AI-Native Product Pipeline — Revolutionary Architecture

## 核心认知升级：Assistant vs Factory

```
Assistant          Factory
─────────────────────────────────────────────────
人操控工具           工具自我运作
单 agent            多 agent 协作
提示 → 代码          目标 → 自主完成
人在回路中           人在批准节点
```

**我们之前建的是 Assistant 级别的流水线。真正的前沿是 Factory 级别。**

---

## 真实生产中的 Factory 案例

### Paperclip — 零人类公司
一个 AI agent 团队，完全自主运营产品公司：
- 多个 AI agent 扮演不同角色（CEO、工程师、市场）
- 自主决策、自主代码生成、自主部署
- YouTube: `mc6xXdYg4Fk`

### OpenAI Codex — AI-Native 工程团队
```
Human: "Build a service that does X"
  ↓
Codex: 分析需求 → 创建 SPEC.md → 写代码 → 创建 PR
  ↓
CI: 自动测试 → 自动部署预览
  ↓
Codex: 根据 PR review 评论自动修复
  ↓
Human: 批准合并
```

### 自主 Bug 修复循环（GitHub Prototype）
```
Bug 发现
  → Agent 分析根因
  → Agent 生成修复代码
  → Agent 创建 PR
  → CI 自动测试
  → Agent 如测试失败则自动修复
  → 循环直到通过
```

---

## Rocky Garage 的革命性流水线

```
ophi: "我要一个产品"
    ↓
┌─────────────────────────────────────────────┐
│  SPEC AGENT（Spec Kit / LLM 驱动）          │
│  把需求转换成：                              │
│  - requirements.md（需求定义）              │
│  - SPEC.md（架构设计）                      │
│  - task list（任务树）                      │
│  - acceptance criteria（验收标准）           │
└─────────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────────┐
│  CODING AGENTS（Rocky = 主 Coding Agent）    │
│  - Architect Agent：系统设计                 │
│  - Backend Agent：API + 业务逻辑            │
│  - Frontend Agent：界面                     │
│  - Test Agent：自动化测试生成               │
│  → 每个 agent 写代码 → push → 创建 PR       │
└─────────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────────┐
│  CI/CD PIPELINE（GitHub Actions / n8n）     │
│  触发条件：PR 创建 / push / 定时             │
│  - 语义安全扫描（CodeQL / 专有 SAST）       │
│  - AI 生成测试执行                          │
│  - 自动化部署到 staging                      │
│  - 质量门禁：覆盖率、lint、类型检查         │
│  - 高信心自动合并，低信心发通知              │
└─────────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────────┐
│  SRE / MONITOR AGENT（Mastra）              │
│  - 监控：日志 + 指标 + trace                │
│  - 异常检测 → 根因分析                      │
│  - 自动开 GitHub Issue                      │
│  - Issue → Coding Agent 修复循环            │
└─────────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────────┐
│  AUTONOMOUS REPAIR LOOP（自愈机制）         │
│  失败 → 根因 → 修复 → 重测 → 通过           │
│  循环直到所有质量门禁通过                   │
└─────────────────────────────────────────────┘
    ↓
┌─────────────────────────────────────────────┐
│  GOVERNANCE LAYER（信任评分）               │
│  每个 agent 有信任分：                      │
│  - 高信心 + 历史好 → 自动批准               │
│  - 低信心 + 新 agent → 强制人工审核         │
│  - 所有操作写入不可变审计日志               │
└─────────────────────────────────────────────┘
    ↓
OpenClaw → Telegram: "产品上线了"
```

---

## 关键革命性机制

### 1. 自主测试生成循环（TDD + AI）
```
传统:  人写测试 → 人跑测试 → 人修复
AI-Factory: Agent 写测试 → CI 跑测试 → 失败 → Agent 自动修复 → 重测
                                          ↓
                                   循环直到通过
```

### 2. 信任评分 + 自适应门禁
```
Agent 信心 > 90% + 过去 10 次合并无 bug → 自动合并
Agent 信心 < 90% + 新代码 → 发送 Telegram 审批
```

### 3. 不可变审计日志
```
每一次代码变更都有记录：
who（哪个 agent）| what（改了啥）| why（决策原因）| trace_id（全链路可追溯）
```

### 4. 产品级监控闭环
```
部署 → 监控 → 异常 → Issue → Coding Agent 修复 → CI 重测 → 重新部署
                                      ↑________________________|
```

---

## 技术栈重新定位

| 工具 | 正确角色 | 之前错用 |
|------|---------|---------|
| **OpenClaw** | 人机入口 + 状态汇总 + 审批触发 | 被当作通用 runtime |
| **n8n** | CI/CD 编排 + webhook 触发 + 定时监控检查 | 被当作 AI runtime |
| **Mastra** | Durable execution + SRE agent + 自主修复循环 | 被当作备用 agent |
| **Langfuse** | 全链路 trace + 审计 + 质量评分 | 被象征性接入 |
| **GitHub Actions** | 确定性构建 + 测试 + 部署 + 质量门禁 | 只有 CI 壳 |
| **Rocky（我）** | 主 Coding Agent + Architect Agent | 被当作手动对话 |

---

## OpenClaw 本身的革命性用法

OpenClaw 不仅仅是对话壳，它本身就是 **Agent Runtime**：

```
OpenClaw 可以：
- 执行 shell 命令（真实工具调用）
- 读写文件系统
- 调用 GitHub API
- 浏览网页
- 运行 MCP 工具

这意味着 Rocky 可以作为 Coding Agent 直接：
- mkdir + write 代码文件
- git push 到 GitHub
- 通过 GitHub API 创建 PR
- 调用 GitHub Actions API 查看 CI 状态
```

**关键区别：之前 Rocky 只生成代码文本，没有主动执行工具链。**

---

## 下一步实现路径

### Phase 1（现在）：手动 Coding Agent 流水线
```
ophi → Rocky（生成代码）→ git push → GitHub Actions（测试+部署）→ OpenClaw（通知）
```

### Phase 2（短期）：自主测试循环
```
Rocky → 生成代码 + 生成测试 → CI 跑测试 → 失败则 Rocky 自动修复 → 重测
```

### Phase 3（中期）：多 Agent 协作
```
SPEC Agent（拆解需求）
  → Backend Agent（写后端） + Frontend Agent（写前端）并行
  → CI → SRE Agent（监控）
  → 自动修复循环
```

### Phase 4（长期）：信任评分 + 零人工干预
```
高信心自动合并
新功能自动生成
监控异常自动修复
```
