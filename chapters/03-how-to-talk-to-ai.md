# Chapter 3. How to Talk to AI

> *Session 3 of the AI Literacy and Logic workshop. Lead instructor: Dr. Carl G. Stahmer, Director, UC Davis DataLab.*

## Learning Objectives

Upon completing this chapter, the reader should be able to:

1. Distinguish the *searchbot* and *cyborg* modes of AI engagement and describe the empirical consequences of each for cognition and for output quality.
2. Explain the three failure modes of searchbot-style prompting: hallucination, inherited bias, and the unremarkable mean.
3. Manipulate the three levers of prompt engineering — format, context, and tuning — to steer a model's output.
4. Explain why the *position* of context within a prompt affects the result, and how chat history and system profiles introduce context the user did not supply.
5. Select among zero-shot, shot-based, chain-of-thought, and combined prompting strategies according to task.
6. Construct a structured prompt using the Markdown Prompting Framework, and explain its advantages for reuse and for the user's own thinking.
7. Apply the prompting "do" and "don't" lists, including the argument for precision over verbosity.
8. Identify circumstances in which a local or specialized open model is preferable to a general-purpose commercial chatbot.

## Framing

![How you talk to AI matters — a lot.](assets/ch3-fig-01-how-you-talk-matters.png)

*Figure 3.1. Prompting affects both the quality of the output and the user's own cognition.*

Three propositions organize this chapter.

1. **How you interact with AI has a profound impact on your brain.**
2. **Good prompting strategies reduce errors and deliver more useful results.**
3. **Happily, the strategies that deliver the best results are also the best for your brain.**

The third proposition is the fortunate one, and it is the reason this chapter can be read either as a guide to productivity or as a guide to cognitive self-preservation without the two diverging.

A note on scope: this chapter assumes interaction through a chat interface rather than through a programming interface or an agentic system. The text a user submits is the **prompt**, and the discipline of structuring it is **prompt engineering**. It is more involved than most people realize, and it is not difficult to master. The obstacle is chiefly that most users have never considered that there is more than one way to talk to the machine.

---

## 3.1 Two Modes of Engagement

![Three patterns of AI use, divided into searchbot and cyborg approaches.](assets/ch3-fig-02-types-of-ai-engagement.png)

*Figure 3.2. Types of AI engagement.*

Enough time has now elapsed, and enough interest has accumulated, that researchers are able to study what people actually do with these systems. The distribution is not hypothetical.

| Share of users | Pattern | Example |
| --- | --- | --- |
| **70%** | Using AI primarily to generate answers to questions | *"Why has there been so little snow in the Sierras this year?"* |
| **20%** | Using AI primarily to validate their own assumptions | *"Why do cats make better pets than dogs?"* |
| **10%** | Engaging AI as a collaborator — exploring ideas, challenging assumptions, working jointly toward a solution | — |

*Table 3.1. Patterns of AI engagement. Framework and figures after Vivienne Ming.*

The first two rows constitute the **searchbot approach**: the user asks a question and accepts what comes back. The third row is the **cyborg approach**.

The 20% figure deserves particular attention, because it is the least visible failure. Asking *why do cats make better pets than dogs* does not pose a question; it presupposes an answer. The model will supply reasons, because the context supplied has made the conclusion foregone. Users do this constantly without noticing, and the effect is to guarantee that the interaction moves no closer to the truth.

That only one user in ten engages collaboratively is not primarily a failure of individuals. Nobody has taught most users how to do otherwise; the world is not full of good examples. Worse, the entire apparatus — the chat interface, the conversational tone, the first person — is designed to make it feel as though one is talking to a person. The natural inclination is therefore to talk to it like a person, which turns out to be close to the worst available strategy. This chapter works against that inclination deliberately.

---

## 3.2 The Cost of the Searchbot Approach

### 3.2.1 Cognitive Cost

![Research and commentary on the cognitive effects of reflexive AI use.](assets/ch3-fig-03-searchbot-cognitive-cost.png)

*Figure 3.3. Student-reported cognitive effects of AI use.*

Controlled studies and human-subject research support a claim that is uncomfortable and worth stating plainly: **using AI reflexively, as a substitute for thinking, measurably degrades the capacity to think.**

The mechanism is neuroplasticity operating as designed. When complex problem-solving is repeatedly offloaded to a machine, the brain reallocates: *we don't need that anymore; let us use the energy elsewhere.* Neurons rewire, and the ability to solve problems of that kind declines.

> **The Google Maps precedent.** The best-documented case is spatial navigation. Before turn-by-turn navigation, drivers who received directions did not memorize *turn left here*; they constructed a spatial representation anchored to landmarks and street names, and navigated against that internal model. After widespread adoption of navigation software, human spatial reasoning ability declined measurably and across the board. A person who could solve a class of spatial problems before, and who uses navigation software for a few years, can no longer solve them.

The experimental design that establishes the analogous effect for AI is straightforward. Administer a battery of standardized cognitive tests to a cohort. Instruct them to use AI to solve every problem they encounter — simply ask, and act on the answer. Retest six months later. Scores decline.

Several published assessments in the same vein:

- *"My conclusion is that artificial intelligence is antithetical to human cognition."* — John Nosta, Nosta Lab
- *"Used reflexively as a shortcut, AI creates 'cognitive debt,' making people faster while quietly eroding their skills."* — Rebecca Hinds, Work AI Institute
- *"AI's biggest danger is psychological: it can give people the illusion they understand something when they don't, weakening judgment just as the technology becomes more embedded in our daily work and learning."* — Saul Perlmutter, UC Berkeley
- *"Students' mental and physical health decline due to excessive AI use, as evidenced by their impaired ability to learn independently and communicate verbally… AI tools have heightened anxiety, social withdrawal, and produced lower emotional intelligence among students."* — Cruz-Ocampo et al., 2025

> **On being the exception.** A predictable response to this material is that it describes other people. The instructor addressed this directly, and the point generalizes well beyond AI.
>
> Consider multitasking. Many controlled studies establish that humans perform worse when multitasking: take any population — doctoral students, eighth-graders, it does not matter — have them complete three tasks sequentially, measure accuracy and time, then have them complete three tasks concurrently. Performance is worse on every measure for roughly nine people in ten. And research subjects, shown their own data, will argue with it: *I was tired; test me tomorrow.*
>
> We are poor at accepting that statistics apply to us. If an effect appears in nine of ten people, the reasonable prior is that you are one of the nine. Assuming otherwise is not a strategy.

### 3.2.2 Cost to the Output

![Three ways searchbot prompting produces poor results.](assets/ch3-fig-04-searchbot-bad-results.png)

*Figure 3.4. Searchbot approach: bad results.*

**Hallucination.** Roughly 95% of humans believe themselves to be self-aware, yet only 10–15% will say *I don't know* when asked about something they do not know. Models inherit this behavior from the humans whose text trained them: they are built to produce an answer.

The instructor made a structural point about this that is easy to miss, and it is worth marking as his position rather than as settled fact: **on this account, hallucination is not a bug that better engineering will remove.** A model that reliably declined to answer when uncertain would not function as a language generator, because the weighting, context, and modeling operations that produce fluent text depend on always producing a next token. If that is right, the behavior will not go away, and the burden falls permanently on the user to understand it and adopt strategies for handling it.

Chapter 4 presents a related but distinguishable account from OpenAI's own research — that models are optimized to be good test-takers, and that guessing when uncertain improves measured performance. That framing treats the behavior as a consequence of an optimization target, and optimization targets can in principle be changed. The two accounts are not incompatible, but they differ in how permanent they imply the problem to be. **In either case, the user's obligation is identical**, and it is the subject of Chapter 4.

There is also a curious asymmetry in how humans receive it. Information from another person is routinely, and appropriately, treated as possibly wrong. The same information arriving on a screen after typing seems to acquire an unearned presumption of truth. It should not. It is no different from any other communication, and there is a substantial chance it is wrong.

**Bias.** Because the model is built to give you an answer, it will readily accept bias introduced in the prompt and answer accordingly. *Tell me why cats are best* produces reasons cats are best. The bias in the question becomes the shape of the answer.

**The unremarkable mean.** This is the least discussed and, for a student or early-career professional, potentially the most consequential.

A model is not answering your question. It is producing **what most people have said about that question**. The weights rise and fall according to how often associations appear in the training corpus. The output is, in a meaningful sense, the average of what has already been written.

Ask a broad, general question and you will receive the same answer everyone else receives. Even where the answer is correct, it carries no value, because it distinguishes nothing.

> **The team scenario.** You are one of five people on a team. The team leader poses a substantive question. Everyone returns to their desk and puts the question to a chatbot. Everyone comes back quickly, eager to have answered first, and everyone delivers substantially the same answer.
>
> Nobody has distinguished themselves and nobody has added value. This sounds harsh, but it describes how professional advancement actually works: value comes from contributing something that was not already available. Taking longer and returning with a genuinely novel, well-reasoned answer is the path that leads somewhere.

The general principle: unless a task is repetitive, mundane, and genuinely objective — *tell me which of these emails need a reply today; summarize my calendar for tomorrow* — the point of using these tools is not to save time. It is to **produce a better product**. Doing it well may take as long as, or longer than, doing it unaided. What justifies the effort is that the result is better than what could have been produced otherwise.

---

## 3.3 The Cyborg Approach

![Quotations from Donna Haraway and Vivienne Ming on human–machine hybridity.](assets/ch3-fig-05-cyborg-manifesto.png)

*Figure 3.5. A Cyborg Manifesto.*

The term **cyborg** here is used in the sense established by Donna Haraway in *A Cyborg Manifesto* (collected in *Simians, Cyborgs, and Women*), a foundational text in cultural studies and feminist science studies. It is not the sense used by the strand of Silicon Valley commentary in which "cyborg" names something to be feared; the usage here follows Vivienne Ming's, in which the hybrid is a liberating rather than a diminishing figure.

> *"The cyborg is resolutely committed to partiality, irony, intimacy, and perversity. It is oppositional, utopian, and completely without innocence."* — Donna Haraway
>
> *"It is not clear who makes and who is made in the relation between human and machine. It is not clear what is mind and what is body in machines that resolve into coding practices. Insofar as we know ourselves in both formal discourse (e.g., biology) and in daily practice (e.g., the home-work economy in the integrated circuit), we find ourselves to be cyborgs, hybrids, mosaics, chimeras."* — Donna Haraway
>
> *"The best human–AI collaboration isn't driven by more advanced large language models but by human traits such as curiosity, intellectual humility, perspective-taking, and the ability to reason under uncertainty."* — Vivienne Ming

**The operational definition.** In the cyborg mode, the AI is a tool that extends your thinking rather than replacing it. You are not asking the machine to think for you and return an answer. You are pushing your own reasoning, your own structure, and your own approach to the problem *into* the machine, and letting it execute against that structure.

This is not a new relationship between minds and tools. Before writing, knowledge had to be held in memory; oral tradition was the only transmission mechanism, and people memorized prodigiously. Print allowed cognition to be offloaded onto a physical object, which freed the brain for other work. Scholars of memory have documented what was lost in that transition, and it was real. The offloading was nonetheless, on balance, generative — because what was offloaded was storage, and what was retained was thinking.

The cyborg approach applies the same logic. Offload execution; retain the reasoning.

The consequence for output quality follows: **the same strategy that protects cognition also produces novel, interesting results rather than the unremarkable mean.**

---

## 3.4 The Three Levers of Prompt Engineering

![Format, context, and tuning.](assets/ch3-fig-06-elements-of-prompt-engineering.png)

*Figure 3.6. The elements of prompt engineering.*

Three properties of a prompt can be varied deliberately.

| Lever | Definition |
| --- | --- |
| **Format** | The structure and style of the prompt and of the desired output |
| **Context** | The background information and examples supplied, and — critically — where they are placed |
| **Tuning** | Narrowing the model's vast general capability toward the specific lane you care about |

*Table 3.2. The three levers.*

**A note on tuning and bias.** Tuning introduces bias. This is intentional and it is acceptable, because **conscious bias is categorically different from unconscious bias**. If I tune a model toward the technology sense of *apple*, or toward peer-reviewed scholarly publications after a given date, I have biased the output — but I know the bias, I have a reason for it, and I can state it when I present the work so that others can evaluate what I did. That is a defensible methodological choice. Unconscious bias, absorbed from a corpus and an interface, is not.

---

## 3.5 Format

![Three prompt formats: natural language, structured input-output pairs, and markdown.](assets/ch3-fig-07-format.png)

*Figure 3.7. Format options.*

Different models respond differently to different formats. Understanding what a model expects is essential to prompting it effectively.

**Natural language.** The default, and the format the interface invites. *Given that global temperatures have risen by 1 degree Celsius since the pre-industrial era, discuss the potential consequences for sea level rise.*

**Structured input–output pairs.** A compact and frequently superior format when the task fits it:

```
Input: "Cat"      Output: "A small furry mammal with whiskers."
Input: "Dog"      Output: "A domesticated canine known for its loyalty."
Input: "Elephant"
```

This will return a four- or five-word description. Compare with asking a chatbot to describe an elephant, which yields three paragraphs — and note that even explicit instructions to be concise are unreliable, because the instruction competes with the general pull toward verbose output. The structured format works better because the next-token machinery follows the established pattern. **The form of the example is itself an instruction, and a more effective one than a description of the form.**

**Markdown.** A more highly structured format, treated at length in Section 3.8.

```markdown
# System Prompt: Estate Planning Attorney
## Role
You are an estate planning professional who uses a formal but friendly tone in your client communications
## Audience
…
```

---

## 3.6 Context

> **Providing sufficient and appropriate context is the single most significant action a user can take to improve AI output.**

![The question "What is an apple?" without context.](assets/ch3-fig-08-context-apple-1.png)

*Figure 3.8. "What is an apple?" — ambiguous.*

![The same question with technology context.](assets/ch3-fig-09-context-apple-2.png)

*Figure 3.9. With context: "I am interested in technology."*

![The same question with botanical context.](assets/ch3-fig-10-context-apple-3.png)

*Figure 3.10. With context: "I am interested in plants."*

The mechanism was established in Chapter 1: the attention layers update each token's representation according to the tokens around it. Supplying context is therefore not a matter of politeness; it is direct manipulation of the vector arithmetic that produces the answer.

### 3.6.1 Position Matters

![Two prompts with identical content in different order.](assets/ch3-fig-11-word-order-matters.png)

*Figure 3.11. "I am interested in plants. What is an apple?" ≠ "What is an apple? I'm interested in plants."*

These two prompts contain identical words and are **not equivalent**. Recall the generation loop: when the model reaches the token *apple* in the second prompt, the botanical context has not yet been encountered, and the weighting proceeds accordingly.

**An important caveat, supplied by the instructor.** Model developers are aware of this problem and have invested in mitigating it. Contemporary models perform substantial bidirectional and multi-token processing, and in a short prompt like the example above the two orderings will often now produce similar output. This is a brute-force solution, and it does not scale: **across a long series of exchanges, it cannot compensate.** As the context window fills, early material is pushed out and ceases to inform generation. Ordering therefore remains a real lever, and the operative word throughout this section is **control**: *control your context.*

### 3.6.2 Chat History Is Context

![A multi-day chat history feeding into a new question.](assets/ch3-fig-12-chat-history-as-context.png)

*Figure 3.12. Chat history as context.*

Consider a sequence in a single conversation:

- *Monday:* "I'm writing a paper for my college class. Describe the fundamentals of networking." → an answer.
- *Monday:* "What effects do the operating systems of individual connected computers have?" → a good answer, because the model still has the networking framing.
- *Monday:* "What cost factors need to be considered?" → a good answer, because it knows the costs concern networked computers.

The paper is written and submitted. Then:

- *Tuesday:* "What is an apple?"

All of the preceding material is still attached. The user's mind has left the topic of computer networks; the context window has not. The answer will be shaped by a framing the user has forgotten supplying.

**Starting a new chat is an act of context control**, and it is one of the most useful habits to develop.

### 3.6.3 Context You Did Not Supply

Chat history is only the visible portion. Every major platform maintains a **user profile** — accumulated settings, preferences, and inferred characteristics — which is injected into the context without appearing in the interface.

This is a genuine problem for anyone whose interests are heterogeneous. A single person may ask a question as a data scientist, then ask a policy question, then ask something about sailing, then something about family. A profile assembled across all of these will steer answers in ways that are invisible and unrequested.

**The system is constantly supplying context you do not see and do not control. Effective prompting means taking that control back.**

---

## 3.7 Tuning and Prompt Types

![Programmatic tuning versus prompt-level tuning.](assets/ch3-fig-13-tuning.png)

*Figure 3.13. Tuning: at the programmatic level, or through the prompt.*

Models can be permanently tuned at the programmatic level — taking an existing model and adjusting its weights toward a domain. This requires resources and expertise beyond the scope of this book. The tuning available to every user is **biasing the model through the prompt**, and it is remarkably effective.

![Four types of prompts.](assets/ch3-fig-14-types-of-prompts.png)

*Figure 3.14. Types of prompts.*

| Type | Description |
| --- | --- |
| **Direct (zero-shot)** | A direct instruction or question with no additional context or examples |
| **Shot-based** | One or more examples of the desired input–output pairs before the actual prompt |
| **Chain of thought (CoT)** | Instructions that break complex reasoning into intermediate steps |
| **Shot-based chain of thought** | Examples to tune the model, followed by an explicit request for reasoning steps |

*Table 3.3. Prompt types.*

### 3.7.1 Direct (Zero-Shot) Prompting

![Zero-shot prompt examples.](assets/ch3-fig-15-zero-shot.png)

*Figure 3.15. Zero-shot prompting: most used, least effective.*

```
Translate the following sentence to French: 'I love cats'

What careers would be good for someone who loves to be outside
and also wants to make a lot of money?

Extract all company names from the attached document.
```

Zero-shot prompting is the most used and least effective strategy. It is not, however, always wrong. The careers example is a legitimate use: the question is exploratory, and the goal is not an exhaustive or authoritative list but a survey of a space. If some of the returned options are appealing, the next move is to narrow — which is where the other strategies enter.

### 3.7.2 One-, Few-, and Multi-Shot Prompting

![Single-shot, few-shot, and multi-shot examples.](assets/ch3-fig-16-shot-based.png)

*Figure 3.16. Shot-based prompting.*

**Single-shot** — one example:

```
Classify the sentiment of the following text as positive, negative, or neutral.
Text: 'The product is terrible.'  Sentiment: Negative
Text: 'I think the vacation was okay.'  Sentiment:
```

The single example establishes the output format and the label vocabulary. The model will likely determine that the second text is not negative; it has less to work with in choosing between neutral and positive.

**Few-shot** — several examples:

```
Classify the sentiment of the following text as positive, negative, or neutral.
Text: 'The product is terrible.'   Sentiment: Negative
Text: 'Super helpful, worth it.'   Sentiment: Positive
Text: 'It doesn't work!'           Sentiment:
```

**Multi-shot** — many examples. More examples improve results, up to roughly ten, and the ceiling is content-dependent. The instructor's candid note: the reasons for the plateau are theorized but not firmly established in the literature, and practitioners' experience is that gains fall off somewhere past half a dozen.

> **Ordering matters as well as quantity.** With three output classes, supply roughly two examples of each — and **interleave them** rather than grouping them. Positive, negative, neutral, positive, negative, neutral. Presenting all the negatives together and then all the positives establishes a pattern in the ordering itself, which is not the pattern you intended to teach.

### 3.7.3 Chain-of-Thought Prompting

![Chain-of-thought prompt examples.](assets/ch3-fig-17-chain-of-thought.png)

*Figure 3.17. Chain-of-thought prompting.*

Chain-of-thought prompting improves reasoning by decomposing a complex query into intermediate steps. Rather than requesting a direct answer, the prompt directs the model to work through a sequence, which increases accuracy in mathematical, logical, and commonsense tasks.

```
If all dogs are mammals and all mammals breathe, do all dogs breathe?
Think step-by-step.

I need to compare the population density of Tokyo and New York.
Break down the required steps to get this answer.

I need to compare the population density of Tokyo and New York.
Break down the required steps to get this answer. Then do the actual
Tokyo vs. New York comparison with current figures and cite data sources.
```

**Testing a chain-of-thought prompt.** Because output varies between runs, a decomposition prompt is worth running more than once: in several chat windows, or in a different tool so as to escape the accumulated context of the first. A stronger variant is to ask explicitly for **three different methodologies** for the problem and then evaluate them against one another. The evaluation is yours to perform, and performing it is the point.

**Chain of thought is where the cyborg approach becomes concrete.** In supplying the steps, you have done the reasoning and pushed it into the machine; the machine executes your plan. This is the difference between asking for an answer and directing an analysis, and it is the mechanism by which a novel result becomes possible.

An important distinction: asking a model to *report* its chain of thought is worth doing, but it is not the same operation. **Making your own chain of thought explicit** — *do this, then this, then this* — keeps your brain in control of the procedure.

> **A caveat that cannot be overstated: the reported reasoning is not a record of the computation.**
>
> When a model describes the steps by which it reached an answer, it has not introspected on its own processing. The answer was not derived by performing the steps it describes. Both the answer and the description of the method are generated the same way — by predicting likely next tokens. What you receive is a description of a methodology assembled from the way many other people have written about methodologies for problems of that kind. It may be an excellent description. It is not an audit trail.
>
> This matters because the reported chain of thought is increasingly treated as though it were verification. It is not, and treating it as such gets the architecture exactly backwards.

> **A cautionary case.** The instructors described a research paper, co-authored across the DataLab team, that was rejected twice — on both occasions because reviewers asked why the authors had analyzed the data by their stated method when they could simply have asked a chatbot. Told that a chatbot result could not be verified, one reviewer replied that you can ask the model for its reasoning, and then you would know.
>
> That response, in the instructor's assessment, completely betrays a misunderstanding of how these models work — and the misunderstanding is becoming endemic, including among people in a position to gatekeep published research.

---

## 3.8 Worked Example: From Natural Language to Structured Prompting

![A structured natural-language prompting sequence.](assets/ch3-fig-18-natural-language-prompt.png)

*Figure 3.18. A well-constructed natural language prompt: context, speaker and audience, controlled chain of thought, references.*

The instructor demonstrated a complete task first in natural language and then in structured markdown, producing equivalent results by both routes. The problem was real: a university development officer working in planned giving needed to advise a prospective donor. The sequence is worth following in detail, because it exhibits every principle in this chapter operating together.

### 3.8.1 The Natural Language Version

**Step 1 — Establish role and audience.** Define who the model is speaking as, and to whom. In the demonstration: an estate planning professional writing to a college-educated, financially successful retiree.

**Step 1a — Supply tone examples.** The prompt included a short set of shot-based style examples — *this would be a poor version, this would be better, this would be best* — to fix the register of the output. Shot-based prompting and chain-of-thought prompting are combined here, exactly as Section 3.7 describes.

**Step 2 — Supply constraints as context.** Client jurisdiction; net worth; annual income; stated goals (maximize return, minimize tax burden, maximize the net worth transferred to heirs). These constraints *are* the tuning.

**Step 3 — Request analysis with an explicit chain of thought and sources.** *Determine the best investment alternative to achieve these goals. Explain your reasoning step by step and cite sources.* The model returned three candidate strategies with a step-by-step breakdown and citations, several of which pointed to published IRS material.

**Step 4 — Verify before proceeding.** This is the critical step and the one most often skipped.

> **Why verification must precede the next prompt.** Once a wrong answer is in the context window, saying *that's wrong, give me a different answer* accomplishes less than users expect — the erroneous material remains in context and continues to shape everything downstream. **Verify at each step, before asking the next question.**

**Step 5 — Request quantitative detail.** With the reasoning validated, ask for the calculations: term and tax burden for each option, presented as a table.

**Step 6 — Verify again**, then request the deliverable: a comparison table suitable for a client, and a summary paragraph derived from the findings.

**Step 7 — Verify the deliverable independently.** In this case the recommendation — a charitable remainder trust — was, in fact, correct, and was confirmed by a certified financial planner who reviewed it. The gift was subsequently arranged on that basis. That confirmation is the reason the instructor could report the result as correct. Without it, there would have been an authoritative-looking document and no knowledge.

> **A practical aside on output formats.** The instructor initially requested a downloadable file and found it faster to request a plain paragraph for copying and pasting. These interface behaviors change frequently. Choose the output format deliberately — list, narrative, table, downloadable file — and revisit the choice as tools change.

### 3.8.2 The Markdown Prompting Framework

![The Markdown Prompting Framework.](assets/ch3-fig-19-markdown-prompting-framework.png)

*Figure 3.19. MPF: simple to learn, and prompts can be saved for reuse.*

The **Markdown Prompting Framework (MPF)** is emerging as an industry standard for structured prompting. Its virtues are that it is simple, that it is easy to learn, and that prompts can be saved and reused.

The instructor's more interesting claim concerns its effect on the user: **markdown forces you to structure your thinking before you ask.** That constraint is the point. It is what keeps the interaction in the creative, cyborg mode rather than the reflexive one.

Markdown requires only a few special characters, and a working prompt needs roughly three. The prompt below reconstructs the structure of the demonstration; the specific client figures are illustrative.

```markdown
# System Prompt: Estate Planning Professional

## Role
You are an estate planning professional who uses a formal but friendly
tone in client communications.

## Audience
A college-educated, financially successful retiree.

## Constraints
* jurisdiction: United States
* net_worth: $1.5M
* annual_income: [client's annual income]
* objectives: maximize return; minimize tax burden; maximize transfer to heirs

## Tasks
1. Determine the best investment alternatives to achieve these goals.
2. Explain your reasoning step by step and cite sources.
3. Calculate the term and tax burden for each alternative; present as a table.
4. Produce a client-ready comparison table.
5. Write a summary paragraph suitable for an email.
```

The components:

- **`#` — the system prompt.** All major chat interfaces treat a top-level heading as a system-level instruction. This is where you tell the model what it is — *you are a financial professional* — in an attempt to steer it away from what it has inferred about you from your profile and settings. It does not overwrite the platform's own system context; the two coexist and interact. But it gives you a lever on material you otherwise cannot touch.
- **`## Role` and `## Audience`.** Standard sections that reduce ambiguity substantially.
- **`## Constraints`.** The tuning. Constraint names are not a controlled vocabulary — `jurisdiction` is used here because it is the operative legal term in the United States, and the model interprets it as natural language. This section is where you must actually think about your problem: what is it, what is in scope, how does this need to be narrowed.
- **`## Tasks`.** A numbered list. **This is the chain of thought made structural.** The model executes step one, then step two, and so on. It performs the same work that was distributed across several turns in the natural language version, with the sequence specified in advance.

Run this way, the markdown prompt produced the same results as the multi-turn natural language session — minor textual variation, identical data, identical conclusions.

### 3.8.3 Using Structured Prompts in Practice

An MPF prompt is a plain text file. It can be written in any text editor and saved. There are then two ways to use it: **drag the file into the prompt window**, or **copy and paste its contents**. Both work in essentially every major chat interface.

The value of a file is reuse.

> **For coursework.** At the start of each term, create one markdown file per course containing the syllabus, the course context, and the relevant framing. As readings are assigned, add them. Before working on anything for that course, start a new chat and drag in that file, which fully establishes the context before the first question.
>
> The instructor was explicit about the boundary: **this applies only where the use of AI is permitted.** Where a course prohibits AI, it is prohibited, and no technique changes that. Where it is permitted, this is among the best available uses.

> **For work.** Every job comprises multiple roles and recurring tasks. Build a prepared prompt for each recurring task.
>
> Expect to spend a couple of weeks tuning it. You will discover where results fail validation, where the model drifts out of the intended lane, where the output length is wrong — and you will add constraints accordingly. Over time you accumulate purpose-built context for your work. **And you must still validate every result.**

**Shared prompt libraries.** GitHub — the platform on which developers share code, and on which enormous quantities of open-source software are published freely — now hosts communities that share markdown prompts. Large curated repositories exist, some assembled from thousands of contributors, organized by profession and task. A user who is comfortable doing so can retrieve pre-built context and, in the open-source spirit, contribute improvements back.

> **A professional note from the instructor.** Learning the Markdown Prompting Framework is not difficult and it makes a visible difference. Employers are increasingly asking candidates how they use AI. A candidate who can describe structured prompting and context control is answering a question that most candidates cannot.

---

## 3.9 The Do and Don't Lists

### 3.9.1 Do

![The prompting "do" list.](assets/ch3-fig-20-prompting-dos.png)

*Figure 3.20. Prompting "do" list.*

| Practice | Rationale |
| --- | --- |
| **Define the speaker** | Establishes the role the model should adopt and displaces inferred profile context |
| **Define the audience** | Determines register, depth, and vocabulary |
| **Provide other relevant context** | The single highest-leverage action available |
| **Consider and define input and output format** | Decide before prompting: list, narrative, table, file |
| **Make chain of thought explicit** | *Do this, then this, then this* — your plan, your control |
| **Ask for references** | They may be hallucinated and often will be, but they give you places to start. Knowing this, they remain useful as leads, never as citations |
| **Be precise** | See below |
| **Provide examples** | Examples of the desired output consistently improve results |

*Table 3.4. Prompting practices to adopt.*

> **On precision versus verbosity.** More words in a prompt is not more context. This is a place where models behave much as human speech does.
>
> The instructor's illustration: *I love you* is more powerful than *I love you so much.* Adjectives are excellent descriptors, but they dilute, because each adjective applies to an enormous range of things. *Beautiful* applies to people, rabbits, cats, dogs, and mountains.
>
> Recall the mechanism. A verbose prompt full of general modifiers introduces tokens with associations to thousands of unrelated concepts, which spreads the model's attention and **undoes your tuning.** You leave the lane you worked to establish.
>
> **Be precise. Do not be verbose.** As a secondary benefit, it costs less when running against a paid programming interface.

### 3.9.2 Don't

![The prompting "don't" list.](assets/ch3-fig-21-prompting-donts.png)

*Figure 3.21. Prompting "don't" list.*

**Don't think of it as a search engine.** If the question is a search engine question, use a search engine. (The instructor noted this advice with some hesitation, since search platforms are themselves increasingly returning AI summaries by default — which he characterized as a significant loss, because the ability to look through a range of sources and judge them yourself is precisely the capacity at issue in Chapter 4.)

**Don't introduce your own bias by asking leading questions.** Introduce bias *consciously*, through framing and tuning, where you can name it and defend it — never accidentally, through the shape of the question.

**Don't get average answers by asking vague questions.** Use chain of thought. Write down your reasoning. Do the thinking.

**Don't include information you wouldn't want made public.** Once submitted, the data has left your control.

> The instructor, who has worked on internet technologies since the internet's early years, offered a hard-won position: institutional agreements stating that prompts are not retained have been made by many organizations about many kinds of data, and there eventually comes a point at which a breach is disclosed and it emerges that the data existed somewhere unanticipated, retained for some ancillary purpose. What it was retained *for* is of no consequence to the person whose data it was. At minimum, the content traversed the internet. **Unless you want it public, do not submit it.**

**Don't trust the answer.** This is the subject of Chapter 4.

---

## 3.10 Talking to the Right AI

![Ollama and Hugging Face.](assets/ch3-fig-22-open-tools-and-models.png)

*Figure 3.22. Open tools and open models.*

A qualification before the recommendation. Because the major commercial models were trained on approximately the same material — essentially the whole scrapeable internet — they are more similar to one another than marketing suggests. Real differences exist, and they lie substantially in the surrounding logic: the safety filters, the context engineering, the interface, the tokenization and retrieval choices. Practitioners do develop preferences by task. But the underlying models are far more alike than different.

The more consequential choice is between running someone else's model on someone else's hardware and running your own.

**Ollama** (<https://ollama.com/>) runs on Windows, macOS, and Linux, requires administrator privileges and no programming ability, and starts a local large language model environment on your own machine. You select which model to run. At the time of the workshop the instructor's recommendation was **Qwen**, which he judged the strongest open model then available for general natural-language work.

**Hugging Face** (<https://huggingface.co/>) hosts thousands of specialized open-source models built for particular disciplines — law, medicine, and narrower subfields still. A great many of these can be loaded into a local runtime.

The combination is powerful. You can run a model locally, with nothing leaving your laptop, that was trained specifically on scholarly literature in your field. For privacy-sensitive work this resolves the confidentiality problem outright, and for domain-specific work it substantially improves the odds of a useful answer.

> **A caution.** Treat a model repository as you would any online repository. That a model is available does not mean it is correct, well-built, or appropriate for your use case. These are artifacts contributed by people who wished to share them, and the platform validates format rather than quality. Apply the FACT framework from Chapter 2 and determine whether the model actually fits your purpose.

---

## 3.11 Questions from the Session

Three exchanges from the discussion period bear directly on practice.

### 3.11.1 Should you use an AI tool to write your prompts?

The question arises constantly, and the honest answer is that it works — a model will produce a serviceable markdown prompt, and that is a reasonable starting point which you then edit.

**But you should not do it while you are learning.** The reason returns to the argument of this entire chapter: the value of the Markdown Prompting Framework is that it forces you to think about what you are doing — *why do I want this, what are the bounds, what are the constraints, what do I actually need?* Delegating that step removes precisely the part that was valuable.

The analogy offered was translation. We have translators for all sorts of things: between human languages, between programming languages. Something is always lost in translation. If you have done the work yourself, you know where the losses tend to occur and what to check for. If you have not, you cannot see them.

The instructors' recommendation: **write your own prompts until you know your space well enough to know what to check.** Once you genuinely know the domain and the tool, delegation becomes a defensible efficiency.

### 3.11.2 Chained models and orchestration

An increasingly common architecture has one model's output feed the construction of the next model's prompt, with a coordinating system driving the sequence. This is the mechanism underlying much of what is marketed as agentic AI, and it is improving as more structured prompting conventions enter the training data. Early models handled markdown poorly precisely because markdown was not well represented in their corpora; that has changed.

The implication for the reader is not that they must build such systems. It is that the skill of specifying a task precisely, in structured form, is the same skill whether the recipient is a model, a chain of models, or a colleague.

### 3.11.3 What employers say they want

An external advisory panel of industry, government, and technology-sector participants convened by the workshop organizers was asked what capabilities graduates need. Their list contained almost nothing technical:

- **Critical thinking**
- **Problem solving**
- **Resilience**
- **Communication** — oral and written, and specifically the ability to communicate and coordinate across teams comprising both humans and AI systems

The panel resisted describing this last capability as management, settling instead on **orchestration**: the coordination of activity across human collaborators and machine systems. Their assessment was that regardless of sector, and regardless of whether a role is technical, work is now technology-driven enough that everyone will operate in mixed human–machine teams — and that many people already do without having confronted the fact explicitly.

The convergence with this chapter is not coincidental. Chain-of-thought prompting, context control, structured specification, and the discipline of validating results are orchestration skills. They are also, as Section 3.2 argued, the practices that keep the human capable of doing the work.

---

## Chapter Summary

- Seventy percent of users treat AI as a search engine; twenty percent use it to confirm their existing beliefs; ten percent collaborate with it. Only the last produces good results.
- Reflexive AI use measurably degrades cognitive capacity, by the same mechanism through which navigation software degraded spatial reasoning. Assume the statistics apply to you.
- Searchbot prompting fails in three ways: hallucination, which is architectural rather than fixable; inherited bias from leading questions; and the unremarkable mean — the average of what has already been said, which distinguishes nothing.
- The cyborg approach pushes your own reasoning into the tool rather than outsourcing the reasoning itself.
- Three levers: format, context, and tuning. Tuning introduces bias deliberately, which is defensible precisely because it can be named.
- Context is the highest-leverage variable, and its *position* matters. Chat history and platform profiles inject context you did not supply and cannot see. Starting a new chat is an act of control.
- Prompt types run from zero-shot through shot-based to chain of thought. Explicit chain of thought is where cyborg practice becomes concrete.
- Verify at every step, because a wrong answer left in context contaminates everything after it.
- The Markdown Prompting Framework provides system prompt, role, audience, constraints, and a numbered task list; it makes prompts reusable and forces the user to think before asking.
- Be precise, not verbose: general modifiers dilute tuning by importing broad associations.
- Local runtimes and specialized open models resolve the confidentiality problem and often improve domain accuracy.

## Key Terms

**prompt** · **prompt engineering** · **searchbot approach** · **cyborg approach** · **cognitive debt** · **unremarkable mean** · **format** · **context** · **tuning** · **context window** · **system prompt** · **zero-shot prompting** · **one-shot / few-shot / multi-shot prompting** · **chain of thought (CoT)** · **Markdown Prompting Framework (MPF)** · **constraints** · **conscious bias** · **local model** · **open model**

## Review Questions

1. Distinguish the searchbot approach from the cyborg approach in terms of *where the reasoning happens*. Why does the distinction have consequences for cognition as well as for output quality?
2. Why does the instructor argue that hallucination cannot be engineered away? Reconstruct the argument from Chapter 1's account of generation.
3. Explain the unremarkable mean, and describe a professional situation in which producing it would be actively harmful to your interests.
4. "I am interested in plants. What is an apple?" and "What is an apple? I'm interested in plants." Explain why these differ, and explain the caveat regarding contemporary models.
5. A user has spent a week discussing a networking assignment with a chatbot and now asks an unrelated question in the same conversation. What will happen and why? What should they have done?
6. Rewrite a vague prompt of your own devising into a chain-of-thought prompt with explicit steps. Identify which step in your sequence requires verification before proceeding.
7. Construct an MPF prompt for a task you perform regularly. Identify the system prompt, role, audience, constraints, and task list, and state which constraint does the most tuning work.
8. Why does adding descriptive adjectives to a prompt tend to *degrade* results? Answer in terms of embeddings and attention.
9. Under what circumstances would a locally-run specialized open model be preferable to a commercial chatbot, and what new obligations does that choice create?

## Further Reading

- Haraway, D. (1985). A Cyborg Manifesto. In *Simians, Cyborgs, and Women: The Reinvention of Nature* (1991). Routledge.
- Ming, V. — work on human–AI collaboration; source of the searchbot/cyborg engagement framework and the usage statistics in Table 3.1.
- Cruz-Ocampo, et al. (2025). Student-reported cognitive effects of artificial intelligence use.
- Markdown Prompting Framework overview: <https://tenacity.io/snippets/supercharge-ai-prompts-with-markdown-for-better-results/>
- Ollama (local model runtime): <https://ollama.com/>
- Hugging Face (open model repository): <https://huggingface.co/>
