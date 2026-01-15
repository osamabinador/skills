# Claude Skills Repository

A comprehensive collection of skills for Claude AI and other AI coding agents. This repository combines skills from Anthropic and Hugging Face, providing a unified resource for specialized AI capabilities.

## What Are Skills?

Skills are folders of instructions, scripts, and resources that AI agents load dynamically to improve performance on specialized tasks. Skills teach AI agents how to complete specific tasks in a repeatable way, whether that's creating documents with your company's brand guidelines, analyzing data using your organization's specific workflows, or automating personal tasks.

Each skill is self-contained in its own folder with a `SKILL.md` file containing YAML frontmatter and instructions. The frontmatter requires only two fields:
- `name` - A unique identifier for your skill (lowercase, hyphens for spaces)
- `description` - A complete description of what the skill does and when to use it

The markdown content below contains the instructions, examples, and guidelines that the AI agent follows when the skill is active.

For more information about the Agent Skills standard, see [agentskills.io](http://agentskills.io).

## Repository Structure

This repository is organized into the following main directories:

- **skills/** - Individual skill folders for various tasks
- **spec/** - The Agent Skills specification
- **template/** - Skill template for creating new skills
- **agents/** - AGENTS.md file for OpenAI Codex compatibility
- **apps/** - Helper applications for skill execution
- **assets/** - Shared assets used by skills
- **scripts/** - Utility scripts for skill management
- **.claude-plugin/** - Claude Code plugin configuration

## Available Skills

### Anthropic Skills (Original)

These skills demonstrate what's possible with Claude's skills system, ranging from creative applications to technical tasks and enterprise workflows.

| Skill Name | Description |
|------------|-------------|
| algorithmic-art | Create algorithmic art and visual designs using code |
| brand-guidelines | Apply consistent brand guidelines to documents and communications |
| canvas-design | Design visual canvases and graphics |
| doc-coauthoring | Collaborate on document creation and editing |
| docx | Create and edit Word documents |
| frontend-design | Design and implement frontend user interfaces |
| internal-comms | Create internal communications following organizational standards |
| mcp-builder | Build Model Context Protocol servers |
| pdf | Create and edit PDF documents |
| pptx | Create and edit PowerPoint presentations |
| skill-creator | Create new skills following best practices |
| slack-gif-creator | Create animated GIFs for Slack and other platforms |
| theme-factory | Create consistent themes across documents and designs |
| web-artifacts-builder | Build web-based artifacts and applications |
| webapp-testing | Test web applications comprehensively |
| xlsx | Create and edit Excel spreadsheets |

### Hugging Face Skills

These skills provide specialized capabilities for AI/ML tasks including dataset creation, model training, and evaluation. They are interoperable with all major coding agent tools.

| Skill Name | Description |
|------------|-------------|
| hf-hugging-face-cli | Execute Hugging Face Hub operations using the hf CLI. Download models/datasets, upload files, manage repos, and run cloud compute jobs |
| hf-hugging-face-datasets | Create and manage datasets on Hugging Face Hub. Supports initializing repos, defining configs/system prompts, streaming row updates, and SQL-based dataset querying/transformation |
| hf-hugging-face-evaluation | Add and manage evaluation results in Hugging Face model cards. Supports extracting eval tables from README content, importing scores from Artificial Analysis API, and running custom evaluations |
| hf-hugging-face-jobs | Run compute jobs on Hugging Face infrastructure. Execute Python scripts, manage scheduled jobs, and monitor job status |
| hf-hugging-face-model-trainer | Train or fine-tune language models using TRL on Hugging Face Jobs infrastructure. Covers SFT, DPO, GRPO and reward modeling training methods |
| hf-hugging-face-paper-publisher | Publish and manage research papers on Hugging Face Hub. Supports creating paper pages, linking papers to models/datasets, and generating professional markdown-based research articles |
| hf-hugging-face-tool-builder | Build reusable scripts for Hugging Face API operations. Useful for chaining API calls or automating repeated tasks |
| hf-hugging-face-trackio | Track and visualize ML training experiments with Trackio. Log metrics via Python API and retrieve them via CLI. Supports real-time dashboards synced to HF Spaces |

## Installation

### Claude Code

Register this repository as a plugin marketplace:

```
/plugin marketplace add osamabinador/skills
```

Then install specific skills:

```
/plugin install <skill-name>@osamabinador/skills
```

For example:

```
/plugin install docx@osamabinador/skills
/plugin install hf-hugging-face-model-trainer@osamabinador/skills
```

### Claude.ai

These skills are available to paid plans in Claude.ai. To use any skill from this repository or upload custom skills, follow the instructions in [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude#h_a4222fa77b).

### Claude API

You can use these skills via the Claude API. See the [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill) for more information.

### OpenAI Codex

Codex will identify skills via the `AGENTS.md` file. You can verify instructions are loaded with:

```
codex --ask-for-approval never "Summarize the current instructions."
```

### Google Gemini CLI

This repo includes `gemini-extension.json` for Gemini CLI integration:

```
gemini extensions install . --consent
```

or use the GitHub URL:

```
gemini extensions install https://github.com/osamabinador/skills.git --consent
```

## Using Skills

Once a skill is installed, mention it directly while giving your AI agent instructions:

- "Use the PDF skill to extract the form fields from `path/to/some-file.pdf`"
- "Use the Docx skill to create a professional resume following brand guidelines"
- "Use the HF model trainer skill to estimate the GPU memory needed for a 70B model run"
- "Use the HF dataset creator skill to draft new few-shot classification templates"
- "Use the HF paper publisher skill to index my arXiv paper and link it to my model"

Your AI agent automatically loads the corresponding `SKILL.md` instructions and helper scripts while completing the task.

## Creating a New Skill

Skills are simple to create. Each skill is a folder containing:

1. **SKILL.md** - The main skill definition file
2. Any supporting files (scripts, templates, assets)

### SKILL.md Format

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it
---

# My Skill Name

[Add your instructions here that the AI agent will follow when this skill is active]

## Examples
- Example usage 1
- Example usage 2

## Guidelines
- Guideline 1
- Guideline 2
```

### Using the Template

This repository includes a template skill in the `template/` directory that you can copy and customize:

1. Copy the template folder to a new name
2. Update the `SKILL.md` frontmatter with your skill's name and description
3. Add your custom instructions, examples, and guidelines
4. Add any supporting scripts or assets
5. Update the marketplace configuration if you want to distribute the skill

## Marketplace Configuration

The `.claude-plugin/marketplace.json` file lists skills with human-readable descriptions for the plugin marketplace. The CI validates that skill names and paths match between `SKILL.md` files and `marketplace.json`, but descriptions are maintained separately: `SKILL.md` descriptions guide when to activate the skill, while marketplace descriptions are written for humans browsing available skills.

## Supporting Files

### Agents

The `agents/AGENTS.md` file provides instructions compatible with OpenAI Codex. This allows the same skill definitions to work across multiple AI coding platforms.

### Applications

The `apps/` directory contains helper applications used by various skills for specialized tasks.

### Assets

The `assets/` directory contains shared resources used across multiple skills, ensuring consistency and reducing duplication.

### Scripts

The `scripts/` directory contains utility scripts for:
- Generating skill documentation
- Validating skill structure
- Managing skill dependencies
- Automating common tasks

## Documentation References

- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Equipping agents for the real world with Agent Skills](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- [Agent Skills Specification](https://agentskills.io/home)
- [Codex AGENTS guide](https://developers.openai.com/codex/guides/agents-md)
- [Gemini CLI extensions docs](https://geminicli.com/docs/extensions/#installing-an-extension)

## License

This repository contains skills with different licensing terms:

- Skills in this repository follow the Agent Skills standard and are provided for demonstration and educational purposes
- Many skills are available under the Apache 2.0 license
- Document creation and editing skills (docx, pdf, pptx, xlsx) are source-available but not open source
- Individual skill folders may contain their own LICENSE files

See individual skill directories for specific licensing terms.

## Contributing

Contributions are welcome! To contribute a new skill:

1. Copy an existing skill folder as a template
2. Customize the SKILL.md with your skill's name, description, and instructions
3. Add any supporting scripts, templates, or assets
4. Test your skill with various AI agents
5. Submit a pull request with a clear description of your skill's purpose and capabilities

## Disclaimer

**These skills are provided for demonstration and educational purposes only.** While some of these capabilities may be available in Claude and other AI agents, the implementations and behaviors you receive may differ from what is shown in these skills. These skills are meant to illustrate patterns and possibilities. Always test skills thoroughly in your own environment before relying on them for critical tasks.
