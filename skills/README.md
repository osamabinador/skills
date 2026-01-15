<div align="center">

# Claude Skills Repository

![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)
![Skills Count](https://img.shields.io/badge/Skills-25-green.svg)
![Platform](https://img.shields.io/badge/Platform-Claude%20Code%20%7C%20Codex%20%7C%20GeminiCLI-yellow.svg)

**A comprehensive collection of skills for Claude AI and other AI coding agents. This repository combines skills from Anthropic and Hugging Face, providing a unified resource for specialized AI capabilities.**

[Installation](#installation) • [Available Skills](#available-skills) • [Documentation](#documentation) • [Contributing](#contributing)

</div>

---

## What Are Skills?

Skills are folders of instructions, scripts, and resources that AI agents load dynamically to improve performance on specialized tasks. Skills teach AI agents how to complete specific tasks in a repeatable way, whether that's creating documents with your company's brand guidelines, analyzing data using your organization's specific workflows, or automating personal tasks.

### Key Features

- **Self-Contained**: Each skill is a complete package with instructions, scripts, and resources
- **Portable**: Skills work across multiple AI platforms (Claude, Codex, Gemini)
- **Extensible**: Easy to create, modify, and share custom skills
- **Production-Ready**: Includes skills used by Claude in production environments

### SKILL.md Format

Each skill contains a `SKILL.md` file with YAML frontmatter:

```yaml
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

For more information about the Agent Skills standard, visit [agentskills.io](http://agentskills.io).

---

## Repository Structure

```
skills/
├── .claude-plugin/         # Claude Code plugin configuration
├── .github/                # GitHub workflows and configurations
├── agents/                 # AGENTS.md for OpenAI Codex compatibility
├── apps/                   # Helper applications for skill execution
├── assets/                 # Shared assets used by skills
├── scripts/                # Utility scripts for skill management
├── skills/                 # Individual skill folders (25 skills)
│   ├── anthropic-skills/   # Document processing and utility skills
│   └── huggingface-skills/ # ML and AI workflow skills
├── spec/                   # The Agent Skills specification
└── template/               # Skill template for creating new skills
```

---

## Available Skills

### Anthropic Skills (17 skills)

Document processing and utility skills demonstrating what's possible with Claude's skills system.

| Skill | Description |
|-------|-------------|
| [algorithmic-art](skills/algorithmic-art/) | Create algorithmic art and visual designs using code |
| [brand-guidelines](skills/brand-guidelines/) | Apply consistent brand guidelines to documents and communications |
| [canvas-design](skills/canvas-design/) | Design visual canvases and graphics |
| [doc-coauthoring](skills/doc-coauthoring/) | Collaborate on document creation and editing |
| [docx](skills/docx/) | Create and edit Word documents |
| [frontend-design](skills/frontend-design/) | Design and implement frontend user interfaces |
| [internal-comms](skills/internal-comms/) | Create internal communications following organizational standards |
| [mcp-builder](skills/mcp-builder/) | Build Model Context Protocol servers |
| [pdf](skills/pdf/) | Create and edit PDF documents |
| [pptx](skills/pptx/) | Create and edit PowerPoint presentations |
| [skill-creator](skills/skill-creator/) | Create new skills following best practices |
| [slack-gif-creator](skills/slack-gif-creator/) | Create animated GIFs for Slack and other platforms |
| [theme-factory](skills/theme-factory/) | Create consistent themes across documents and designs |
| [web-artifacts-builder](skills/web-artifacts-builder/) | Build web-based artifacts and applications |
| [webapp-testing](skills/webapp-testing/) | Test web applications comprehensively |
| [xlsx](skills/xlsx/) | Create and edit Excel spreadsheets |

### Hugging Face Skills (8 skills)

Specialized capabilities for AI/ML tasks including dataset creation, model training, and evaluation.

| Skill | Description |
|-------|-------------|
| [hf-hugging-face-cli](skills/hf-hugging-face-cli/) | Execute Hugging Face Hub operations using the hf CLI. Download models/datasets, upload files, manage repos, and run cloud compute jobs |
| [hf-hugging-face-datasets](skills/hf-hugging-face-datasets/) | Create and manage datasets on Hugging Face Hub. Supports initializing repos, defining configs/system prompts, streaming row updates, and SQL-based dataset querying/transformation |
| [hf-hugging-face-evaluation](skills/hf-hugging-face-evaluation/) | Add and manage evaluation results in Hugging Face model cards. Supports extracting eval tables from README content, importing scores from Artificial Analysis API, and running custom evaluations |
| [hf-hugging-face-jobs](skills/hf-hugging-face-jobs/) | Run compute jobs on Hugging Face infrastructure. Execute Python scripts, manage scheduled jobs, and monitor job status |
| [hf-hugging-face-model-trainer](skills/hf-hugging-face-model-trainer/) | Train or fine-tune language models using TRL on Hugging Face Jobs infrastructure. Covers SFT, DPO, GRPO and reward modeling training methods, plus GGUF conversion for local deployment |
| [hf-hugging-face-paper-publisher](skills/hf-hugging-face-paper-publisher/) | Publish and manage research papers on Hugging Face Hub. Supports creating paper pages, linking papers to models/datasets, claiming authorship, and generating professional markdown-based research articles |
| [hf-hugging-face-tool-builder](skills/hf-hugging-face-tool-builder/) | Build reusable scripts for Hugging Face API operations. Useful for chaining API calls or automating repeated tasks |
| [hf-hugging-face-trackio](skills/hf-hugging-face-trackio/) | Track and visualize ML training experiments with Trackio. Log metrics via Python API and retrieve them via CLI. Supports real-time dashboards synced to HF Spaces |

---

## Installation

### Claude Code

Register this repository as a plugin marketplace:

```bash
/plugin marketplace add osamabinador/skills
```

Then install specific skills or skill bundles:

```bash
# Install individual skill
/plugin install docx@osamabinador/skills

# Install Hugging Face skills bundle
/plugin install huggingface-skills@osamabinador/skills

# Install document processing bundle
/plugin install document-skills@osamabinador/skills

# Install example skills bundle
/plugin install example-skills@osamabinador/skills
```

### Claude.ai

These skills are available to paid plans in Claude.ai. To use any skill from this repository or upload custom skills, follow the instructions in [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude#h_a4222fa77b).

### Claude API

You can use these skills via the Claude API. See the [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill) for more information.

### OpenAI Codex

Codex will identify skills via the `AGENTS.md` file:

```bash
codex --ask-for-approval never "Summarize the current instructions."
```

For more details, see the [Codex AGENTS guide](https://developers.openai.com/codex/guides/agents-md).

### Google Gemini CLI

Install as a Gemini CLI extension:

```bash
# Install from local directory
gemini extensions install . --consent

# Install directly from GitHub
gemini extensions install https://github.com/osamabinador/skills.git --consent
```

See [Gemini CLI extensions docs](https://geminicli.com/docs/extensions/#installing-an-extension) for more help.

---

## Using Skills

Once a skill is installed, simply mention it when giving your AI agent instructions:

### Document Processing Examples

```markdown
"Use the PDF skill to extract the form fields from `path/to/some-file.pdf`"
"Use the Docx skill to create a professional resume following brand guidelines"
"Use the Xlsx skill to analyze this spreadsheet and create a summary report"
"Use the PPTX skill to create a presentation with our company template"
```

### Hugging Face ML Examples

```markdown
"Use the HF model trainer skill to estimate the GPU memory needed for a 70B model run"
"Use the HF dataset creator skill to draft new few-shot classification templates"
"Use the HF evaluation skill to run benchmarks on our fine-tuned model checkpoint"
"Use the HF paper publisher skill to index my arXiv paper and link it to my model"
"Use the HF jobs skill to schedule a training job on Hugging Face infrastructure"
```

Your AI agent automatically loads the corresponding `SKILL.md` instructions and helper scripts while completing the task.

---

## Creating a New Skill

Skills are simple to create and customize. Follow these steps to add a new skill to the repository.

### Step 1: Use the Template

Copy the template folder as a starting point:

```bash
cp -r template skills/my-new-skill
```

### Step 2: Update SKILL.md

Edit the `SKILL.md` file in your new skill folder:

```yaml
---
name: my-new-skill
description: A clear description of what this skill does and when to use it
---

# My New Skill

## Overview
[Describe what this skill does]

## When to Use
[Explain when this skill should be activated]

## How It Works
[Detail the process or workflow]

## Examples
- Example 1: [Description]
- Example 2: [Description]

## Guidelines
- Guideline 1
- Guideline 2
```

### Step 3: Add Supporting Files

Add any necessary scripts, templates, or assets to the skill folder:

```
skills/my-new-skill/
├── SKILL.md           # Main skill definition
├── script.py          # Optional helper script
├── template.md        # Optional template
└── assets/            # Optional assets directory
```

### Step 4: Update Marketplace Configuration

Add your skill to `.claude-plugin/marketplace.json`:

```json
{
  "name": "my-new-skill-bundle",
  "description": "Description for marketplace",
  "source": "./",
  "strict": false,
  "skills": [
    "./skills/my-new-skill"
  ]
}
```

### Step 5: Test Your Skill

Test the skill with various AI agents to ensure it works as expected before contributing.

---

## Skill Categories

### Document Processing Skills

Skills for creating and editing documents across different formats:

- **docx** - Word document creation and editing
- **pdf** - PDF document manipulation
- **pptx** - PowerPoint presentation creation
- **xlsx** - Excel spreadsheet operations
- **doc-coauthoring** - Collaborative document editing

### Creative & Design Skills

Skills for visual design and creative tasks:

- **algorithmic-art** - Code-generated art and visuals
- **canvas-design** - Canvas-based design work
- **frontend-design** - Frontend UI/UX design
- **theme-factory** - Design system theming
- **slack-gif-creator** - Animated GIF creation

### Development & Technical Skills

Skills for software development and technical tasks:

- **mcp-builder** - Model Context Protocol server development
- **skill-creator** - Skill development methodology
- **web-artifacts-builder** - Web application building
- **webapp-testing** - Comprehensive web testing

### Enterprise & Communication Skills

Skills for business communications:

- **brand-guidelines** - Brand consistency enforcement
- **internal-comms** - Internal communication templates

### Hugging Face ML Skills

Specialized skills for machine learning workflows:

- **hf-hugging-face-cli** - Hub CLI operations
- **hf-hugging-face-datasets** - Dataset management
- **hf-hugging-face-evaluation** - Model evaluation
- **hf-hugging-face-jobs** - Compute job management
- **hf-hugging-face-model-trainer** - Model training and fine-tuning
- **hf-hugging-face-paper-publisher** - Research paper publishing
- **hf-hugging-face-tool-builder** - Custom tool development
- **hf-hugging-face-trackio** - Experiment tracking

---

## Supporting Files

### AGENTS.md

The `agents/AGENTS.md` file provides instructions compatible with OpenAI Codex, allowing the same skill definitions to work across multiple AI coding platforms.

### Helper Applications

The `apps/` directory contains helper applications used by various skills for specialized tasks.

### Shared Assets

The `assets/` directory contains shared resources used across multiple skills, ensuring consistency and reducing duplication.

### Utility Scripts

The `scripts/` directory contains utility scripts for:

- Generating skill documentation
- Validating skill structure
- Managing skill dependencies
- Automating common tasks

---

## Documentation & References

### Official Documentation

- [What are skills?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Using skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Agent Skills Specification](https://agentskills.io/home)

### Engineering Resources

- [Equipping agents for the real world with Agent Skills](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill)
- [Codex AGENTS guide](https://developers.openai.com/codex/guides/agents-md)
- [Gemini CLI extensions docs](https://geminicli.com/docs/extensions/#installing-an-extension)

---

## License

This repository is licensed under the Apache License, Version 2.0. See the [LICENSE](LICENSE) file for details.

### Individual Skills

- Many skills in this repository are available under the Apache 2.0 license
- Document creation and editing skills (docx, pdf, pptx, xlsx) are source-available but not open source
- Individual skill folders may contain their own LICENSE files

See individual skill directories for specific licensing terms.

---

## Contributing

Contributions are welcome! To contribute a new skill or improvement:

### Getting Started

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-skill`)
3. Commit your changes (`git commit -m 'Add amazing new skill'`)
4. Push to the branch (`git push origin feature/amazing-skill`)
5. Open a Pull Request

### Contribution Guidelines

- Follow the existing skill structure and format
- Include comprehensive documentation in SKILL.md
- Test your skill with multiple AI agents
- Add your skill to the marketplace configuration
- Ensure code quality and consistency

### Reporting Issues

For bugs or feature requests, please open an issue with:
- Clear description of the problem or feature
- Steps to reproduce (for bugs)
- Expected behavior vs actual behavior
- Relevant skill and platform information

---

## Support

### Getting Help

- **Documentation**: Check the individual skill SKILL.md files
- **Issues**: Open an issue for bugs or questions
- **Discussions**: Use GitHub Discussions for general questions

### Common Questions

**Q: How do I install a specific skill?**
A: Use `/plugin install <skill-name>@osamabinador/skills` in Claude Code.

**Q: Can I use these skills with other AI agents?**
A: Yes! Skills work with Claude Code, Codex, and Gemini CLI (with varying compatibility).

**Q: How do I create a custom skill?**
A: Copy the template folder and customize the SKILL.md file following our guide.

**Q: Are these skills production-ready?**
A: Many skills are used by Claude in production. However, always test custom skills in your environment.

---

## Acknowledgments

- [Anthropic](https://www.anthropic.com) for the original skills repository
- [Hugging Face](https://huggingface.co) for ML workflow skills
- [Agent Skills](https://agentskills.io) for the standardized skills specification
- All contributors who help improve this collection

---

<div align="center">

**Made with care by [osamabinador](https://github.com/osamabinador)**

⭐ Star this repository if you find it useful!

</div>
