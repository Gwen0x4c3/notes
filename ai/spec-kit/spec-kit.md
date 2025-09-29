## Spec Kit

https://github.com/github/spec-kit



## Installation & Usage
### 1. Install Specify
Install once and use everywhere:

```
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Then use the tool directly:

```
specify init <PROJECT_NAME>
specify check
```

### 2. Establish project principles

Use the **`/constitution`** command to create your project's governing principles and development guidelines that will guide all subsequent development.

```
/constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
```

### 3. Create the spec

Use the **`/specify`** command to describe what you want to build. Focus on the **what** and **why**, not the tech stack.

```
/specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.
```

### 4. Create a technical implementation plan

Use the **`/plan`** command to provide your tech stack and architecture choices.

```
/plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
```

### 5. Break down into tasks

Use **`/tasks`** to create an actionable task list from your implementation plan.

```
/tasks
```

### 6. Execute implementation

Use **`/implement`** to execute all tasks and build your feature according to the plan.

```
/implement
```

For detailed step-by-step instructions, see our [comprehensive guide](https://github.com/github/spec-kit/blob/main/spec-driven.md).

## Prompt
[Assistant Prompt](../prompts/spec-kit-generator-prompt.md) | [Message Prompt](../prompts/spec-kit-generator-prompt.md)

## Summary

Spec-Kit 是一个面向规范驱动开发（Spec-Driven Development, SDD）的工具包，主张先由可执行规范推动软件实现，而非传统的先写代码。其核心特点包括：

1. **理念与特色**  
   - 强调以目标与意图（“做什么”、“为什么”）为中心，减少过早关注实现细节（“怎么做”）。
   - 集成主流 AI 代理（如 Claude、Gemini、Copilot），可用于优化规范、制定技术方案、任务拆解。
   - 为用户提供规范驱动的开发流程，帮助团队高效协作并适应多样技术栈和企业需求。

2. **主要优点**  
   - 推动高质量、以用户需求为中心的软件开发，可灵活适应企业合规等约束条件。
   - 提供清晰的 CLI 工具流程（/specify, /plan, /tasks），降低项目启动时的迷茫。
   - 与现代敏捷开发实践契合，引入 AI 提速想法到代码的转化。

3. **潜在不足**  
   - 对 AI 代理依赖较重，可能引入不一致或过度复杂化，需人工干预。
   - 初期设置有一定门槛，需要安装特定工具与依赖（如 uvx、dotnet）。
   - 更适合新项目或迭代开发，对于小型修改或维护老系统可能显得复杂。

4. **与同类工具对比**  
   - Spec-Kit 侧重规范自动生成与可执行性，依托 GitHub 生态，易集成。
   - AgentOS 偏重可定制 AI 代理编码工作流，BMAD 强调多人协作、角色分工，皆可与 Spec-Kit 互补，形成完整开发链路。

5. **典型使用场景**  
   - 新项目启动时快速结构化想法并形成规范。
   - 已集成 AI 工具的团队借助 Spec-Kit 提升产出质量，减少与需求不符的代码生成。
   - 多角色团队高效协作，规范、方案、任务三步走，满足合规与透明需求。
   - 对已有项目进行功能增强、技术探索等场景。

6. **不适宜场景**  
   - 简单脚本、小工具开发，CLi 流程可能反而拖慢效率。
   - 维护旧代码、技术栈受限时，AI 可能无法胜任高级推理、场景理解。
   - 非软件项目如硬件或市场策划，通用 PRD 工具更合适。
   - 无可用 AI 代理或限制访问环境下，Spec-Kit 功能受限。
   - 高定制、高敏感项目，人工精准控制优先，AI 批量生成风险较高。

**总结**：  
Spec-Kit 非常适合 AI 辅助、规范驱动的软件团队。它能够将产品规范转化为清晰的技术方案和可执行任务，显著提升敏捷开发、协作透明度和效率。但对于极为轻量或无 AI 需求的场景来说，反而可能增加不必要的复杂度。推荐先在小型原型项目中试用其核心流程，以评估适应性和实际价值。