# usage

BMad Method (突破性敏捷 AI 驱动开发方法) 的设计旨在适应不同项目阶段的需求。无论是从零开始的新项目 (Greenfield)，还是在现有代码库上进行迭代 (Brownfield)，其核心思路都是用专业化的 AI Agent 团队来组织工作流和管理上下文。

整个方法论通过一套 Agent 驱动的流程，将一个高层级的项目想法，逐步细化为可执行的开发任务。

1. **构思与分析 (Ideation & Analysis) - Analyst Agent：**
   * 目标： 澄清项目概念，进行头脑风暴，产出《项目简报》（Project Brief）。
   * 关键点： 强调 Agent 的作用是“教练”而非“任务执行者”，通过高级的启发式方法（如六顶思考帽、五个为什么、角色扮演）帮助用户深入思考。
2. **产品规划 (Product Planning) - Product Manager (PM) Agent：**
   * 目标： 基于《项目简报》产出《产品需求文档》（PRD）。
   * 关键点： 确保 PRD 包含功能和非功能性需求，并帮助定义最小可行产品（MVP）的范围，避免过度开发，同时使用“事后诸葛亮”等高级启发式来优化需求。
3. **架构设计 (Architecture Design) - Architect Agent：**
   * 目标： 基于 PRD 产出《架构设计文档》。
   * 关键点： 建议使用更强大的 LLM 模型（如 Opus）来生成高质量的架构，并详细定义技术栈、编码标准、数据模型和项目目录结构，以确保开发阶段的一致性。
4. **任务拆解与上下文工程 (Sharding & Context Engineering)：**
   * 目标： 将大型文档（PRD 和架构）拆解（Shard）成包含完整上下文的小文件。
   * 关键点： 这是 BMad Method 的核心。将文档拆解为如 `coding-standards.md`、`tech-stack.md` 等小文件，确保后续的开发 Agent 每次只加载其工作所需的最小、最相关的上下文，防止“上下文污染”。
5. **开发与执行 (Development & Execution) - Scrum Master (SM) & Dev Agent：**
   * SM Agent： 读取 Epic 和 Stories，并结合架构文档，创建包含所有上下文的、详细的开发故事文件，供 Dev Agent 使用。SM Agent 还具备“纠正路线”功能，以应对项目中期的大幅变更。
   * Dev Agent： 接收 SM Agent 提供的故事文件，并根据其中的具体任务清单、编码标准和技术栈进行代码实现。
6. **质量保障 (Quality Assurance) - QA Agent：**
   * 目标： 审查 Dev Agent 的代码实现。
   * 关键点： QA Agent (Quinn) 会深度检查代码是否符合架构标准、编码规范，确保 Agent 没有偏离轨道或在错误的位置放置文件。

***

### 场景一：启动新项目 (Greenfield Project)

对于新项目，利用 BMad 完整的 Agent 驱动规划 (Agentic Planning) 能力，从一个高层级的想法开始，逐步构建出详尽的文档和开发蓝图。

#### 步骤 1：环境搭建与 Agent 部署

1. 初始化项目： 在新的空项目目录中，运行 BMad 的安装命令：`npx bmad-method install`。
2. 配置偏好： 在 `.bmad-core/data/technical-preferences.md` 中定义技术栈、编码标准和设计原则，以指导后续 Agent 的决策。

#### 步骤 2：Agent 驱动规划（文档创建）

这个阶段是 BMad 最强大的功能之一，它确保了项目拥有完整、一致的初始文档。

| Agent 角色              | 目标文档                            | 命令/操作 (示例)                                                 |
| --------------------- | ------------------------------- | ---------------------------------------------------------- |
| Analyst Agent (分析师)   | `project-brief.md` (项目简报)       | `@analyst Create a new project for an online library app.` |
| PM Agent (产品经理)       | `prd.md` (产品需求文档)               | `@pm Draft PRD based on the project brief.`                |
| Architect Agent (架构师) | `architecture-design.md` (架构设计) | `@architect Create the system architecture for the PRD.`   |
| PO Agent (产品负责人)      | `epics.md` (史诗级任务)              | `@po Draft epics from the PRD.`                            |

成果： 一套经过多个专业 Agent 协作、且彼此一致的规划文档。

#### 步骤 3：上下文工程与开发周期（代码实现）

规划文档就绪后，开发工作流开始。

1. 上下文分片 (Sharding)：
   * 运行 Scrum Master (SM) Agent 的分片命令，将大型文档分解为独立的、包含完整上下文的开发故事文件（例如 `1.1-browse-books.md`）。
   * _命令示例：_ `@sm Shard the latest Epic into user stories.`
2. 开发与迭代：
   * Dev Agent 专注于实现当前的故事文件，无需担心上下文丢失，因为 SM 已经将 PRD 和架构中的相关部分嵌入到文件中。
   * _命令示例：_ `@dev Implement the user authentication module for this story.`
3. 质量关卡 (Quality Gate)：
   * QA Test Architect Agent 遵循测试先行 (Test-First) 的原则，进行风险分析、测试设计和代码审查。
   * _命令示例：_ `@qa *review {story}` (触发全面审查)。

***

### 场景二：在现有项目上使用 (Brownfield Project)

在现有项目上使用 BMad，目标是标准化未来的开发工作、提高代码质量，并解决老项目常见的文档缺失和上下文断裂问题。

#### 步骤 1：环境搭建与初始 Agent 配置

1. 安装 BMad： 在现有代码库的根目录安装 BMad：`npx bmad-method install`。
2. 定义核心上下文：
   * 在 BMad 的配置文件中，设置 `devLoadAlwaysFiles` 参数。将老项目中任何重要的文档（如 API 约定、数据库模式图、主要的 README 文件）加入此列表。这能确保所有 Agent 都能始终加载这些现有项目的“规则”。

#### 步骤 2：文档逆向工程（补齐文档）

这是 Brownfield 项目的关键步骤。使用 BMad 的规划 Agent 来分析现有代码，并生成缺失的文档，为未来的开发建立一个“Source of Truth”。

| Agent 角色         | 目标操作                          | 目的                                   |
| ---------------- | ----------------------------- | ------------------------------------ |
| Analyst/PM Agent | 分析现有代码： 指导 Agent 审查核心功能模块。    | 梳理和生成缺失的 PRD 或用户故事，定义“现有系统应该是什么样子的”。 |
| Architect Agent  | 生成架构文档： 指导 Agent 分析依赖、服务和数据流。 | 从代码中抽取系统架构图和设计说明，记录现有系统的结构。          |

#### 3. 步骤 3：新功能或维护工作流

一旦有了基础的文档（无论是新的还是逆向生成的），您就可以将未来的所有开发任务纳入 BMad 结构。

1. 任务启动：
   * 对于新功能或大型重构，将其定义为一个 Epic。
2. 跳过初始规划：
   * 如果任务很明确（例如，修复一个 Bug），可以直接从 SM Agent 开始。
3. 分片与开发：
   * SM Agent 读取您为新功能编写的 Epic，并将其分片成包含现有系统上下文（通过 `devLoadAlwaysFiles` 加载）和新功能需求的故事文件。
   * Dev/QA Agent 严格按照这个结构化的 Story 文件进行开发和审查。

#### 总结对比

| 特征    | 新项目 (Greenfield)                 | 现有项目 (Brownfield)                                         |
| ----- | -------------------------------- | --------------------------------------------------------- |
| 工作流起点 | 始于 Analyst Agent 的零散创意。          | 始于文档逆向工程或直接的 SM Agent 分片。                                 |
| 核心焦点  | Agent 驱动的完整文档创建 和 功能实现。          | 将现有上下文标准化、文档补齐，以及结构化的维护/迭代。                               |
| 关键工具  | Analyst, PM, Architect (用于创建文档)。 | PM, Architect (用于生成缺失文档)；`devLoadAlwaysFiles` (用于加载现有规则)。 |
