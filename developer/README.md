# Developer MCP Server

A powerful context management system designed specifically for software development teams. The Developer MCP Server maintains persistent context across your coding sessions, ensuring you never lose track of your project's structure, dependencies, and progress.

## Features

- **Persistent Development Context**: Pick up exactly where you left off in your last session, with complete context about the components, issues, and tasks you were working on.

- **Session Management**: Start new development sessions and record your achievements, task updates, and project status changes when you finish, creating a persistent record of your development activities.

- **Dependency Tracking**: Understand how components, features, and technologies relate to each other with a comprehensive dependency model.

- **Project Status Insights**: Get immediate visibility into project progress, including status of components, features, issues, and milestones.

- **Component Context Retrieval**: Understand any component's purpose, implementation details, dependencies, and related issues at a glance.

- **Decision History**: Track why architectural and implementation decisions were made, when, and by whom—no more guessing why something was built a certain way.

- **Milestone Progress Tracking**: Monitor progress toward project milestones and identify potential bottlenecks before they derail your timeline.

- **Related Entity Discovery**: Quickly find all related entities for any component, feature, or task to understand its complete context.

## Entities

The Developer MCP Server recognizes the following types of entities in your software development context:

- **Project**: Overall software project or product
- **Component**: Module, service, package, or logical unit within a project
- **Feature**: Specific functionality being developed
- **Issue**: Bug, problem, or defect to be addressed
- **Task**: Work item or activity needed for development
- **Developer**: Team member working on the project
- **Technology**: Programming language, framework, library, or tool
- **Decision**: Important technical or architectural decision
- **Milestone**: Key project deadline or phase
- **Environment**: Development, staging, or production environment
- **Documentation**: Project documentation resource
- **Requirement**: Project requirement or specification
- **Status**: Entity status values (inactive, active, complete)
- **Priority**: Priority level values (high, low)

## Relationships

The Developer MCP Server models the following relationships between entities, mirroring real-world software development dynamics:

- **depends_on**: Entity A requires Entity B to function
- **implements**: Component implements a feature
- **assigned_to**: Task is assigned to a developer
- **blocked_by**: Task is blocked by an issue
- **uses**: Component uses a technology
- **part_of**: Component is part of a project
- **contains**: Project contains a component
- **works_on**: Developer works on a project/component
- **related_to**: General relationship between entities
- **affects**: Issue affects a component
- **resolves**: Task resolves an issue
- **created_by**: Entity was created by a developer
- **documented_in**: Component is documented in documentation
- **decided_in**: Decision was made in a meeting
- **required_by**: Feature is required by a requirement
- **has_status**: Links entities to their current status (inactive, active, complete)
- **has_priority**: Links entities to their priority level (high, low)
- **depends_on_milestone**: Task depends on reaching a milestone
- **precedes**: Indicates that one task comes before another in a sequence
- **reviews**: Developer reviews a component
- **tested_in**: Component is tested in an environment

## Status and Priority Management

The Developer MCP Server provides robust status and priority tracking capabilities:

- **Status Values**: 
  - **inactive**: Entity has not yet been started or is currently paused
  - **active**: Entity is currently being worked on
  - **complete**: Entity has been finished

- **Priority Values**:
  - **high**: Entity requires immediate attention or has significant impact
  - **low**: Entity can be addressed when higher priority items are complete

- **Sequential Task Management**:
  - Define which tasks must be completed before others can begin
  - Visualize the natural workflow of development tasks
  - Identify critical path dependencies in your development process

## Environment Variables

The Developer MCP Server supports the following environment variables to customize where data is stored:

- **MEMORY_FILE_PATH**: Path where the knowledge graph data will be stored
  - Can be absolute or relative (relative paths use current working directory)
  - Default: `./developer/memory.json`

- **SESSIONS_FILE_PATH**: Path where session data will be stored
  - Can be absolute or relative (relative paths use current working directory)
  - Default: `./developer/sessions.json`

Example usage:

```bash
# Store data in the current directory
MEMORY_FILE_PATH="./dev-memory.json" SESSIONS_FILE_PATH="./dev-sessions.json" npx github:tejpalvirk/contextmanager-developer

# Store data in a specific location (absolute path)
MEMORY_FILE_PATH="/path/to/data/developer-memory.json" npx github:tejpalvirk/contextmanager-developer

# Store data in user's home directory
MEMORY_FILE_PATH="$HOME/contextmanager/developer-memory.json" npx github:tejpalvirk/contextmanager-developer
```

## Available Tools

The Developer MCP Server provides the following tools:

- **startsession**: Starts a new development session and provides information about recent sessions, active projects, high-priority tasks, and upcoming milestones. Shows status and priority information for tasks and other entities, as well as identifies tasks ready to be worked on based on sequential dependencies.

- **loadcontext**: Loads detailed context for an entity (project, component, feature, task, etc.) and tracks this context loading as part of the current session. Shows status values (inactive, active, complete), priority levels (high, low), and sequential relationships.

- **endsession**: Performs a structured analysis of the development session through multiple stages (summary, achievements, task updates, new tasks, status updates, project status) and records this information in the persistent knowledge graph.

- **buildcontext**: Creates new entities, relations (including has_status, has_priority, and precedes), or observations in the knowledge graph.

- **deletecontext**: Removes entities, relations (including status, priority, and sequential relations), or observations from the knowledge graph.

- **advancedcontext**: Retrieves information from the knowledge graph with different query types (graph, search, nodes, related, decisions, milestone, status, priority, sequence).

## Prompts

Here are some example prompts to use with the Developer MCP Server:

### Starting a Session
```
"Start a new development session for me."
```

### Loading Context
```
"Show me the current status of the AuthService project."
"Load the context for the UserProfile component."
"What are the open issues affecting the Payment feature?"
"Show me details about the upcoming Q2 Release milestone."
"Show me all tasks with high priority status in the Authentication module."
"What tasks need to be completed before we can start implementing the checkout flow?"
```

### Recording Session Progress
```
"End my development session. I've been working on AuthService for 3 hours and completed user authentication flow implementation."
"Record my achievements for today: implemented password reset feature and fixed login redirect bug."
"Update the status of these tasks: Login Form is complete, User Registration is in progress."
"Create new tasks for the next sprint: Implement MFA, Add social login options. Set MFA as high priority and make it precede the social login task."
```

### Knowledge Graph Management
```
"Create a new feature called 'BillingSystem' in the ProjectX project with status active and high priority."
"Create a relationship showing that PaymentComponent implements BillingSystem feature."
"Show me all components that depend on the DatabaseService."
"What decisions have been made about the authentication approach for ProjectX?"
"Update the status of the API Documentation task to complete."
"Set the User Profile feature as a prerequisite for the Payment Processing feature."
```

## Usage

The Developer MCP Server excels in scenarios like:

### Context Continuity
```
"Let me see the component I was working on yesterday and all its dependencies."
```
The server retrieves your most recently accessed components along with their dependencies, issues, and related tasks, allowing you to instantly resume work without spending time reconstructing context.

### Onboarding New Team Members
```
"Give me an overview of Project X's architecture and component structure."
```
New developers can quickly understand the project structure, key components, and their relationships—dramatically reducing the time needed to become productive on a new codebase.

### Session Recording
```
"End my development session and record what I accomplished."
```
The server guides you through a structured process to document your achievements, task updates, and project status changes, preserving this context for future sessions and team members.

### Architectural Decision Context
```
"Why was GraphQL chosen over REST for the API layer?"
```
The server retrieves the decision entity along with related meetings, developers involved, and the context in which the decision was made—preserving organizational knowledge that would otherwise be lost.

### Dependency Analysis
```
"What would be affected if we modify the authentication service?"
```
Before making changes, developers can understand all components, features, and tasks that depend on a particular component, reducing the risk of unexpected breakages.

### Project Progress Tracking
```
"What's our progress toward the Q2 release milestone?"
```
Project leads can instantly see the status of all tasks and features associated with a milestone, identifying at-risk items before they jeopardize the timeline.

### Status and Priority Management
```
"Show me all high-priority tasks that are still active."
```
Quickly identify the most important work that needs attention, ensuring that critical tasks are addressed first.

### Task Sequencing
```
"What tasks are blocked because they depend on incomplete prerequisite tasks?"
```
Identify and resolve bottlenecks in the development process by understanding the sequential dependencies between tasks.

## Configuration

### Usage with Claude Desktop

Add this to your `claude_desktop_config.json`:

#### Install from GitHub and run with npx

```json
{
  "mcpServers": {
    "developer": {
      "command": "npx",
      "args": [
        "-y",
        "github:tejpalvirk/developer"
      ]
    }
  }
}
```

#### Install globally and run directly

First, install the package globally:

```bash
npm install -g github:tejpalvirk/contextmanager/developer
```

Then configure Claude Desktop:

```json
{
  "mcpServers": {
    "developer": {
      "command": "contextmanager-developer"
    }
  }
}
```

#### docker

```json
{
  "mcpServers": {
    "developer": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "mcp/developer"
      ]
    }
  }
}
```

## Building

### From Source

```bash
# Clone the repository
git clone https://github.com/tejpalvirk/contextmanager.git
cd contextmanager

# Install dependencies
npm install

# Build the server
npm run build

# Run the server
cd developer
node developer_index.js
```

### Docker:

```bash
docker build -t mcp/developer -f developer/Dockerfile .
```

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository. 