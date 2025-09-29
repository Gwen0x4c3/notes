### 一、在新项目中使用Spec Kit

#### 1. 初始化项目
**指令**：
```bash
specify init <PROJECT_NAME> --ai <AGENT>
```
- 说明：使用`specify init`命令初始化一个新项目，指定项目名称和AI代理（如Claude、GitHub Copilot或Gemini）。
- 示例：
  ```bash
  specify init photo-manager --ai claude
  ```
- 输出：创建一个新的Git仓库、项目目录结构、代理特定的命令模板（如`.claude/commands/`）和自动化脚本。

**项目结构示例**：
```
photo-manager/
├── .claude/
│   └── commands/
│       ├── constitution.md
│       ├── specify.md
│       ├── plan.md
│       ├── tasks.md
│       └── implement.md
├── memory/
├── scripts/
├── specs/
├── templates/
└── CLAUDE.md
```

#### 2. 建立项目章程（Constitution）
**指令**：
```
/constitution
```
- 说明：使用`/constitution`命令定义项目的指导原则，涵盖代码质量、测试标准、用户体验一致性和性能要求等。
- 示例输入：
  ```
  /constitution Create principles for a photo management application focusing on: user privacy (photos never leave local device), performance (fast loading of large photo collections), accessibility (keyboard navigation, screen reader support), and code quality (comprehensive testing, clean architecture). Include guidelines for data storage patterns and UI responsiveness standards.
  ```
- 输出：生成`memory/constitution.md`，包含项目的核心指导原则。

#### 3. 创建规范（Specification）
**指令**：
```
/specify
```
- 说明：使用`/specify`命令描述要构建的内容，聚焦于“是什么”和“为什么”，而不是技术栈。
- 示例输入：
  ```
  /specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.
  ```
- 输出：生成`specs/XXX-feature/spec.md`，记录功能需求。

#### 4. 创建技术实现计划（Plan）
**指令**：
```
/plan
```
- 说明：使用`/plan`命令指定技术栈和架构选择，定义实现方法。
- 示例输入：
  ```
  /plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
  ```
- 输出：生成`plan.md`，包含技术上下文、依赖、存储方案等。

#### 5. 任务分解（Tasks）
**指令**：
```
/tasks
```
- 说明：将计划分解为可执行的任务列表。
- 示例输入：基于`plan.md`自动生成任务，无需手动输入。
- 输出：生成`tasks.md`，列出具体开发任务。

#### 6. 实现（Implementation）
**指令**：
```
/implement
```
- 说明：根据`tasks.md`执行任务，通常结合测试驱动开发（TDD）。
- 示例输入：
  ```
  implement specs/002-create-taskify/plan.md
  ```
- 输出：生成源代码和测试文件。

**完整流程**：
1. 初始化：`specify init photo-manager --ai claude`
2. 定义章程：`/constitution ...`
3. 编写规范：`/specify ...`
4. 制定计划：`/plan ...`
5. 任务分解：`/tasks`
6. 实现：`/implement`

---

### 二、在现有项目中使用Spec Kit

#### 1. 在现有项目目录中初始化
**指令**：
```bash
specify init --here --ai <AGENT>
```
- 说明：在当前项目目录中初始化Spec Kit，不会创建新仓库，而是将模板和脚本集成到现有项目。
- 示例：
  ```bash
  /specify init --here --ai gemini
  ```
- 注意事项：
  - 如果项目中已有类似`CLAUDE.md`的代理配置文件，需手动检查和合并配置，以避免冲突。
  - 确保现有项目有Git仓库，否则需先运行`git init`。

#### 2. 调整项目章程
**指令**：
```
/constitution
```
- 说明：为现有项目补充或更新章程，确保与现有代码库的指导原则一致。
- 示例输入：
  ```
  /constitution Update principles to align with existing photo management app: ensure backward compatibility, maintain local storage for privacy, and optimize for large photo collections.
  ```
- 输出：更新或创建`memory/constitution.md`。

#### 3. 创建新功能规范
**指令**：
```
/specify
```
- 说明：在现有项目中为新功能添加规范。
- 示例输入：
  ```
  /specify Add a feature to the existing photo manager to allow tagging photos with custom labels and searching by tags.
  ```
- 输出：生成`specs/XXX-new-feature/spec.md`。

#### 4. 制定技术计划
**指令**：
```
/plan
```
- 说明：为新功能制定技术实现计划，需考虑现有技术栈。
- 示例输入：
  ```
  /plan Extend the existing Vite-based photo manager. Add a tagging system using local SQLite for storing tags. Ensure the UI remains responsive with vanilla JavaScript.
  ```
- 输出：生成`plan.md`。

#### 5. 任务分解与实现
**指令**：
```
/tasks
/implement
```
- 说明：与新项目类似，分解任务并实现，注意与现有代码集成。
- 示例输入（实现）：
  ```
  implement specs/003-add-tagging/plan.md
  ```
- 输出：生成新功能的代码和测试。

**完整流程**：
1. 初始化：`specify init --here --ai gemini`
2. 更新章程：`/constitution ...`
3. 新功能规范：`/specify ...`
4. 制定计划：`/plan ...`
5. 任务分解：`/tasks`
6. 实现：`/implement`

**注意**：
- 现有项目的复杂性可能需要手动调整生成的模板或配置文件。
- 如果使用Claude，需特别注意`CLAUDE.md`的配置冲突，建议参考[Issue #164](https://github.com/github/spec-kit/issues/164)。[](https://github.com/github/spec-kit/issues/164)

---

### 三、输入内容Demo总结

#### 新项目Demo（照片管理应用）
1. **初始化**：
   ```bash
   specify init photo-manager --ai claude
   ```
2. **章程**：
   ```
   /constitution Create principles for a photo management application focusing on: user privacy (photos never leave local device), performance (fast loading of large photo collections), accessibility (keyboard navigation, screen reader support), and code quality (comprehensive testing, clean architecture).
   ```
3. **规范**：
   ```
   /specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums.
   ```
4. **计划**：
   ```
   /plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
   ```

#### 现有项目Demo（为照片管理应用添加新功能）
1. **初始化**：
   ```bash
   uvx --from git+https://github.com/github/spec-kit.git specify init --here --ai gemini
   ```
2. **章程**：
   ```
   /constitution Update principles to align with existing photo management app: ensure backward compatibility, maintain local storage for privacy, and optimize for large photo collections.
   ```
3. **规范**：
   ```
   /specify Add a feature to the existing photo manager to allow tagging photos with custom labels and searching by tags.
   ```
4. **计划**：
   ```
   /plan Extend the existing Vite-based photo manager. Add a tagging system using local SQLite for storing tags. Ensure the UI remains responsive with vanilla JavaScript.
   ```