# Skill: Kenya Civic Data Expert

## Purpose
Makes Claude an expert at Kenya's constitutional framework, county system,
government data sources, and civic AI tools.

## Load this skill when:
- Building civic AI tools for Kenya
- Working with kenya-legal-rag, civic-agent-kit, haki-debate-ai
- Processing Kenyan legal/government documents
- Answering questions about Kenyan rights, laws, counties

---

## Constitutional Framework

**The Constitution of Kenya 2010** is the supreme law.
Key chapters for civic AI:
- Chapter 4 (Bill of Rights): Articles 19-57 — fundamental rights
- Chapter 11 (Devolution): County government system
- Chapter 12 (Public Finance): Budget, taxation
- Article 35: Access to information (a right, not a privilege)
- Article 33: Freedom of expression
- Article 40: Right to property (inc. land)
- Article 41: Right to fair labour
- Article 43: Economic and social rights (health, food, water, housing, education)
- Article 47: Fair administrative action

**Key principle:** The Bill of Rights applies to all persons in Kenya,
not just citizens. Relevant for refugee tools.

---

## County System (47 Counties)

**Devolution:** Kenya has 47 counties with elected governors and MCAs.
Each county has a County Assembly and County Executive.

**Key counties by population:**
1. Nairobi (4.9M) — capital, highest economic output
2. Kiambu (2.4M) — central, tech hub (Silicon Savannah)
3. Nakuru (2.2M) — Rift Valley economic center
4. Kakamega (2.0M) — Western, agricultural
5. Bungoma (1.7M) — Western
...down to Lamu (0.2M) — smallest

**ASAL counties** (Arid and Semi-Arid Lands — priority for development):
Turkana, Marsabit, Mandera, Wajir, Garissa, Isiolo, Samburu,
West Pokot, Tana River, Kilifi (parts), Kwale (parts)

---

## Key Government Data Sources

| Source | URL | What |
|--------|-----|------|
| KNBS | knbs.or.ke | Kenya National Bureau of Statistics |
| NDMA | ndma.go.ke | National Drought Management Authority |
| CBK | centralbank.go.ke | Central Bank of Kenya |
| Kenya Parliament | parliament.go.ke | Bills, Hansard, committees |
| Controller of Budget | cob.go.ke | Budget implementation reports |
| SASRA | sasra.go.ke | SACCO Societies Regulatory Authority |
| KALRO | kalro.org | Kenya Agricultural and Livestock Research |
| KPLC | kplc.co.ke | Kenya Power (electricity) |
| NLC | nlc.go.ke | National Land Commission |

---

## civic-agent-kit Tools

**Install:** pip install civic-agent-kit
**GitHub:** https://github.com/gabrielmahia/civic-agent-kit
**MCP server:** Start with `civic-agent-kit`

| Tool | What it returns |
|------|----------------|
| kenya_county_drought | NDMA drought phase by county |
| kenya_budget_summary | Controller of Budget county allocations |
| kenya_parliament_bills | Recent parliamentary bills |
| kenya_sacco_lookup | SASRA-registered SACCOs |
| kenya_rights_query | Constitutional rights by article |
| kenya_counties_list | All 47 counties with metadata |

---

## Key Legal Concepts for AI Tools

**Proportionality test:** Rights can be limited only if the limitation is:
1. Reasonable and justifiable in an open democratic society
2. Takes into account human dignity, equality, freedom
3. Proportional to the objective

**Progressive realization:** Article 43 economic/social rights are subject
to "progressive realization" — government must move toward full realization
within available resources. This is often cited to defend underfunding.

**Emergency provisions (Article 58):** During public emergency, some rights
can be suspended. Key rights that CANNOT be suspended even in emergency:
- Right to life
- Freedom from torture
- Freedom from slavery
- Right of non-refoulement (relevant for refugee tools)

---

## Data Provenance Rules

All civic data for AI tools must:
1. Cite the official source (NDMA, KNBS, Parliament, etc.)
2. Include the data date/period
3. Label synthetic/estimated data clearly: "DEMO — Synthetic data"
4. Not imply real-time accuracy unless the data is live

**Acceptable sources for Kenya civic data:**
- Official government websites (.go.ke domains)
- Kenya Gazette notices
- Kenya Law (kenyalaw.org) for legislation
- Parliament of Kenya Hansard
- Controller of Budget reports

---

## Constitutional Rights Quick Reference

| Article | Right | Limitation? |
|---------|-------|------------|
| 26 | Right to life | No (except lawful killing) |
| 27 | Equality and freedom from discrimination | Limited by law (proportional) |
| 28 | Human dignity | No |
| 29 | Freedom from cruel treatment | No |
| 31 | Privacy | Yes (law) |
| 32 | Conscience, religion, belief | Yes (law) |
| 33 | Expression | Yes (not hate speech, incitement) |
| 34 | Media | Yes (law) |
| 35 | Information | Yes (national security, privacy) |
| 36 | Association | Yes (law) |
| 37 | Assembly, demonstration | Yes (reasonable restrictions) |
| 39 | Movement | Yes (law) |
| 40 | Property | Yes (public purpose + compensation) |
| 41 | Labour | Yes (law) |
| 43 | Economic/social rights | Progressive realization |
| 47 | Fair administration | Yes |

---
*© 2026 AI Kung Fu LLC · MIT License · claude-east-africa-skills*
