#  BlogCrew - Agentic AI Blog Writing with CrewAI

BlogCrew is a Python project that leverages Agentic AI using CrewAI to automate the process of researching and writing blog posts. It orchestrates multiple AI agents with specific roles and tasks, allowing them to collaborate and produce high-quality content on a given topic.

BlogCrew is built on top of CrewAI, a framework for creating agentic workflows. CrewAI allows to define agents, tasks, and tools in a structured way so that multiple AI agents can work together to achieve a goal.

---
In this project, two main AI agents are defined:

Researcher Agent - Collects recent and relevant facts about a given topic.

Writer Agent - Produces a concise, engaging blog summary using the research.

The workflow is configurable via YAML files and can be easily extended to include new agents, tasks, or tools.

### Features

Automated research and content creation workflow.

Multi-agent collaboration using CrewAI.

Configurable agents and tasks through YAML files.

Integration with external tools like SerperDevTool for search and ScrapeWebsiteTool for web scraping.

Verbose logging to monitor agent actions.

Fully extensible for new AI tasks or workflows.


## Configuration

BlogCrew uses YAML files to define agents and tasks.

### Agents Configuration (`config/agents.yaml`)

Defines the AI agents, their LLM models, roles, goals, and backstories.

Example:

```yaml
research_agent:
  llm: gemini/gemini-2.0-flash
  role: Research Specialist
  goal: Research interesting facts about the topic: {topic}
  backstory: You are an expert at finding relevant and factual data

writer_agent:
  llm: gemini/gemini-2.0-flash
  role: Creative Writer
  goal: Write a short blog summary using the research
  backstory: You are skilled at writing engaging summaries based on provided content.
```

---

### Tasks Configuration (`config/tasks.yaml`)

Defines tasks for each agent, including descriptions and expected outputs.

Example:

```yaml
research_task:
  description: Find 3-5 interesting and recent facts about {topic} as of year 2025.
  expected_output: A bullet list of 3-5 facts

blog_task:
  description: Write a 100-word blog post summary about {topic} using the facts from the research.
  expected_output: A blog post summary
```

---

## Agents

* **Researcher Agent** – Uses tools like `SerperDevTool` to gather accurate information.
* **Writer Agent** - Converts the research into a concise and readable blog post.

Each agent is configurable via `agents.yaml` and can have multiple tools attached to enhance capabilities.

---

## Tasks

* **Research Task** – Assigned to the Researcher Agent to gather facts.
* **Blog Task** – Assigned to the Writer Agent to write the blog summary.

Tasks are defined in `tasks.yaml` and describe what output is expected from each agent.

---

## Usage

1. Run the main script:

```bash
python blog_crew.py
```

2. Provide input when kicking off the workflow:

```python
blog_crew.crew().kickoff(inputs={"topic": "The future of electrical vehicles"})
```

3. Workflow steps:

* The Researcher Agent collects 3-5 interesting facts about the topic.
* The Writer Agent generates a blog summary using the research results.

---
## Output:

<img width="2864" height="1670" alt="image" src="https://github.com/user-attachments/assets/050a0891-4be3-4900-ae31-a109ca451102" />

<img width="2840" height="1314" alt="image" src="https://github.com/user-attachments/assets/b6a256e2-0572-4fce-ac0d-6cb857630d02" />

<img width="2814" height="1392" alt="image" src="https://github.com/user-attachments/assets/e1708227-02df-4518-8a2b-d7b8fc46d65f" />


