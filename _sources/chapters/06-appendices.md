# Appendices

---

## Appendix A. The AI Use Roadmap as a Checklist

Work through the questions in order. A "stop" answer at any point ends the inquiry.

**Stage 1 — Define the use case**

- [ ] **Is it allowed?** Syllabus, workplace policy, publication rules, community norms. *(Check first; a negative answer ends the inquiry.)*
- [ ] **Is an AI tool the right instrument?** Mathematics → calculator or statistical software. Verified facts → library database. Deterministic tasks → deterministic tools.
- [ ] **Can you do it yourself?** *If yes, you probably do not need AI.*
- [ ] **Is the data restricted?** Personal, protected, confidential, or belonging to someone else. *If yes, stop — or use a local, non-connected tool.*

**Stage 2 — Evaluate the risk**

- [ ] **Does truth or accuracy matter?**
- [ ] **Do you have the expertise to verify the result?** *If no, stop.*
- [ ] **Will you actually verify it?** *A different question from the previous one, and where most failures occur.*
- [ ] **Are you willing to be held accountable for the outcome?** *If no, stop.*

**Stage 3 — Review the options**

- [ ] Is there an **approved, licensed** institutional tool?
- [ ] Is there an **open-source** tool that is adequate?
- [ ] If neither, and only then: a **proprietary chatbot**.
- [ ] **Does the tool align with your values?** *(Apply Appendix B.)*

**Terminal state: *maybe* use AI.**

---

## Appendix B. The FACT Framework as a Checklist

**Fairness**
- Does this tool treat all groups equitably?
- Does the output reinforce stereotypes or exclude groups?
- Assume it is biased. Can you discover the bias? Can you mitigate it?

**Accountability**
- If it makes a mistake, who is responsible? *(You.)*
- Are you comfortable with that?
- Can you stand behind the work if your supervisor asks?

**Confidentiality**
- Was private data used to build this tool?
- How does it use prompts and user data?
- Would you be comfortable seeing your prompt published on a front page?
- Can you delete your data? Are there opt-out settings? *(No opt-out is a red flag.)*

**Transparency**
- How was this built, by whom, and for what purpose?
- Who benefits, and who is affected?
- Does the company disclose training data and environmental impact?
- Can you explain how the result was reached? *If not, you are guessing rather than researching.*

**If a tool fails these four tests, find a different solution.**

---

## Appendix C. Prompting Quick Reference

### C.1 Do

| Practice | Why |
| --- | --- |
| Define the speaker | Sets the role; displaces inferred profile context |
| Define the audience | Sets register, depth, vocabulary |
| Provide relevant context | The highest-leverage action available |
| Decide input and output format in advance | List, narrative, table, file |
| Make chain of thought explicit | *Do this, then this, then this* |
| Ask for references | As leads to follow, never as citations |
| Be precise | Verbosity dilutes tuning |
| Provide examples | Form is a stronger instruction than description of form |

### C.2 Don't

| Avoid | Why |
| --- | --- |
| Treating it as a search engine | If it is a search question, use a search engine |
| Leading questions | Introduces unconscious bias into the answer |
| Vague questions | Produces the unremarkable mean |
| Anything you would not want public | Once submitted, it is out of your control |
| Trusting the answer | See Chapter 4 |

### C.3 Context Control Habits

- **Start a new chat** when the topic changes. Chat history is context.
- **Verify before the next prompt.** A wrong answer left in context contaminates everything after it.
- **Audit your platform profile.** The system injects context you did not supply.
- **Order matters.** Put context before the question, not after.

---

## Appendix D. Prompt Type Selection

| Situation | Strategy |
| --- | --- |
| Exploring a space; no exhaustive answer needed | **Zero-shot** |
| The output format matters and is easy to demonstrate | **One- / few-shot** |
| Classification or extraction against a fixed scheme | **Few- / multi-shot** (gains plateau around ten examples) |
| Multi-step analysis; reasoning must be inspectable | **Chain of thought**, with steps you specify |
| Recurring task with a stable structure | **Markdown Prompting Framework** file, reused |
| Complex task with a required output style | **Shot-based chain of thought** |

---

## Appendix E. Markdown Prompting Framework Template

Save as a plain `.md` text file. Drag into the prompt window, or copy and paste.

```markdown
# System Prompt: [short title]

## Role
You are a [role] who [relevant characteristics, tone, expertise].

## Audience
[Who the output is for: expertise level, context, what they need from it.]

## Context
[Background the model needs. Documents, prior decisions, constraints of the situation.]

## Constraints
* jurisdiction: [if relevant]
* scope: [what is in and out of scope]
* sources: [e.g. peer-reviewed literature after 2020]
* length: [if relevant]
* format: [table / narrative / bulleted list]

## Tasks
1. [First step.]
2. [Second step. Explain reasoning step by step and cite sources.]
3. [Third step.]
4. [Produce the deliverable.]

## Output
[What you want back, in what form.]
```

**Notes on use**

- `#` is read as a system-level instruction by all major chat interfaces. It does not override the platform's system context; it coexists with it.
- Constraint keys are not a controlled vocabulary. The model interprets them as natural language. Choose terms that are precise in your domain.
- The **Tasks** list is your chain of thought made structural.
- Expect to spend a couple of weeks tuning a prompt you intend to reuse. Add constraints where you observe drift.
- **Validate every result**, every time.

---

## Appendix F. The CRAAP Test — Print Version

| | General source | AI output |
| --- | --- | --- |
| **Currency** | Is the production date such that the information is relevant? | *How do you know the date of the information?* Beware time bias introduced by your prompt. |
| **Relevance** | Is the fact or argument relevant to my question? Who is the intended audience? | Is it relevant to your prompt — and did your prompt ask what you meant? |
| **Authority** | Does the person or organization have the credentials and experience to be reliable? | *How do you know the original source?* Does the tool have the training and corpus for this question? **The tool has no authority.** |
| **Accuracy** | Can you verify the claim in at least two other reputable sources? | **The same — and this is now the essential step.** |
| **Purpose** | Why was this created? Fact, opinion, entertainment, satire, propaganda? | Can you find the purpose at the source? *And:* what is the purpose of the tool, and what bias does it carry? |

---

## Appendix G. The Lateral Reading Workflow — Print Version

1. **Break it down.** Identify specific facts, claims, references, and sources of authority.
2. **Search.** Consult other sources to verify facts, references, and credentials.
3. **Analyze.** Weigh what the external sources show.
4. **Decide.** Determine whether the claim is valid.
5. **Repeat.** For every claim, fact, and source.

**With AI, check every claim.** Reliability does not accumulate across a response: the first ten claims may be true and the eleventh may be fabricated.

**When the tool supplies a source, verify the source too.** Click it. Follow the link. Read it. Apply CRAAP. A real source may still fail to support the claim attached to it.

---

## Appendix H. Identifying Synthetic Images — Field Checklist

**The overarching question: what generally doesn't make sense?**

| Category | Look for |
| --- | --- |
| **Functional implausibility** | Objects that could not do their job: staircases to nowhere, non-supporting poles, holes in columns, asymmetrical fastenings, railings at impossible levels, merged eyeglass earpieces |
| **Anatomical implausibility** | Missing or malformed features, incoherent facial expressions, mouths and teeth, artifacts between teeth. *(Hands are no longer reliable.)* |
| **Violations of physics** | Reflections that do not match the subject — mirrors, windows, puddles, lakes. Shadows inconsistent with the light source. |
| **Sociocultural implausibility** | Situations that are socially or culturally improbable. *(Red flag only: unlikely ≠ impossible.)* |
| **Stylistic artifacts** | Waxy or plastic texture, absent skin texture, cinematization, hyper-real but unnatural detail, inconsistent resolution or color |
| **Rendered text** | Signs, labels, and street names that are not real language |

**Detection depends on accumulated inconsistency, not one decisive artifact — and it takes more time than scrolling allows.**

### Verification steps

- **Different angles.** A real event usually generates multiple images from multiple people.
- **Reputable text references.** Is anyone credible writing about this?
- **Creator attribution.** Is there a named photographer or creator?
- **Publisher credentials.** Who is the source? What is the site?
- **Reverse image search.** TinEye, Google Images — trace it to origin, or find it debunked.
- **Digital watermarks.** SynthID and comparable systems; metadata is usually stripped by social platforms.

### Social media specifically

- Are they selling something? Is the image engineered to make you click?
- **How old is the account?** *500,000 followers and two weeks of history is a red flag.*
- What is the account history? Have earlier, more obviously synthetic images been deleted?
- Are all the videos short? *(At the time of writing, video over about a minute — particularly with sustained dialogue — is likely authentic, because generation is expensive and degrades with length. Expect this heuristic to expire.)*
- AI influencer accounts often disclose, but obliquely: in the account name, in a pun, in the biography, or behind an external link.

---

## Appendix I. Choosing an Instrument

### I.1 Alternatives to AI

| Task | Alternative | Why |
| --- | --- | --- |
| Fact-checking | Library databases, Google Scholar | Real, verified citations |
| Data analysis | R, Python | Transparency, accuracy, reproducibility |
| Literature review | Library database search; abstracts; Zotero | Nuance, context, organization |
| Math and logic | Calculator, specialized software | Calculation rather than prediction |
| Privacy-sensitive work | Local software, non-connected tools, paper | Data security |
| Deep thinking | Socratic dialogue with peers | Creativity and logic; knowable biases |

*All of these use less energy and water than a large language model.*

### I.2 AI Tools by Task

| Task | Example tools |
| --- | --- |
| General chatbots, brainstorming | ChatGPT, Copilot, Claude, Gemini |
| Coding | Claude Code, Copilot |
| Literature searching | Elicit, Consensus, Scite |
| Reading and summarizing | NotebookLM, Scholarcy, SciSpace |
| Text editing | Grammarly, LanguageTool |
| Note taking | Zoom AI Companion, Otter.ai |

*Tool names date rapidly; the categories do not.*

> **Private or sensitive data should be used only with institution-approved or licensed tools, for approved purposes.**

### I.3 Running Your Own

| Resource | Purpose |
| --- | --- |
| **Ollama** — <https://ollama.com/> | Local model runtime for Windows, macOS, Linux. No programming required; administrator privileges needed. Nothing leaves your machine. |
| **Hugging Face** — <https://huggingface.co/> | Repository of thousands of open models, many specialized by discipline. |

**Caution:** availability is not endorsement. Apply the FACT framework and confirm the model fits your use case.

---

## Appendix J. Resource Costs — Figures Cited in the Workshop

> **Read this appendix with its caveat.** These figures are simultaneously right and wrong depending on model, data center, region, and methodology. Precise numbers are difficult to obtain because the companies are private and are not obliged to disclose. What follows represents researchers' best efforts as presented in the workshop. **Treat every figure as an order of magnitude to be re-verified, not a constant.**

| Measure | Figure |
| --- | --- |
| U.S. electricity used by data centers, 2023 | 4.4% of annual use |
| Projected, 2028 | 12% |
| Water use, one medium-sized data center | ≈ 110 million gallons/year |
| Projected AI-sector freshwater use, 2027 | ≈ 1.7 trillion gallons/year — more than the total water use of Denmark |
| Training GPT-3 — carbon | ≈ lifetime emissions of 5 gasoline cars |
| Training GPT-3 — water | ≈ 1.5 Olympic swimming pools of drinking water evaporated |
| Writing a 100-word email | ≈ 3 bottles of fresh water |
| Generating one high-resolution image | ≈ one full smartphone battery charge |
| One AI prompt vs. one conventional search | ≈ 10× the electricity |

**Sources:** Strubell, Ganesh & McCallum (2019), <https://doi.org/10.48550/arXiv.1906.02243>; Li, Yang, Islam & Ren (2023), <https://arxiv.org/pdf/2304.03271>; Congressional Research Service R48646, <https://www.congress.gov/crs-product/R48646>.

---

## Appendix K. A Brief Chronology

| Year | Development |
| --- | --- |
| 1943 | Artificial neural networks first described (McCulloch & Pitts) |
| 1957 | First computer simulation of an ANN (Rosenblatt) |
| 1966 | ELIZA chatbot (Weizenbaum) |
| 1970s–80s | First "AI winter"; logic-based systems dominate |
| 1982–1986 | Backpropagation described (Werbos; Rumelhart, Hinton & Williams) |
| 1990s–2000s | Second "AI winter" |
| 2012 | AlexNet wins an image classification competition, triggering the deep learning boom |
| 2013 | word2vec introduces efficient word embeddings (Mikolov et al.) |
| 2017 | The transformer architecture (Vaswani et al.) |
| 2022 | ChatGPT released and marketed; public attention follows |

---

## Appendix L. Consolidated References

### Foundational technical papers

- McCulloch, W. S., & Pitts, W. (1943). A logical calculus of the ideas immanent in nervous activity.
- Rosenblatt, F. (1957–58). Work on the perceptron — the first computer simulation of an artificial neural network. *(Cited in the workshop by year and contribution; consult the primary literature for the exact reference.)*
- Rumelhart, D. E., Hinton, G. E., & Williams, R. J. (1986). Learning representations by back-propagating errors. *Nature*.
- Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks.
- Mikolov, T., et al. (2013). Efficient estimation of word representations in vector space.
- Vaswani, A., et al. (2017). Attention is all you need.
- Firth, J. R. (1957). A synopsis of linguistic theory.

### Ethics, bias, and social impact

- Bender, E. M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021). On the dangers of stochastic parrots: Can language models be too big? *FAccT '21*.
- Buolamwini, J., & Gebru, T. (2018). Gender shades: Intersectional accuracy disparities in commercial gender classification. *PMLR*.
- D'Ignazio, C., & Klein, L. F. (2020). *Data Feminism*. MIT Press.
- Noble, S. U. (2018). *Algorithms of Oppression: How Search Engines Reinforce Racism*. NYU Press.
- Haraway, D. (1985/1991). A Cyborg Manifesto. In *Simians, Cyborgs, and Women*. Routledge.
- *Coded Bias* (documentary, dir. Shalini Kantayya, 2020).

### Environmental cost

- Strubell, E., Ganesh, A., & McCallum, A. (2019). Energy and policy considerations for deep learning in NLP. <https://doi.org/10.48550/arXiv.1906.02243>
- Li, P., Yang, J., Islam, M. A., & Ren, S. (2023). Making AI less "thirsty." <https://arxiv.org/pdf/2304.03271>
- Luccioni, A. S., Viguier, S., & Ligozat, A.-L. (2023). Estimating the carbon footprint of BLOOM. *JMLR*.
- Congressional Research Service, R48646. <https://www.congress.gov/crs-product/R48646>

### Hallucination, validation, and information literacy

- Kalai, A. T., et al. (2025). Why language models hallucinate.
- Linardon, J., et al. (2025). Citation fabrication in AI-assisted mental health literature review.
- Ibrahim, et al. (2026). Conversational warmth and hallucination rates.
- Kamali, N., et al. (2024). How to distinguish AI-generated images from authentic photographs. <https://doi.org/10.48550/arXiv.2406.08651>
- Van Kampen, K. Evaluating resources and misinformation. University of Chicago Library. <https://guides.lib.uchicago.edu/c.php?g=1241077&p=9082343>
- University of Maryland Libraries. AI and information literacy: Fact-checking AI with lateral reading. <https://lib.guides.umd.edu/c.php?g=1340355&p=9880575>
- Cruz-Ocampo, et al. (2025). Student-reported cognitive effects of AI use.
- NASA. 2M1207 b — first image of an exoplanet. <https://science.nasa.gov/resource/2m1207-b-first-image-of-an-exoplanet/>

### Tools and practical resources

- Markdown Prompting Framework: <https://tenacity.io/snippets/supercharge-ai-prompts-with-markdown-for-better-results/>
- Ollama: <https://ollama.com/>
- Hugging Face: <https://huggingface.co/>
- Anthropic, Claude's character: <https://www.anthropic.com/research/claude-character>
- 3Blue1Brown — video series on neural networks and transformers.
- UC Davis DataLab: <https://datalab.ucdavis.edu> · Workshops: <https://datalab.ucdavis.edu/workshops/>

### Related UC Davis coursework

SOC 195 · STS 111, 115, 195 · PHI 133

---

## Appendix M. Sources for This Book

This textbook was assembled from the materials of a single delivery of the UC Davis *AI Literacy and Logic* workshop:

**Presentation decks**

- `session_a_welcome.pptx` — 8 slides
- `session_1_how_ai_thinks.pptx` — 48 slides
- `session_2_responsible_AI.pptx` — 29 slides
- `session_3_talk_to_AI.pptx` — 33 slides
- `session_4_ai_talks_to_you.pptx` — 55 slides

**Recordings**

- `AI Workshop modules 1-3 May 30.m4a` — 5 hours 0 minutes
- `AI Workshop module 4 May 30.m4a` — 1 hour 33 minutes

Slide text, speaker notes, and embedded tables were extracted programmatically. Recordings were transcribed automatically and used as the source for the expository narrative, the case studies, the classroom exercises, and the instructors' qualifications and asides. Figures are rendered directly from the original slides.

Where an automatic transcript was ambiguous, the slide text and speaker notes were treated as authoritative. Quantitative claims are reproduced as delivered, with the instructors' own caveats preserved.
