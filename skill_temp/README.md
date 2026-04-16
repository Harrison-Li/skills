# Skill Template Boilerplate

This directory provides a standard structure for creating **Gemini CLI Skills**. Skills allow you to extend the agent's capabilities with specialized knowledge, expert workflows, and specific behavioral guidelines.

## 🚀 How to Create a New Skill

1. **Copy this folder**:
   ```bash
   cp -r skill_temp path/to/your-new-skill
   ```
2. **Rename the directory**: Use a descriptive, slug-ified name (e.g., `react-expert` or `aws-devops`).
3. **Fill in `SKILL.md`**:
   - Update the `name` in frontmatter (this is the ID used to activate it).
   - Write a clear `description` so the agent knows *when* to trigger it.
   - Define the Core Principles and Guidelines.
4. **Add Examples**: Use `references/EXAMPLES.md` to show the agent "Good" vs "Bad" code/actions. This is the most effective way to shape behavior.
5. **Add Technical Specs**: Put commands, file paths, and version requirements in `references/technical_reference.md`.

## 📁 Directory Purpose

| File/Folder | Purpose |
| :--- | :--- |
| `SKILL.md` | **The Brain.** Contains the primary instructions and trigger logic. |
| `references/` | **The Library.** Supplemental docs that keep the main `SKILL.md` lean. |
| `agents/` | Model-specific overrides (e.g., system prompt tweaks for specific LLMs). |
| `scripts/` | Helper scripts that the skill might need to execute. |
| `assets/` | Static files, images, or templates used by the skill. |

## 💡 Best Practices

- **Be Surgical**: Instruct the agent to only touch what is necessary.
- **Goal-Driven**: Always require the agent to define success criteria (e.g., "Run `npm test` after the fix").
- **Constraint-First**: Use "Don't" rules to prevent common LLM hallucinations or over-engineering.
- **Links**: Use relative links in `SKILL.md` to point to reference files (e.g., `[Examples](references/EXAMPLES.md)`).
