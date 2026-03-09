# ocbot_skills

Community skills for [ocbot](https://github.com/instry/ocbot). Each skill is a folder containing a `SKILL.md` file with YAML frontmatter and instructions, following the [Agent Skills](http://agentskills.io) standard.

## Structure

```
skills/
  amazon-order-export/
    SKILL.md
  github-pr-review/
    SKILL.md
  linkedin-auto-connect/
    SKILL.md
```

## Creating a Skill

Create a folder under `skills/` with a `SKILL.md`:

```markdown
---
name: my-skill-name
description: A clear description of what this skill does and when to use it
---

# My Skill Name

[Instructions for the agent to follow]
```

See [How to create custom skills](https://support.claude.com/en/articles/12512198-creating-custom-skills) for details.
