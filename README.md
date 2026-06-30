# 🌍 Claude Skills: East Africa AI Stack

Claude skills repository for Kenya/East Africa contexts — prompts, tools, and skill definitions tuned for Kenyan civic, financial, and agricultural use cases.

Inspired by Rundown AI guide: *"Make Claude an Expert at Anything with This Skills Repo"* (January 2026).

These skills make Claude Code an expert at East African AI contexts — Swahili NLP, M-PESA Daraja, Kenya civic law, and the full East Africa AI stack architecture.

## Usage with Claude Code

```bash
# Load a skill in your Claude Code session
/load https://raw.githubusercontent.com/gabrielmahia/claude-east-africa-skills/main/skills/mpesa-daraja/SKILL.md

# Or reference in your CLAUDE.md
cat skills/mpesa-daraja/SKILL.md >> CLAUDE.md
```

## Available Skills

| Skill | File | Makes Claude expert at |
|-------|------|------------------------|
| Swahili Language | `skills/swahili-language/SKILL.md` | Swahili NLP, grammar, domain vocab, common AI errors |
| M-PESA Daraja API | `skills/mpesa-daraja/SKILL.md` | All 22 Daraja endpoints, auth, phone normalization, errors |
| Kenya Civic Data | `skills/kenya-civic-data/SKILL.md` | Constitution, 47 counties, civic-agent-kit, data sources |
| East Africa Stack | `skills/east-africa-stack/SKILL.md` | Full stack architecture, when to use each layer |

## Research Basis
- arXiv:2509.04516 — Swahili AI accuracy gap (4× error rate)
- Safaricom Daraja API documentation
- Constitution of Kenya 2010
- Kenya National Bureau of Statistics

## Related Tools
- [mpesa-mcp](https://github.com/gabrielmahia/mpesa-mcp) — M-PESA MCP server
- [civic-agent-kit](https://github.com/gabrielmahia/civic-agent-kit) — Kenya civic data MCP
- [wapimaji-mcp](https://github.com/gabrielmahia/wapimaji-mcp) — Water/drought MCP
- [swahili-civic-nlp](https://huggingface.co/datasets/gmahia/swahili-civic-nlp) — Swahili NLP dataset

---
*© 2026 Gabriel Mahia / AI Kung Fu LLC · MIT License*
