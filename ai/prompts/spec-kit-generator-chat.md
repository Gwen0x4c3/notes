### Current time: {{datetime}}
### User's language {{language}}
Project Requirement: {{project_description}}

Based on the above project requirement, generate the corresponding command contents according to the following official steps of GitHub Spec-Kit. Each part should strictly follow the style and format of the official example, ensuring the content focuses on the core "what" and "why" of the requirement, without excessive technical details. Output format is:

1. Establish project principles
Use the /constitution command to create your project's governing principles and development guidelines that will guide all subsequent development.
```
/constitution [Generated principles description, focusing on code quality, testing standards, user experience consistency, and performance requirements, etc.]
```
2. Create the spec
Use the /specify command to describe what you want to build. Focus on the what and why, not the tech stack.
```
/specify [Generated spec description, focusing on what to build and why, not involving tech stack]
```
3. Create a technical implementation plan
Use the /plan command to provide your tech stack and architecture choices.
```
/plan [Generated technical implementation plan, including tech stack and architecture choices, using minimal libraries, preferring native technologies, etc.]
```
4. Break down into tasks
Use /tasks to create an actionable task list from your implementation plan.
```
/tasks
```

5. Execute implementation
Use /implement to execute all tasks and build your feature according to the plan.
```
/implement
```
#Example output:
1. Establish project principles
Use the /constitution command to create your project's governing principles and development guidelines that will guide all subsequent development.
```
/constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
```
2. Create the spec
Use the /specify command to describe what you want to build. Focus on the what and why, not the tech stack.
```
/specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.`
```
3. Create a technical implementation plan
Use the /plan command to provide your tech stack and architecture choices.
```
/plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.`
```
4. Break down into tasks
Use /tasks to create an actionable task list from your implementation plan.
```
/tasks
```
5. Execute implementation
Use /implement to execute all tasks and build your feature according to the plan.
```
/implement
```