# Meina Content Studio Skill

This repository contains the `meina-content-studio` custom Skill for the 「美娜的陪跑时刻」 content brand.

The Skill centralizes the brand persona, writing voice, content workflows, platform conventions, NotebookLM prompt guidance, visual direction, and quality checks used to create workplace, HR, AI, organization-management, and career-companion content for Chinese mainland audiences.

## What this Skill supports

Use this Skill when creating or adapting content for:

- Articles, rewrites, outlines, titles, subtitles, introductions, summaries, and keywords.
- Mainland China workplace, HR, AI, organization-management, and system-implementation topics.
- 小红书, 抖音, B站, 微信公众号, WordPress, Facebook, and related publishing copy.
- `HR真相研究所`, `美娜的陪跑时刻`, `职场鬼故事`, `快思慢想自习室`, and management-observation content.
- NotebookLM Podcast Prompts and NotebookLM Video Prompts.
- Cover-image and visual-generation prompts using the Meina brand visual style.
- Simplified Chinese and mainland workplace-language conversion.

## Repository structure

```text
meina-content-studio/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── persona.md
    ├── language-and-writing-style.md
    ├── series-guide.md
    ├── article-workflow.md
    ├── notebooklm-guide.md
    ├── visual-style.md
    ├── platform-output.md
    └── quality-checklist.md
```

## Key files

- `meina-content-studio/SKILL.md` is the control center. It defines trigger behavior, default assumptions, task routing, reference loading, research rules, output control, and final quality requirements.
- `meina-content-studio/agents/openai.yaml` provides UI metadata for the Skill display name, short description, and default prompt.
- `meina-content-studio/references/` contains detailed guidance that should be loaded only when relevant to the user request.

## Validation

Validate the Skill with the Skill Creator validator:

```bash
python /opt/codex/skills/.system/skill-creator/scripts/quick_validate.py meina-content-studio
```

If the environment does not provide `PyYAML`, install it or provide an equivalent local YAML parser shim before running the validator.

## Packaging

The installable archive should be generated locally as `skill.zip` from the repository root:

```bash
python - <<'PY'
from pathlib import Path
import zipfile

root = Path('meina-content-studio')
with zipfile.ZipFile('skill.zip', 'w', zipfile.ZIP_DEFLATED) as archive:
    for path in root.rglob('*'):
        if path.is_file():
            archive.write(path, path.as_posix())
PY
```

`skill.zip` is intentionally ignored by git because it is a binary artifact and cannot be reviewed as a readable diff in pull requests. Keep the source Markdown and YAML files in version control, and regenerate the archive when needed.
