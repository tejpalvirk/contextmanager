# Student MCP Server

An MCP server implementation that provides tools for managing student knowledge graphs, enabling structured representation of courses, assignments, exams, concepts, and study resources. This server helps students track their academic progress, manage deadlines, and optimize their learning journey.

## Features

- **Persistent Educational Context**: Maintain a structured knowledge graph of educational entities and relationships across multiple sessions
- **Study Session Management**: Track study sessions with unique IDs and record progress over time
- **Course Management**: Organize courses, lectures, assignments, and exams in a structured format
- **Concept Mapping**: Connect learning concepts to show relationships and prerequisites
- **Assignment Tracking**: Monitor assignment status, due dates, and related resources
- **Exam Preparation**: Track exam dates and organize study materials
- **Deadline Management**: Keep track of upcoming due dates for assignments and exams
- **Resource Organization**: Connect learning resources to specific courses and concepts
- **Progress Monitoring**: Track completion status of courses, assignments, and exams
- **Knowledge Connections**: Visualize relationships between different educational concepts

## Entities

The Student MCP Server recognizes the following entity types:

- **course**: Academic courses being taken
- **assignment**: Homework, projects, and other submitted work
- **exam**: Tests, quizzes, and other assessments
- **concept**: Knowledge topics and learning objectives
- **resource**: Textbooks, articles, videos, and other learning materials
- **note**: Personal study notes and observations
- **lecture**: Individual class sessions
- **project**: Larger educational projects or undertakings
- **question**: Specific questions for study or review
- **term**: Academic terms or semesters
- **goal**: Learning objectives and targets
- **professor**: Course instructors and teachers
- **status**: Entity status values (active, completed, pending, abandoned)
- **priority**: Priority level values (high, low)

## Relationships

Entities can be connected through the following relationship types:

- **enrolled_in**: Student is taking a course
- **assigned_in**: Assignment is part of a course
- **due_on**: Assignment/exam has specific due date
- **covers**: Lecture/resource covers concept
- **references**: Note references concept
- **prerequisite_for**: Concept is foundation for another
- **taught_by**: Course taught by professor
- **scheduled_for**: Lecture/exam scheduled for specific time
- **contains**: Course contains lectures/assignments
- **requires**: Assignment requires specific concepts
- **related_to**: Concept related to another concept
- **created_for**: Note created for specific lecture
- **studies**: Study session focuses on concept/exam
- **helps_with**: Resource helps with assignment/concept
- **submitted**: Assignment submitted on date
- **part_of**: Entity is part of another entity
- **included_in**: Included in a larger component
- **follows**: Entity follows another in sequence
- **attends**: Student attends lecture
- **graded_with**: Assignment/exam graded with specific criteria
- **has_status**: Links entities to their current status (active, completed, pending, abandoned)
- **has_priority**: Links entities to their priority level (high, low)
- **precedes**: Indicates that one task or assignment comes before another in a sequence

## Status and Priority Management

The Student MCP Server provides comprehensive status and priority tracking capabilities:

- **Status Values**: 
  - **active**: Currently being worked on or studied
  - **completed**: Finished or successfully submitted
  - **pending**: Not yet started but planned
  - **abandoned**: No longer being pursued

- **Priority Values**:
  - **high**: Requires immediate attention or has significant impact on grades
  - **low**: Can be addressed after higher priority items are complete

- **Sequential Learning Management**:
  - Define which assignments or concepts must be completed before others
  - Organize study activities in a logical progression
  - Create dependencies between related learning tasks
  - Build structured learning paths through course material

## Available Tools

The Student MCP Server provides these tools for interacting with educational knowledge:

### startsession
Starts a new study session, generating a unique session ID and displaying current courses, upcoming deadlines, recently studied concepts, and past study sessions. Shows status information via has_status relations, priority levels via has_priority relations, and identifies assignments ready to be worked on next based on sequential dependencies.

### loadcontext
Loads detailed context for a specific entity (course, assignment, etc.), displaying relevant information based on entity type. Includes status information, priority levels, and sequential relationships between related entities.

### endsession
Records the results of a study session through a structured, multi-stage process:
1. **summary**: Records session summary, duration, and course focus
2. **conceptsLearned**: Documents concepts studied during the session
3. **assignmentUpdates**: Tracks updates to assignments
4. **statusUpdates**: Records changes to entity status values
5. **courseStatus**: Updates overall course status, priority assignments, and sequential relationships
6. **newConcepts**: Records new concepts learned during the session
7. **assembly**: Final assembly of all session data

### buildcontext
Creates new entities, relations, or observations in the knowledge graph:
- **entities**: Add new educational entities (courses, assignments, concepts, status, priority, etc.)
- **relations**: Create relationships between entities (including has_status, has_priority, precedes)
- **observations**: Add observations to existing entities

### deletecontext
Removes entities, relations, or observations from the knowledge graph:
- **entities**: Remove educational entities
- **relations**: Remove relationships between entities (including status, priority, and sequential relations)
- **observations**: Remove specific observations from entities

### advancedcontext
Retrieves information from the knowledge graph:
- **graph**: Get the entire knowledge graph
- **search**: Search for nodes based on query criteria
- **nodes**: Get specific nodes by name
- **course**: Get details about a specific course
- **deadlines**: Get upcoming deadlines
- **assignment**: Get details about a specific assignment
- **exam**: Get details about a specific exam
- **concepts**: Get information about concepts
- **lecture**: Get information about lectures
- **term**: Get details about an academic term
- **status**: Find entities with a specific status value
- **priority**: Find entities with a specific priority value
- **sequence**: Identify sequential relationships for learning activities

## Domain-Specific Functions

The Student MCP Server includes specialized domain functions for education:

- **getCourseOverview**: Comprehensive view of a course including lectures, assignments, exams, and resources
- **getUpcomingDeadlines**: Find assignments and exams with approaching due dates
- **getAssignmentStatus**: Get detailed status of assignments, including progress and related concepts
- **getExamPrep**: Get exam preparation materials and related concepts
- **findRelatedConcepts**: Discover connections between different educational concepts
- **getStudyProgress**: Track study progress across courses
- **getTermOverview**: Get overview of courses and work for an academic term
- **getConceptMastery**: Assess level of understanding for specific concepts
- **getStatusOverview**: View all entities with a specific status (active, completed, pending, abandoned)
- **getPriorityItems**: Identify high-priority assignments and study tasks
- **getLearningSequence**: Visualize the sequence of learning activities based on precedes relations

## Example Prompts

### Starting a Session
```
Let's start a new study session for my Computer Science course.
```

### Loading Course Context
```
Load the context for my Calculus 101 course so I can see upcoming assignments and exams.
```

### Recording Study Progress
```
I've just finished studying for 2 hours on Calculus 101. I focused on limits and derivatives, completed my homework assignment on basic differentiation, and took notes on the chain rule. I've marked the limits content as completed and set the derivatives practice as high priority. I'm feeling more confident about the upcoming exam next week.
```

### Managing Learning Materials
```
Create a new concept called "Binary Trees" related to my Data Structures course with the description "A binary tree is a tree data structure in which each node has at most two children." Set its status to active and make it precede the "Graph Algorithms" concept.
```

```
Update the status of my "Database Assignment" to "completed" and add that I successfully implemented all required queries. Mark the "Advanced SQL" concept as high priority for my next study session.
```

## Usage

This MCP server enables students to:

- **Maintain Study Continuity**: Keep track of what you've learned across multiple study sessions
- **Optimize Learning Time**: Focus on high-priority assignments and concepts
- **Track Academic Progress**: Monitor completion of courses, assignments, and mastery of concepts
- **Prepare for Exams**: Organize study materials and track progress towards exam readiness
- **Manage Deadlines**: Stay on top of upcoming due dates for assignments and exams
- **Connect Knowledge**: See relationships between different concepts across courses
- **Prioritize Work**: Focus on high-priority assignments and learning tasks
- **Structure Learning**: Create logical sequences for learning related concepts
- **Track Status**: Monitor the status of assignments, projects, and learning activities

## Configuration

### Usage with Claude Desktop

Add this to your `claude_desktop_config.json`:

#### Install from GitHub and run with npx

```json
{
  "mcpServers": {
    "student": {
      "command": "npx",
      "args": [
        "-y",
        "github:tejpalvirk/student"
      ]
    }
  }
}
```

#### Install globally and run directly

First, install the package globally:

```bash
npm install -g github:tejpalvirk/student
```

Then configure Claude Desktop:

```json
{
  "mcpServers": {
    "student": {
      "command": "contextmanager-student"
    }
  }
}
```

#### docker

```json
{
  "mcpServers": {
    "student": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "mcp/student"
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
cd student
node student_index.js
```

### Docker:

```bash
docker build -t mcp/student -f student/Dockerfile .
```

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository.

## Environment Variables

The Student MCP Server supports the following environment variables to customize where data is stored:

- **MEMORY_FILE_PATH**: Path where the knowledge graph data will be stored
  - Can be absolute or relative (relative paths use current working directory)
  - Default: `./student/memory.json`

- **SESSIONS_FILE_PATH**: Path where session data will be stored
  - Can be absolute or relative (relative paths use current working directory)
  - Default: `./student/sessions.json`

Example usage:

```bash
# Store data in the current directory
MEMORY_FILE_PATH="./student-memory.json" SESSIONS_FILE_PATH="./student-sessions.json" npx github:tejpalvirk/contextmanager-student

# Store data in a specific location (absolute path)
MEMORY_FILE_PATH="/path/to/data/student-memory.json" npx github:tejpalvirk/contextmanager-student

# Store data in user's home directory
MEMORY_FILE_PATH="$HOME/contextmanager/student-memory.json" npx github:tejpalvirk/contextmanager-student
``` 