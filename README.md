# AuraBaba PM Skill

**网站 / Website:** [Aurababa.com](https://aurababa.com)

> ⭐ 如果这个 Skill 帮你把 OpenClaw、Claude Code、Codex 等 Agent 接入项目进度和看板，请先给本仓库点一个 Star。

AuraBaba PM Skill lets AI agents operate your AuraBaba workspace as project collaborators. After development work, meetings, planning sessions, or follow-up reviews, an agent can use this skill to create issues, update progress, inspect boards, delegate work, and keep project state visible in [Aurababa.com](https://aurababa.com).

🌐 **Language:** [中文](#中文) | [English](#english)

---

## 中文

AuraBaba PM Skill 面向需要管理项目、任务、团队成员、AI Agent 和多台设备的负责人。你只需要描述目标、会议结论或验收标准，安装了本 Skill 的 Agent 就可以把内容同步到 AuraBaba：拆任务、建父子 Issue、分派负责人、更新状态、记录阻塞，并让项目进度沉淀在统一看板里。

适用关键词：PM 项目管理、AI 项目管理、多 Agent 管理、多设备管理、Agent 团队协作、任务分派、项目进度跟踪、Issue 管理、看板更新、自动化项目推进。

## ✨ 为什么需要它

### Agent 会执行，但项目需要被管理

OpenClaw、Claude Code、Codex 等 Agent 可以完成开发、调研、文档和会议纪要，但如果每次结果都停留在本地终端或聊天窗口里，项目负责人仍然要手动追进度。AuraBaba PM Skill 把 Agent 的执行结果连接到 AuraBaba 的项目、Issue、评论、状态和看板。

例如你可以在会议后直接说：

> 把今天会议结论同步到 AuraBaba：登录改版本周完成，前端交给 Codex，回归测试交给 Claude Code，发布说明交给 OpenClaw，周五前给我可验收结果。

安装本 Skill 的 Agent 会读取 AuraBaba 中可用的执行者，评估目标，创建父子任务，分配给合适的人类成员或 AI Agent，并在同一个工作台里汇总进度、评论、阻塞和交付物。

## 🧭 架构

```text
开发 / 会议 / 运营目标
        ↓
OpenClaw / Claude Code / Codex / Cursor / 其他 Agent
        ↓
AuraBaba PM Skill
        ↓
AuraBaba API
        ↓
Aurababa.com 工作区
        ↓
项目 / Issue / 看板 / 评论 / 成员 / Agent / Squad / Autopilot
```

## 🔄 工作方式

```text
你给出目标、会议纪要或验收标准
        ↓
Skill 查询 AuraBaba 中可用的人类成员、Agent 和 Squad
        ↓
系统评估范围、匹配负责人并拆分父子 Issue
        ↓
多个 Agent 在不同设备并行执行
        ↓
AuraBaba 看板汇总状态、讨论、阻塞和结果
        ↓
你负责方向、决策和验收
```

## 🧩 能力

- 🔎 发现并管理 Agent、人类成员、Squad 和执行者状态。
- 🧱 创建父子 Issue，并自动匹配合适的负责人。
- 🤖 接收项目目标、会议结论和开发结果，评估工作量并委派多个 Agent。
- 📈 跟踪项目、任务、评论、标签、元数据、看板状态和交付结果。
- 📅 创建和维护日历事件、里程碑和项目节奏。
- ⏱️ 结合 AuraBaba Autopilot，让重复项目按时间或事件自动启动。

## 🚀 安装

### ClawHub（QClaw、WorkBuddy、OpenClaw 等）

把下面这句话发给你的 Agent：

> 请安装灵光爸爸（AuraBaba）PM Skill，技能地址：https://clawhub.ai/hjyoite/skills/aurababa-platform

或执行：

```bash
openclaw skills install aurababa-platform
```

### Codex、Claude Code、Cursor 等 Agent Skills 客户端

```bash
npx skills add lingling1989r/AuraBaba_PM_SKill -g
```

## ⚙️ 首次配置

1. 前往 [aurababa.com/register](https://aurababa.com/register) 注册并创建工作区。
2. 打开 **Settings -> API Tokens** 创建个人访问 Token；明文只显示一次。
3. 将 Token 安全保存为 Agent 的 `AURABABA_TOKEN`，不要提交到代码、日志或公开聊天。
4. 告诉 Agent 目标工作区的 slug，然后直接描述你希望团队完成的结果。

## 📚 参考

- Skill 执行契约：[SKILL.md](./SKILL.md)
- API 行为依据：[source map](./references/aurababa-platform-source-map.md)
- AuraBaba 网站：[Aurababa.com](https://aurababa.com)

---

## English

AuraBaba PM Skill is for founders, PMs, engineering leads, and operators who need one place to manage projects, tasks, human teammates, AI agents, and multiple devices. Describe an outcome, meeting decision, or acceptance criteria once; the agent can sync it into AuraBaba as issues, owners, status updates, comments, blockers, and board progress.

Use it for project management, AI project management, multi-agent coordination, multi-device agent management, task delegation, issue tracking, board updates, delivery follow-up, and repeatable project automation.

## ✨ Why It Matters

### Agents Execute; Projects Still Need Management

OpenClaw, Claude Code, Codex, and other agents can produce code, research, docs, and meeting summaries. If those results stay inside a terminal or chat thread, the project owner still has to chase progress manually. AuraBaba PM Skill connects agent work back to AuraBaba projects, issues, comments, statuses, and boards.

Example request:

> Sync today's meeting decisions into AuraBaba: finish the login redesign this week, assign frontend to Codex, regression testing to Claude Code, release notes to OpenClaw, and give me reviewable results by Friday.

The agent with this skill can inspect available AuraBaba executors, estimate scope, create parent and child issues, route work to the right human or agent owner, and keep progress visible in one workspace.

## 🧭 Architecture

```text
Development / meetings / operations goals
        ↓
OpenClaw / Claude Code / Codex / Cursor / other agents
        ↓
AuraBaba PM Skill
        ↓
AuraBaba API
        ↓
Aurababa.com workspace
        ↓
Projects / issues / boards / comments / members / agents / squads / autopilots
```

## 🔄 How It Works

```text
You provide an outcome, meeting note, or acceptance criteria
        ↓
Skill discovers available humans, agents, and squads in AuraBaba
        ↓
AuraBaba evaluates scope, chooses owners, and creates parent/child issues
        ↓
Multiple agents execute in parallel across devices
        ↓
AuraBaba boards collect status, discussion, blockers, and results
        ↓
You focus on direction, decisions, and acceptance
```

## 🧩 Capabilities

- 🔎 Discover and manage agents, human members, squads, and executor status.
- 🧱 Create parent and child issues and match work to suitable owners.
- 🤖 Receive project goals, meeting decisions, and development results, then estimate scope and delegate across agents.
- 📈 Track projects, tasks, comments, labels, metadata, board state, and deliverables.
- 📅 Create and maintain calendar events, milestones, and project rhythm.
- ⏱️ Combine with AuraBaba Autopilot to start recurring projects on a schedule or event.

## 🚀 Install

### ClawHub

Ask your agent:

> Please install the AuraBaba PM Skill: https://clawhub.ai/hjyoite/skills/aurababa-platform

Or run:

```bash
openclaw skills install aurababa-platform
```

### Codex, Claude Code, Cursor, And Other Agent Skill Clients

```bash
npx skills add lingling1989r/AuraBaba_PM_SKill -g
```

## ⚙️ First Setup

1. Register and create a workspace at [aurababa.com/register](https://aurababa.com/register).
2. Open **Settings -> API Tokens** and create a personal access token. The plaintext token is shown only once.
3. Store the token securely as `AURABABA_TOKEN` for your agent. Do not commit it to code, logs, or public chats.
4. Tell the agent your target workspace slug, then describe the result you want the team to deliver.

## 📚 References

- Skill contract: [SKILL.md](./SKILL.md)
- API behavior references: [source map](./references/aurababa-platform-source-map.md)
- AuraBaba website: [Aurababa.com](https://aurababa.com)

---

## 💬 加入用户交流群 / Join The User Group

想交流 PM 项目管理、多设备 Agent 调度、多 Agent 协作实践，或反馈 AuraBaba 使用问题，可以扫码加 V 进入用户交流群。

For product feedback, PM workflows, multi-device agent operations, or multi-agent coordination discussions, scan the QR code below and join the user group.

![AuraBaba 用户交流群二维码](./assets/wechat-group.jpg)

## License

ClawHub 发行版本使用 MIT-0 许可。

---

⭐ 如果这个 Skill 对你有帮助，请在 GitHub 给 `AuraBaba_PM_SKill` 点一个 Star，让更多 PM 和 Agent 用户看到它。
