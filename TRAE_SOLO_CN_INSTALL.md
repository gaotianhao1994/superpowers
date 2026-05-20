# Superpowers for Trae Solo CN 安装指南

本指南将帮助您将 Superpowers 技能库安装到 Trae Solo CN 中。

## 安装步骤

### 方法 1：项目本地安装（推荐）

1. **将 Superpowers 项目克隆或下载到您的项目目录中**

   ```bash
   git clone https://github.com/obra/superpowers.git
   ```

   或者直接将整个项目文件夹复制到您的项目中。

2. **在您的项目根目录中创建 TRAE.md 文件**

   如果 Trae Solo CN 使用类似 AGENTS.md、CLAUDE.md 或 GEMINI.md 的配置文件，请在您的项目根目录创建或编辑该文件，添加以下内容：

   ```
   @./superpowers/skills/using-superpowers/SKILL.md
   @./superpowers/skills/using-superpowers/references/trae-tools.md
   ```

   注意：请根据您放置 Superpowers 项目的实际路径调整上述路径。

3. **配置技能路径**

   如果 Trae Solo CN 支持配置技能搜索路径，请将以下路径添加到技能搜索路径中：
   ```
   ./superpowers/skills/
   ```

### 方法 2：全局安装

1. **将 Superpowers 项目克隆或下载到您的主目录中**

   ```bash
   cd ~
   git clone https://github.com/obra/superpowers.git
   ```

2. **创建全局配置文件**

   在 Trae Solo CN 的全局配置目录中创建或编辑配置文件，添加以下内容：
   ```
   @~/superpowers/skills/using-superpowers/SKILL.md
   @~/superpowers/skills/using-superpowers/references/trae-tools.md
   ```

3. **配置全局技能路径**

   将 `~/superpowers/skills/` 添加到 Trae Solo CN 的全局技能搜索路径中。

## 验证安装

安装完成后，在 Trae Solo CN 中开始一个新会话，然后问：

```
告诉我关于你的 superpowers
```

如果 Superpowers 正确加载，您应该会看到相关的回应。

## 使用技能

### 手动调用技能

如果 Trae Solo CN 有 Skill 工具，您可以使用它来调用技能：

```
使用 Skill 工具调用 brainstorming 技能
```

或者如果需要手动读取技能文件：

```
读取 ./superpowers/skills/brainstorming/SKILL.md
```

### 可用的技能

Superpowers 包含以下技能：

- **brainstorming** - 在编写代码前激活，通过问题细化想法，探索替代方案，分段展示设计以供验证
- **using-git-worktrees** - 在设计批准后激活，在新分支上创建隔离工作区，运行项目设置，验证干净的测试基线
- **writing-plans** - 在设计批准后激活，将工作分解为小任务（每个 2-5 分钟），每个任务都有确切的文件路径、完整的代码和验证步骤
- **subagent-driven-development** - 在有计划后激活，为每个任务分派新的子代理，进行两阶段审查（规范合规性，然后是代码质量）
- **executing-plans** - 在有计划后激活，分批执行并在人工检查点暂停
- **test-driven-development** - 在实现过程中激活，强制执行红-绿-重构：编写失败的测试，看着它失败，编写最少的代码，看着它通过，提交。删除在测试前编写的代码
- **requesting-code-review** - 在任务之间激活，根据计划审查，按严重性报告问题。关键问题会阻止进度
- **receiving-code-review** - 响应代码审查反馈
- **systematic-debugging** - 4 阶段根本原因过程（包括根本原因跟踪、深度防御、基于条件的等待技术）
- **verification-before-completion** - 确保问题真正得到解决
- **finishing-a-development-branch** - 在任务完成后激活，验证测试，提供选项（合并/PR/保留/丢弃），清理工作树
- **writing-skills** - 创建遵循最佳实践的新技能（包括测试方法）
- **using-superpowers** - 介绍技能系统
- **dispatching-parallel-agents** - 并行子代理工作流

## 工具映射

由于 Superpowers 技能是为 Claude Code 编写的，您可能需要将技能中提到的工具名称映射到 Trae Solo CN 中可用的工具。

请编辑 `skills/using-superpowers/references/trae-tools.md` 文件，根据 Trae Solo CN 的实际工具名称更新映射表。

## 自定义

### 修改工具映射

编辑 `skills/using-superpowers/references/trae-tools.md` 文件，将 Claude Code 的工具名称映射到 Trae Solo CN 的工具名称。

### 添加自定义技能

您可以在 `skills/` 目录下添加自己的技能，或者创建一个单独的技能目录并将其添加到技能搜索路径中。

## 故障排除

### 技能没有自动加载

- 确保 TRAE.md（或相应的配置文件）在正确的位置
- 检查文件路径是否正确
- 尝试重新启动 Trae Solo CN

### 工具不可用

- 检查 `trae-tools.md` 中的工具映射是否正确
- 如果 Trae Solo CN 没有某个工具，尝试使用最接近的替代工具或调整工作流程

### 技能找不到

- 确保技能路径已正确添加到 Trae Solo CN 的技能搜索路径中
- 检查每个技能文件夹中是否有有效的 SKILL.md 文件

## 获取帮助

- Superpowers 项目主页：https://github.com/obra/superpowers
- 报告问题：https://github.com/obra/superpowers/issues
- Discord 社区：https://discord.gg/35wsABTejz

## 更新

要更新 Superpowers，只需在项目目录中运行：

```bash
git pull
```

## 注意事项

- 本安装指南是基于 Superpowers 对其他平台的支持方式编写的，可能需要根据 Trae Solo CN 的具体功能进行调整
- 如果 Trae Solo CN 有插件系统，建议优先使用插件方式安装（如果可用）
- 如果遇到问题，请参考其他平台的安装方式（Claude Code、OpenCode、Cursor 等）进行适配
