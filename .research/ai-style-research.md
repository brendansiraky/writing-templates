# AI/LLM Writing Style Research

Research compiled on how AI/LLM practitioners classify, specify, and evaluate writing styles for language model generation.

---

## 1. Palmer's Five-Layer Voice Profile System

**Source:** Shelly Palmer, "Getting AI to Write Like You" (February 2026)
**URL:** https://shellypalmer.com/2026/02/getting-ai-to-write-like-you/

Palmer developed a five-layer architecture for capturing and reproducing an author's authentic voice through AI:

### Layer 1: Context Profile
A structured JSON document (500+ lines) containing:
- Voice characteristics
- Tone descriptions
- Forbidden constructions
- Approved vocabulary
- Format specifications per post type
- Thesis placement rules
- Paragraph discipline targets

### Layer 2: Critics Framework
Nine specialized evaluators scoring distinct dimensions:
1. Hook strength
2. Thesis clarity
3. Evidence quality
4. Business implications
5. Structure
6. Voice consistency
7. Insight density
8. Originality
9. Format compliance

### Layer 3: Definitive Writing Profile
Extracted from analysis of published work, codifying actual mechanics:
- Sentence construction patterns
- Paragraph development habits
- Punctuation preferences
- Hedging conventions
- Personal interjection rules

Key insight: Palmer discovered that distinctive voice emerges from "grade-school simple sentence structures carrying expert-level content."

### Layer 4: Exemplar Database
A vectorized, searchable collection of published writing used for RAG retrieval:
- Topic-relevant passages
- Format-matched openings/closings
- Past correction examples

### Layer 5: Auto-Diff Feedback Loop
Compares AI drafts to published (human-edited) versions, classifying each correction:
- Tightening edits
- Vocabulary changes
- Forbidden pattern removals
- Grammar fixes
- Structural modifications

Each correction becomes a retrieval signal for future drafts, enabling continuous improvement without manual re-specification.

**Relevance:** This is the most comprehensive structured voice specification system found. It demonstrates that effective voice capture requires multiple complementary layers -- a static specification alone is insufficient. The feedback loop concept is particularly novel.

---

## 2. Bezdek's Definitive LLM Writing Style Guide

**Source:** Viktor Bezdek, "The Definitive Guide to LLM Writing Styles" (GitHub)
**URL:** https://viktorbezdek.github.io/definitive-llm-writing-style-guide/
**Also:** https://github.com/viktorbezdek/definitive-llm-writing-style-guide

Bezdek organizes LLM writing styles into 16 primary dimensions, each with low/medium/high calibration:

### Personality Traits (Big Five + extensions)
Openness, Conscientiousness, Extraversion, Agreeableness, Neuroticism, Assertiveness, Empathy, Optimism, Humility, Ambition, Curiosity, Honesty, Risk-taking, Adaptability, Tolerance

### Emotional Intelligence
Self-awareness, Self-regulation, Motivation, Empathy, Social skills, Emotional perception, Expression, Assertiveness, Independence, Optimism, Stress tolerance, Self-actualization, Adaptability, Trust, Conflict resolution

### Cognitive Style
Analytical, Creative, Strategic, Detail-oriented, Big-picture thinking, Systematic, Intuitive, Practical, Scientific, Abstract thinking, Logical, Verbal, Visual, Concrete, Sequential

### Values and Beliefs
Conservative/Progressive, Liberal/Libertarian, Religious/Secular, Humanist, Environmentalist, Capitalist/Socialist, Patriotic, Globalist, Individualistic/Collectivistic

### Communication Style
Direct/Indirect, Formal/Informal, Factual/Emotional, Analytical/Intuitive, Verbose/Concise, Confident/Hesitant, Humorous/Serious, Respectful, Friendly, Fast/Slow-paced, Visual/Auditory/Kinesthetic, Functional/Expressive

### Language Register
Formal, Informal, Colloquial, Slang, Jargon, Technical, Academic, Literary, Poetic, Nostalgic, Inspirational, Humorous, Sarcastic, Ironic, Sincere, Exaggerated, Understated, Persuasive, Informative, Instructional, Conversational, Oratorical, Intimate, Casual

### Tone
Humorous, Sarcastic, Ironic, Friendly, Optimistic, Assertive, Confident, Playful, Persuasive

### Voice
Conversational, Sarcastic, Humorous, Enthusiastic, Informal, Friendly, Assertive, Confident, Optimistic, Persuasive, Playful, Ironic

### Narrative Style
First-person, Stream of consciousness, Nonlinear, Flashback, Foreshadowing, Cliffhanger, Plot twist, Irony, Metaphor, Simile, Satire, Unreliable narrator, Vignette

### Additional Dimensions
- Jargon (field-specific terminology)
- Slang (group-specific informal language)
- Politeness strategies
- Gendered language markers
- Age-specific language
- Socioeconomic language markers
- Cultural background

**Relevance:** This is the most exhaustive taxonomy found. It attempts to parameterize every conceivable dimension of writing style. However, its breadth may work against practical usability -- specifying 16 dimensions with 15+ options each creates an overwhelming configuration space. The low/medium/high calibration per dimension is a useful simplification pattern.

---

## 3. Forte Labs AI Style Guide Method

**Source:** Tiago Forte, "How to Create an AI Style Guide" (Forte Labs blog)
**URL:** https://fortelabs.com/blog/how-to-create-an-ai-style-guide-write-with-chatgpt-in-your-own-voice/

Forte's approach is analysis-first: feed existing writing samples to an LLM and have it extract a style profile.

### Analytical Dimensions Extracted
- **Voice and Tone:** e.g., "authoritative yet relatable," blend of formality and conversationality
- **Mood:** Emotional atmosphere (optimistic, encouraging, empowering)
- **Sentence Structure:** e.g., "mix of simple, compound, and complex structures"
- **Transition Style:** e.g., "connective phrases like 'in other words,' 'but most of all'"
- **Rhythm and Pacing:** Balance of short punchy sentences with longer explanations
- **Signature Styles:** Recurring techniques like personal anecdotes, rhetorical questions, lists, and direct reader address

### Recommended Method
1. Identify 4-6 signature writing samples using analytics
2. Feed each to ChatGPT with a detailed analysis prompt
3. Ask ChatGPT to summarize voice, tone, diction, style, and structure
4. Consolidate into a structured style guide with section headings, descriptions, and actionable guidelines
5. Iterate across multiple pieces to capture consistency

**Relevance:** This bottom-up approach (analyze then specify) is complementary to top-down taxonomies. It captures what actually makes someone's writing distinctive rather than asking them to self-report across abstract dimensions. The analysis prompt itself becomes a key artifact.

---

## 4. Common Prompt Engineering Approaches for Writing Style

### Popular Frameworks

**POWER Framework** (widely cited in 2025 prompt engineering guides):
- Purpose
- Output format
- Word choice/style
- Examples
- Refinement constraints

**CRISP Framework:**
- Context
- Role
- Instructions
- Style
- Parameters

### Key Style Specification Components
From multiple sources (OpenAI prompt engineering guide, Lakera, PromptBuilder, GodOfPrompt):

1. **Tone:** formal/casual/friendly/persuasive/empathetic/humorous/authoritative
2. **Audience:** who the writing is for (shapes vocabulary, structure, depth)
3. **Format:** paragraphs/bullets/numbered lists/JSON/headers
4. **Constraints:** word limits, reading level, number of sections
5. **Examples/samples:** reference texts to match
6. **Negative instructions:** what NOT to do (often more effective than positive)

### Best Practice: Constraint-Based Design (2025 consensus)
Simple constraints like "three bullets only" or "keep it under one paragraph" dramatically improve output quality. Specifying what to avoid is often more effective than specifying what to include.

### ChatGPT Custom Instructions Method
From multiple sources (Zapier, GodOfPrompt, OpenAI Academy):
- Go to Settings > Personalization > Custom Instructions
- Specify preferred tone, contractions, sentence length, formality level
- Provide writing samples and ask ChatGPT to "summarize my tone and style"
- Key dimensions: word choice, sentence length, level of formality, use of contractions, vocabulary sophistication

**Sources:**
- https://platform.openai.com/docs/guides/prompt-engineering
- https://www.lakera.ai/blog/prompt-engineering-guide
- https://promptbuilder.cc/blog/prompt-engineering-in-2025-complete-guide
- https://www.godofprompt.ai/blog/60-best-writing-style-for-chatgpt-prompts
- https://zapier.com/blog/train-chatgpt-to-write-like-you/

---

## 5. Popular Writing Styles Requested from AI

**Source:** GodOfPrompt, "60+ Best Writing Styles for ChatGPT Prompts"
**URL:** https://www.godofprompt.ai/blog/60-best-writing-style-for-chatgpt-prompts

### Organized by Category

**Conversational:** Casual, Formal, Friendly, Humorous, Empathetic, Direct, Supportive

**Technical:** Instructional, Analytical, Structured, Complex, Simplified, Mathematical, Step-by-Step, Comparative

**Creative:** Storytelling, Poetic, Descriptive, Dramatic, Satirical, Playful, Metaphorical, Abstract, Inspirational, Mythical/Fantasy

**Genre-Specific:** Technical Documentation, Research Paper, Blog Post, News Report, Interview Style, Review Style, Report Writing, Legal Writing, Marketing Copy

**Tone-Based:** Persuasive, Authoritative, Neutral, Cautious, Encouraging, Professional, Reflective, Concise

**Educational:** Didactic, Socratic, Explanatory, Informative, Evaluative, Reflective Educational

**Hybrid:** Problem-Solving, Forecasting, Hypothetical, Conversational Hybrid, Advisory, Factual Storytelling, Objective

**Relevance:** This list represents what practitioners actually ask for, as opposed to academic taxonomies. Notable patterns: (1) conversational and professional styles dominate, (2) creative styles are well-represented, (3) most styles can be described in 1-2 words, suggesting simple labels are preferred over complex specifications.

---

## 6. Anti-AI Writing Patterns (What Makes AI Writing Detectable)

### PNAS Study: LLMs vs. Human Writing

**Source:** Rosenbusch et al., "Do LLMs write like humans? Variation in grammatical and rhetorical styles" (PNAS, 2025)
**URL:** https://www.pnas.org/doi/10.1073/pnas.2422455122

Key findings using Douglas Biber's 66 linguistic feature categories:

- **Present participial clauses:** Instruction-tuned models use these at 2-5x the rate of human text
  - Example: "Bryan, leaning on his agility, dances around the ring"
- **Nominalizations:** LLMs use noun formations at 1.5-2x the rate of humans
- **Agentless passive voice:** GPT-4o uses at roughly half the human rate
- **Critical finding:** Instruction tuning makes output LESS human, not more -- models converge toward "informationally dense, noun-heavy style"
- **Vocabulary overuse:** Words like "camaraderie," "palpable," and "tapestry" used at 100x+ human rates
- **Reduced stylistic variation:** LLMs struggle to match human variation across registers

### Wikipedia: Signs of AI Writing

**Source:** Wikipedia editors, "Wikipedia:Signs of AI writing"
**URL:** https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
**Analysis:** https://www.onlinewritingclub.com/p/18-signs-you-used-ai-to-write-that

Key patterns identified across thousands of examples:

**Structural:**
- Overuse of the "rule of three" (adjective, adjective, adjective)
- Rigid paragraph structure: topic sentence -> evidence -> summary
- Uniform sentence length and cadence
- Excessive mechanical boldface formatting
- Formulaic em-dash usage (mimicking "punched up" sales writing)

**Vocabulary:**
- "Delve" (peaked 2023-24, declined 2025)
- Substitutes "serves as" and "mark the" for simpler alternatives
- Prefers "features" and "offers" over "has"
- Overuses hedge words: "might," "could," "perhaps," "generally"
- Perpetually balanced hedging (presenting multiple perspectives even when unnecessary)

**Tone:**
- Avoids contractions (sounds stiff)
- Corporate documentation feel
- Emotional flatness
- Repetitive circling around the same idea with slightly different words

### Blake Stockton: AI Red Flag Words

**Source:** Blake Stockton, "Don't Write Like AI" series (The AI Writers Room)
**URL:** https://www.blakestockton.com/red-flag-words/

Categorized overused AI words:

**Innovation/Change/Strategy:** Unlock, Transform, Revolutionize, Future-proof, Game-changer, Strategic, Supercharge, Harness, Leverage, Optimize, Streamline, Unleash, Unprecedented, Seamless, Cutting-edge, Best-in-class, Next-generation

**Business/Value Framing:** Enable, Crucial, Essential, Key, Robust, Distinct, Elevated, Aligned, Proactive, Nuanced, Innovative, Intersection

**Conversational/Transitional:** Moreover, The goal?, The result?, The bottom line, Thrilled, Delve, Foster, Emphasize

**Structural Patterns:**
- "It's not X, it's Y" (negation pattern)
- "In today's world..." / "In today's competitive business environment..."
- Colons used excessively for emphasis
- "From X to Y" constructions

### Augmented Educator: Ten Telltale Signs

**Source:** Michael G. Wagner, "The Ten Telltale Signs of AI-Generated Text"
**URL:** https://www.theaugmentededucator.com/p/the-ten-telltale-signs-of-ai-generated

1. Overuse of transitional phrases and hedging language
2. Predictable sentence templates and structural monotony
3. Formal and academic vocabulary choices (words like "delve," "underscore," "harness," "illuminate")
4. Absence of genuine personal voice and emotional resonance
5. Excessive use of em-dashes as universal punctuation
6. (Signs 6-10 behind paywall)

### Comprehensive Overused AI Word Lists

**Sources:** Multiple (Grammarly, Embryo, Walter Writes AI, Textero, Microsoft 365)

Consensus overused words across all sources:
- **Transitions:** Moreover, Furthermore, However, Notably, Therefore, Additionally, Significantly, Subsequently, Accordingly, Indeed
- **Filler adjectives:** Innovative, Cutting-edge, Comprehensive, Robust, Seamless, Dynamic, Scalable, Groundbreaking
- **Action verbs:** Delve, Harness, Leverage, Optimize, Streamline, Unlock, Unleash, Navigate, Elevate, Foster
- **Phrases:** "At its core," "Pave the way for," "At the forefront of," "Unlock the potential of," "In the realm of," "Ever-evolving," "Tapestry of"

**Relevance for style templates:** These patterns define the NEGATIVE space -- what writing styles should explicitly avoid to sound authentic. Any good style specification should include a "forbidden patterns" list derived from these findings.

---

## 7. Academic Foundations: Biber's Dimensions of Variation

**Source:** Douglas Biber, "Variation across Speech and Writing" (Cambridge University Press, 1988)
**Also:** "Dimensions of Register Variation" (1995)

Biber identified six fundamental dimensions of linguistic variation through factor analysis of 66 linguistic features across 23 spoken and written genres:

1. **Involved vs. Informational Production** -- interactiveness, affective content vs. dense informational content
2. **Narrative vs. Non-Narrative Concerns** -- storytelling features vs. non-narrative
3. **Explicit vs. Situation-Dependent Reference** -- explicit marking vs. reliance on context
4. **Overt Expression of Persuasion** -- persuasive/argumentative features
5. **Abstract vs. Non-Abstract Information** -- abstract/technical vs. concrete
6. **On-line Informational Elaboration** -- real-time production features

Each dimension represents a continuum. Features co-occurring on each dimension were identified through factor analysis. This framework was directly used in the PNAS study above for evaluating LLM output.

**Relevance:** Biber's dimensions are the most scientifically validated framework for describing writing style variation. They operate at a more fundamental level than "tone" or "voice" labels. The PNAS study shows LLMs are systematically skewed on these dimensions (especially Dimension 1: too informational, not enough involved).

---

## 8. Text Style Transfer Research: Style Categories

**Source:** Jin et al., "Deep Learning for Text Style Transfer: A Survey" (Computational Linguistics, MIT Press, 2022)
**URL:** https://direct.mit.edu/coli/article/48/1/155/108845/Deep-Learning-for-Text-Style-Transfer-A-Survey

**Also:** "A Survey of Text Style Transfer: Applications and Ethical Implications" (2024)
**URL:** https://arxiv.org/html/2407.16737v1

### Style Attributes Studied in TST Research
The NLP community has converged on these primary style attributes for text style transfer:

1. **Sentiment** (positive/negative)
2. **Formality** (formal/informal)
3. **Politeness** (polite/impolite)
4. **Humor** (humorous/non-humorous)
5. **Emotion** (joy, sadness, anger, fear, etc.)
6. **Toxicity** (toxic/non-toxic)
7. **Simplicity** (simple/complex)
8. **Biasedness** (biased/neutral)
9. **Authorship** (author-specific style)
10. **Gender** (masculine/feminine coded)
11. **Political slant** (left/right)

### Key Research Insight
Style transfer works best when the target style can be defined on a clear axis (e.g., formal<->informal). Multi-attribute style transfer (changing multiple style dimensions simultaneously) remains a harder problem. This suggests that style specifications should decompose into independent, axis-aligned dimensions rather than holistic labels.

**Also relevant:** "From theories on styles to their transfer in text: Bridging the gap with a hierarchical survey" (Cambridge, Natural Language Engineering) which proposes a hierarchical taxonomy bridging literary style theory and NLP style transfer.

---

## 9. Stylometric Analysis: Measurable Writing Features

**Source:** Hassaan-Elahi, "Writing-Styles-Classification-Using-Stylometric-Analysis" (GitHub)
**URL:** https://github.com/Hassaan-Elahi/Writing-Styles-Classification-Using-Stylometric-Analysis

Stylometrics provides measurable, quantitative features of writing style:

### Lexical Features
- Word frequency distributions
- Word length distributions
- Vocabulary size
- Hapax legomena (words used only once)
- Type-token ratio

### Syntactic Features
- Sentence length (mean, variance)
- Clause structure complexity
- Use of subordination vs. coordination
- Part-of-speech distributions

### Readability Metrics
- Flesch-Kincaid grade level
- Gunning Fog Index
- Coleman-Liau Index
- SMOG Index

### Vocabulary Richness
- Yule's K
- Simpson's D
- Honore's R

**Relevance:** These quantifiable features can serve as measurable targets in style specifications. Rather than saying "write simply," a template could specify "Flesch-Kincaid grade 8, average sentence length 15 words, type-token ratio > 0.6."

---

## 10. Synthesis: Key Insights for Style Template Design

### What Works for Specifying AI Writing Style

1. **Constraint-based specification outperforms aspiration-based.** "Don't use em-dashes" works better than "write naturally." Forbidden pattern lists are highly effective.

2. **Simple labels are sufficient for most use cases.** Users request styles like "casual," "professional," "storytelling" -- not 16-dimensional personality vectors. Practical style specs should start simple.

3. **Writing samples are the gold standard.** Both Palmer and Forte independently found that analyzing existing writing produces better specifications than abstract description. "Write like this example" beats "write in a warm, engaging, yet authoritative tone."

4. **The most important axes are:**
   - Formality (formal <-> casual)
   - Information density (dense <-> conversational)
   - Emotional involvement (detached <-> personal)
   - Sentence complexity (simple <-> complex)
   - Vocabulary level (plain <-> specialized)
   - Directness (direct <-> hedging)

5. **Anti-patterns matter as much as target patterns.** Every style spec should include what to AVOID. The overused-AI-word research provides a ready-made exclusion list.

6. **Instruction tuning pushes LLMs toward a specific "AI style."** The PNAS research shows this style is: informationally dense, noun-heavy, hedging, formally academic, structurally rigid, and emotionally flat. Any style that differs from this default must explicitly counteract these tendencies.

7. **Multi-layered specifications outperform single-prompt instructions.** Palmer's five-layer system, while complex, demonstrates that voice consistency requires specification at multiple levels: vocabulary, sentence structure, paragraph organization, rhetorical patterns, and forbidden constructions.

8. **Quantitative targets help.** Specifying measurable features (sentence length, reading level, paragraph length) provides objective anchors that complement subjective descriptions like "friendly tone."

### Recommended Specification Structure
Based on this research, an effective writing style template should include:

```
1. Style label (1-2 word name)
2. Core description (1-2 sentences capturing the overall feel)
3. Key axes with position:
   - Formality: [formal/neutral/casual]
   - Density: [dense/moderate/light]
   - Emotion: [detached/balanced/personal]
   - Complexity: [simple/moderate/complex]
   - Vocabulary: [plain/standard/specialized]
   - Directness: [blunt/balanced/diplomatic]
4. Quantitative targets:
   - Reading level
   - Avg sentence length
   - Paragraph length range
5. Positive patterns (DO):
   - Specific constructions, transitions, rhetorical devices
6. Negative patterns (DON'T):
   - Forbidden words, phrases, structures
7. Exemplar text (1-3 paragraphs showing the style in action)
8. Audience description
```

---

## Sources Index

### Academic / Research
- Biber, D. (1988). *Variation across Speech and Writing*. Cambridge University Press.
- Biber, D. (1995). *Dimensions of Register Variation*. Cambridge University Press.
- Jin, D. et al. (2022). "Deep Learning for Text Style Transfer: A Survey." *Computational Linguistics*, MIT Press. https://direct.mit.edu/coli/article/48/1/155/108845/
- Rosenbusch, H. et al. (2025). "Do LLMs write like humans? Variation in grammatical and rhetorical styles." *PNAS*. https://www.pnas.org/doi/10.1073/pnas.2422455122
- Gunawardhana, G. (2025). "How to Spot AI-Generated Text: Telltale vs. Subtle Signs." SSRN. https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5403685
- "A Survey of Text Style Transfer: Applications and Ethical Implications" (2024). https://arxiv.org/html/2407.16737v1

### Practitioner / Industry
- Palmer, S. (2026). "Getting AI to Write Like You." https://shellypalmer.com/2026/02/getting-ai-to-write-like-you/
- Bezdek, V. "The Definitive Guide to LLM Writing Styles." https://viktorbezdek.github.io/definitive-llm-writing-style-guide/
- Forte, T. "How to Create an AI Style Guide." https://fortelabs.com/blog/how-to-create-an-ai-style-guide-write-with-chatgpt-in-your-own-voice/
- GodOfPrompt. "60+ Best Writing Styles for ChatGPT Prompts." https://www.godofprompt.ai/blog/60-best-writing-style-for-chatgpt-prompts
- Stockton, B. "Don't Write Like AI" series. https://www.blakestockton.com/red-flag-words/
- Wagner, M. "The Ten Telltale Signs of AI-Generated Text." https://www.theaugmentededucator.com/p/the-ten-telltale-signs-of-ai-generated

### Reference / Encyclopedic
- Wikipedia. "Signs of AI writing." https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- OpenAI. "Prompt Engineering Guide." https://platform.openai.com/docs/guides/prompt-engineering
- Grammarly. "Decoding AI Language: Common Words and Phrases." https://www.grammarly.com/blog/ai/common-ai-words/
- Microsoft 365. "Six common words and phrases used by AI to avoid." https://www.microsoft.com/en-us/microsoft-365-life-hacks/everyday-ai/six-obvious-ai-words-to-avoid-in-your-writing
