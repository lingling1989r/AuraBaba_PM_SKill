# AuraBaba PM Skill

> PM 项目管理、多设备执行环境与多 Agent 协作管理 Skill。

如果 AuraBaba 帮你把项目推进、任务分派和多 Agent 协作变得更省心，欢迎先点一个 GitHub Star 支持我们。

**Language:** [中文](#中文) | [English](#english)

---

## 中文

AuraBaba PM Skill 面向需要管理项目、任务、团队成员、AI Agent 和多台设备的负责人。你只需要描述目标和验收标准，AuraBaba 会帮助你把目标拆成可跟踪的项目任务，分派给合适的人类成员或 AI Agent，并在同一个工作台里汇总进度、评论、阻塞和交付物。

它适合这些关键词和场景：PM 项目管理、AI 项目管理、多 Agent 管理、多设备管理、Agent 团队协作、任务分派、项目进度跟踪、Issue 管理、自动化项目推进。

### 为什么需要它

#### 一个人负责方向，不等于一个人做完所有事

一个人可以负责方向、优先级和验收，但研究、开发、测试、内容、运营可以由不同 Agent 并行执行。你不需要逐个打开 Agent 安排工作，也不需要在多个聊天窗口里手工追进度。

例如只需说：

> 把本周产品发布目标交给团队推进：完成登录改版、回归测试、发布说明和上线检查，周五前给我可验收结果。

安装本 Skill 的 Agent 会读取 AuraBaba 中可用的执行者，系统根据能力和当前状态选择负责人，再自动评估、拆分并分派给多个 Agent。负责人只需在 AuraBaba 里查看父子任务、依赖、评论、状态和最终结果。

#### 多设备、多 Agent 的项目管理

- 将产品目标拆成前端、后端、测试、文档、运营等并行工作流。
- 在同一套 Issue、评论和项目上下文中协作管理人类成员和 AI Agent。
- 集中查看分布在不同设备上的 Agent 状态，避免任务散落在不同机器和对话里。
- 把决策、交付物和阻塞保存在项目时间线上，便于复盘和接力。
- 结合 AuraBaba Autopilot，让重复项目按时间或事件自动启动。

### 工作方式

```text
你的一条目标指令
      ↓
Skill 查询 AuraBaba 中可用的人类成员、Agent 和 Squad
      ↓
系统评估目标、匹配负责人并拆分任务
      ↓
多个 Agent 在不同设备并行执行
      ↓
父子 Issue 汇总进度、讨论、阻塞和结果
      ↓
你只负责方向、决策和验收
```

### 安装

#### ClawHub（QClaw、WorkBuddy、OpenClaw 等）

把下面这句话发给你的 Agent：

> 请安装灵光爸爸（AuraBaba）PM Skill，技能地址：https://clawhub.ai/hjyoite/skills/aurababa-platform

或执行：

```bash
openclaw skills install aurababa-platform
```

#### Codex、Claude Code、Cursor 等 Agent Skills 客户端

```bash
npx skills add lingling1989r/AuraBaba_PM_SKill -g
```

#### 国内直连下载

访问 [aurababa.com/skills](https://aurababa.com/skills)，可直接查看 `SKILL.md` 或下载完整 ZIP。

### 首次配置

1. 前往 [aurababa.com/register](https://aurababa.com/register) 注册并创建工作区。
2. 打开 **Settings -> API Tokens** 创建个人访问 Token；明文只显示一次。
3. 将 Token 安全保存为 Agent 的 `AURABABA_TOKEN`，不要提交到代码、日志或公开聊天。
4. 告诉 Agent 目标工作区的 slug，然后直接描述你希望团队完成的结果。

### 能力

- 发现并管理 Agent、人类成员、Squad 和执行者状态。
- 创建父子 Issue，并自动匹配合适的负责人。
- 接收项目目标、评估工作量并委派多个 Agent。
- 跟踪项目、任务、评论、标签、元数据和交付结果。
- 创建和维护日历事件、里程碑和项目节奏。

技能执行契约见 [SKILL.md](./SKILL.md)，API 行为依据见 [source map](./references/aurababa-platform-source-map.md)。

---

## English

AuraBaba PM Skill is for founders, PMs, engineering leads, and operators who need one place to manage projects, tasks, human teammates, AI agents, and multiple devices. Describe the outcome once; AuraBaba helps split the work into trackable issues, route it to the right human or agent owner, and keep progress, comments, blockers, and deliverables in one workspace.

Use it for project management, AI project management, multi-agent coordination, multi-device agent management, task delegation, issue tracking, delivery follow-up, and repeatable project automation.

### Why It Matters

#### One owner sets direction; a team executes

One person can own direction, priority, and acceptance while research, development, QA, content, and operations run in parallel through different agents. You do not need to open every agent manually or chase progress across several chat windows.

Example request:

> Move this week's product release forward: finish the login redesign, regression testing, release notes, and launch checklist, then give me reviewable results by Friday.

The agent with this skill can inspect available AuraBaba executors, match the right owner, break down the work, delegate to multiple agents, and keep the project visible through parent and child issues.

### Built For PM, Devices, And Agents

- Break product goals into parallel frontend, backend, QA, docs, and operations workflows.
- Coordinate humans and AI agents through the same issues, comments, and project context.
- See agent status across multiple devices instead of losing tasks in local machines or chat threads.
- Preserve decisions, deliverables, and blockers on the project timeline.
- Combine with AuraBaba Autopilot to start recurring projects on a schedule or event.

### How It Works

```text
One outcome from you
      ↓
Skill discovers available humans, agents, and squads in AuraBaba
      ↓
AuraBaba evaluates scope, chooses owners, and splits work
      ↓
Multiple agents execute in parallel across devices
      ↓
Parent and child issues collect progress, discussion, blockers, and results
      ↓
You focus on direction, decisions, and acceptance
```

### Install

#### ClawHub

Ask your agent:

> Please install the AuraBaba PM Skill: https://clawhub.ai/hjyoite/skills/aurababa-platform

Or run:

```bash
openclaw skills install aurababa-platform
```

#### Codex, Claude Code, Cursor, And Other Agent Skill Clients

```bash
npx skills add lingling1989r/AuraBaba_PM_SKill -g
```

#### Direct Download In China

Visit [aurababa.com/skills](https://aurababa.com/skills) to view `SKILL.md` or download the ZIP package.

### First Setup

1. Register and create a workspace at [aurababa.com/register](https://aurababa.com/register).
2. Open **Settings -> API Tokens** and create a personal access token. The plaintext token is shown only once.
3. Store the token securely as `AURABABA_TOKEN` for your agent. Do not commit it to code, logs, or public chats.
4. Tell the agent your target workspace slug, then describe the result you want the team to deliver.

### Capabilities

- Discover and manage agents, human members, squads, and executor status.
- Create parent and child issues and match work to suitable owners.
- Receive project goals, estimate scope, and delegate across multiple agents.
- Track projects, tasks, comments, labels, metadata, and deliverables.
- Create and maintain calendar events, milestones, and project rhythm.

See [SKILL.md](./SKILL.md) for the skill contract and [source map](./references/aurababa-platform-source-map.md) for API behavior references.

---

## 加入用户交流群 / Join The User Group

想交流 PM 项目管理、多设备 Agent 调度、多 Agent 协作实践，或反馈 AuraBaba 使用问题，可以扫码加 V 进入用户交流群。

For product feedback, PM workflows, multi-device agent operations, or multi-agent coordination discussions, scan the QR code below and join the user group.

<img src="assets/wechat-group.jpg" alt="AuraBaba WeChat user group QR code" width="240">

## License

ClawHub 发行版本使用 MIT-0 许可。
