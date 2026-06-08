# Skill: Swahili Language Expert for AI Applications

## Purpose
Makes Claude an expert at Swahili NLP, culturally accurate Swahili content,
and the specific language challenges for East African AI tools.

## Load this skill when:
- Building Swahili-language AI tools
- Processing Swahili text (NLP, translation, classification)
- Writing Swahili UI text for Kenyan/Tanzanian users
- Fine-tuning models on Swahili data

---

## Key Facts

**Speaker base:** 47M+ first-language, 200M+ second-language across Kenya, Tanzania,
Uganda, Rwanda, DRC, Burundi, Mozambique, and the African Union.

**The accuracy gap:** AI models produce ~4× more errors in Swahili than English,
primarily due to a 500× training data gap in Common Crawl (arXiv:2509.04516, 2025).

**Dialects:**
- Standard: Kiswahili sanifu (Kenya/Tanzania standard)
- Urban: Sheng (Nairobi youth slang — English/Swahili/Kikuyu mix)
- Coastal: Kimvita (Mombasa), Kiamu (Lamu)
- For AI tools: default to Kiswahili sanifu; add Sheng understanding as secondary

---

## Swahili Grammar Essentials for AI Applications

### Noun classes (critical for agreement):
| Class | Singular | Plural | Example |
|-------|----------|--------|---------|
| M-/Wa- | m- | wa- | mtu/watu (person/people) |
| M-/Mi- | m- | mi- | mti/miti (tree/trees) |
| Ki-/Vi- | ki- | vi- | kitu/vitu (thing/things) |
| N-/N- | n- | n- | nyumba/nyumba (house/houses) |

Adjectives, verbs, and pronouns agree with noun class.
**AI trap:** Default to class agreement or outputs sound unnatural.

### Number system:
- 1-5: moja, mbili, tatu, nne, tano
- 6-9: sita, saba, nane, tisa
- 10: kumi
- 100: mia moja
- 1000: elfu moja / elfu

### Time:
Swahili clock offset by 6 hours from Western time.
"Saa moja asubuhi" = 7:00 AM (not 1:00 AM)
**AI trap:** Always clarify Western time when needed; never assume Swahili clock.

---

## Domain-Specific Vocabulary

### M-PESA / Financial:
- Lipa: pay
- Pesa: money
- Akaunti: account
- Tuma pesa: send money
- Pokea pesa: receive money
- Salio: balance
- Malipo: payment
- Risiti: receipt
- Mkopo: loan
- Riba: interest

### Civic / Government:
- Serikali: government
- Kaunti: county (Kenya's 47 counties)
- Bunge: parliament
- Sheria: law
- Haki: right/justice
- Katiba: constitution
- Uchaguzi: election
- Kura: vote
- Ushuru: tax
- Huduma: service

### Agriculture / Shamba:
- Shamba: farm/field
- Kilimo: agriculture/farming
- Mavuno: harvest
- Mbegu: seeds
- Mbolea: fertilizer
- Wadudu: pests/insects
- Ugonjwa wa mmea: plant disease
- Msaada wa kilimo: agricultural assistance

### Health (CHW context):
- Homa: fever
- Kikohozi: cough
- Kuhara: diarrhoea
- Maumivu: pain
- Hospitali: hospital
- Dawa: medicine
- Chanjo: vaccination
- Uzazi wa mpango: family planning
- Ujauzito: pregnancy

---

## Common AI Errors in Swahili (anti-patterns)

❌ "Mimi niko happy" (mixing English mid-sentence — Sheng, avoid in formal tools)
✅ "Ninafuraha" or "Mimi ni mwenye furaha"

❌ Using "wewe" as formal address
✅ Use "bwana/bibi" or "mheshimiwa" for formal contexts

❌ Treating Swahili as phonetic English with Swahili words
✅ Respect verb tense system: -na- (present), -li- (past), -ta- (future), -me- (perfect)

❌ Ignoring noun class agreement in generated text
✅ Check class: "kiatu kizuri" (good shoe, ki/ki class) not "kiatu mzuri"

---

## Prompting Patterns That Work

### For translation to Swahili:
```
Translate to standard Kiswahili (Kiswahili sanifu). 
Audience: [rural farmers | urban professionals | government officials].
Register: [formal | informal].
Avoid Sheng unless specifically targeting urban youth.
```

### For NLP classification:
```
Classify this Swahili text. Note:
- Swahili uses noun classes that affect word morphology
- Common code-switching with English in informal texts
- Numbers may be in Roman numerals or Arabic
Output: category, confidence, any code-switching detected
```

### For UI text:
```
Write Swahili UI text for: [feature description].
Max length: [N] characters.
Register: simple enough for primary school literacy level.
Avoid: government jargon, medical terms without explanation.
Include: KiEnglish (acceptable borrowed words like "internet", "simu", "kompyuta").
```

---

## Reference Datasets
- swahili-civic-nlp: https://huggingface.co/datasets/gmahia/swahili-civic-nlp
- kenya-agricultural-qa: https://huggingface.co/datasets/gmahia/kenya-agricultural-qa
- kenya-legal-nlp: https://huggingface.co/datasets/gmahia/kenya-legal-nlp
- IrokoBench (African language evaluation): arXiv:2406.03368
- Swahili accuracy gap study: arXiv:2509.04516

---
*© 2026 AI Kung Fu LLC · MIT License · claude-east-africa-skills*
