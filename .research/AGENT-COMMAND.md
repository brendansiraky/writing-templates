# Agent Command: Create 10 Writing Style Specs

## Context

This project defines writing styles as JSON specs precise enough that an LLM can produce writing that faithfully matches the described style. The format uses prescriptive rules as the primary mechanism, supplemented by exemplar passages.

**Key files already in place:**
- `/Users/brendan/code/writing-templates/writing-style.schema.json` — JSON Schema (draft 2020-12) defining the format
- `/Users/brendan/code/writing-templates/templates/conversational-storyteller.json` — A fully populated example to use as structural reference
- `/Users/brendan/code/writing-templates/.research/` — Four research documents covering academic taxonomies, professional frameworks, literary styles, and AI-specific style research

## Task

Create 10 writing style JSON files in `/Users/brendan/code/writing-templates/templates/`, each conforming to `writing-style.schema.json`. Use **10 agents, 1 style each**, all running in parallel. Each style is substantial enough to warrant a dedicated agent's full context window.

## The 10 Styles (Research-Backed)

### Agent 1 — `classic-prose.json`
- Thomas & Turner's most celebrated style from *Clear and Simple as the Truth* (Princeton UP, 1994). Classical Middle Style (genus medium).
- The writer sees something clearly and presents it to an intellectual equal. Language is a window onto the subject. Confidence without arrogance.
- Practitioners: The New Yorker (pre-1985), Descartes, Pascal, Didion at her clearest, Adam Gopnik.
- Meta: energy=medium, density=moderate, formality=medium, warmth=cool, vocabulary_level=advanced

### Agent 2 — `plain-prose.json`
- Orwell's 6 rules from "Politics and the English Language" (1946). Strunk & White's *Elements of Style*. Klinkenborg's *Several Short Sentences About Writing*. Classical Plain Style (genus tenue).
- Transparency, economy, clarity as a moral act. Every word earns its place. No ornamentation.
- Practitioners: Orwell, E.B. White, Klinkenborg, Zinsser.
- Meta: energy=low, density=sparse, formality=medium, warmth=cool, vocabulary_level=intermediate

### Agent 3 — `literary-minimalism.json`
- Established movement: Hallett *Minimalism and the Short Story* (1999), Buford's *Granta* 8 "Dirty Realism" (1983), Hemingway's "iceberg theory."
- Paratactic sentences, omission as meaning, subtext over text. What's left unsaid matters more than what's on the page.
- Practitioners: Hemingway, Raymond Carver, Amy Hempel, Lydia Davis, Denis Johnson, Grace Paley.
- Meta: energy=low, density=sparse, formality=medium, warmth=cold, vocabulary_level=basic

### Agent 4 — `narrative-journalism.json`
- Wolfe's 4 formal techniques (*The New Journalism*, 1973). McPhee's structural methods (*Draft No. 4*, 2017). Biber Dimension 2 (narrative).
- Scene-by-scene construction, full dialogue, third-person POV shifting, status-detail observation. Saturation reporting. The writer disappears; the subject comes alive.
- Practitioners: Tom Wolfe, Gay Talese, John McPhee, Susan Orlean, Patrick Radden Keefe.
- Meta: energy=medium, density=dense, formality=medium, warmth=warm, vocabulary_level=intermediate

### Agent 5 — `lyrical-contemplative.json`
- Thomas & Turner's Contemplative style. Lyric essay tradition (Miller & Paola, *Tell It Slant*, 2003). Nature writing tradition.
- Reflective, associative, poetic tools in prose, driven by musicality and attention. The writer reflects on inner experience and outer observation simultaneously.
- Practitioners: Annie Dillard, Virginia Woolf, Marilynne Robinson, Maggie Nelson, Robert Macfarlane.
- Meta: energy=low, density=dense, formality=medium, warmth=warm, vocabulary_level=advanced

### Agent 6 — `warm-explainer.json`
- Biber D1 (involved production) + D2 (narrative). Kinneavy's Referential-Informative aim. Britton's Transactional function.
- Complex subjects made delightful through character, analogy, and genuine enthusiasm. Expertise worn lightly. The writer is thrilled to be telling you this.
- Practitioners: Bill Bryson, Oliver Sacks, Mary Roach, Ed Yong, Randall Munroe.
- Meta: energy=high, density=moderate, formality=low, warmth=hot, vocabulary_level=intermediate

### Agent 7 — `analytical-wit.json`
- Thomas & Turner's Classic style + humor. NN/g dimensions (serious + casual + matter-of-fact). Biber D4 (persuasion).
- Sharp analysis delivered with deadpan humor and compression. The joke lives in the unexpected precision of the observation. Complex ideas made legible through wit.
- Practitioners: The Economist house style, Matt Levine, Joan Didion's criticism, Fran Lebowitz, Nora Ephron.
- Meta: energy=high, density=moderate, formality=low, warmth=cool, vocabulary_level=advanced

### Agent 8 — `oratorical-persuasion.json`
- Classical Grand Style (genus grande). Thomas & Turner's Oratorical style. Lanham *Analyzing Prose* (2003). Biber D4 (overt persuasion).
- Periodic sentences, tricolon, anaphora, emotional crescendo. Language deployed for maximum rhetorical force. The Grand Style moves people to action.
- Practitioners: MLK, Frederick Douglass, Obama, Cicero, Toni Morrison's essays, Ta-Nehisi Coates.
- Meta: energy=high, density=dense, formality=high, warmth=warm, vocabulary_level=advanced

### Agent 9 — `personal-essay.json`
- Lopate *The Art of the Personal Essay* (1994). Britton's Expressive function (1975). Kinneavy's Expressive aim (1971). The Montaigne tradition.
- First-person reflection using the self as lens for exploring a subject. The particular illuminating the universal. Intimacy without narcissism.
- Practitioners: Montaigne, James Baldwin, Zadie Smith, Leslie Jamison, Brian Doyle, Roxane Gay.
- Meta: energy=medium, density=moderate, formality=low, warmth=warm, vocabulary_level=intermediate

### Agent 10 — `practical-instructional.json`
- Thomas & Turner's Practical style. Diataxis framework (Procida). Podmajersky *Strategic Writing for UX* (O'Reilly, 2019). Biber D1 (informational pole).
- Language in service of action. The reader needs to do something, and the writing helps them do it. Respects the reader's time and intelligence.
- Practitioners: Stripe docs, Paul Graham's practical essays, Derek Sivers, the best README files.
- Meta: energy=medium, density=moderate, formality=medium, warmth=cool, vocabulary_level=intermediate

## Quality Standards (CRITICAL)

Every one of the 21 `spec` sections must meet the **granularity standard**:
- **Quantitative**: "12-18 words average" not "short sentences"
- **Prescriptive**: what to do AND what not to do
- **Mechanistic**: "front-load subject and verb in first 7 words" not "be clear"
- **Exemplified**: at least one concrete example sentence/phrase per section
- **Exception-aware**: "Never X, except when Y"

The `exemplar_passages` section must contain 2-3 original passages (~150-200 words each) **written in the described style**. These passages must demonstrate all rules operating simultaneously. They should be genuinely good writing — not mechanical demonstrations.

The `anti_patterns` section must include AI-typical patterns to avoid (reference `.research/ai-style-research.md` for the comprehensive lists of AI tells).

## Execution Plan

1. **Read reference files first**: Each agent MUST read `writing-style.schema.json` and `templates/conversational-storyteller.json` before writing anything. Agents should also read the relevant research docs in `.research/`.

2. **Create a team** called `style-creators` with 10 agents.

3. **Spawn 10 agents in parallel**, one per style as specified above. Each agent should:
   - Read the schema and example template
   - Read relevant research from `.research/`
   - Create its single style JSON file in `/Users/brendan/code/writing-templates/templates/`
   - Ensure JSON is valid and well-formatted

4. **After all agents complete**, validate all 10 files against the schema:
   ```
   npx ajv-cli validate -s writing-style.schema.json -d "templates/*.json" --spec=draft2020
   ```

5. **Report results** — list all created files and validation status.

## Important Notes

- Use `bypassPermissions` mode for agents so they can write files without prompts.
- Each style must be **genuinely distinct** — different sentence lengths, different rhythms, different diction, different emotional registers. If two styles sound similar in their exemplar passages, one of them is wrong.
- The research docs in `.research/` contain specific practitioner signatures, movement definitions, and framework details. USE THEM — don't just make things up.
- Refer to `templates/conversational-storyteller.json` for the expected level of detail, length, and specificity in each section. Match or exceed its quality.
