# Chapter 2. How to Use AI Responsibly

> *Session 2 of the AI Literacy and Logic workshop. Lead instructor: Dr. Pamela Reynolds, Associate Director, UC Davis DataLab.*

## Learning Objectives

Upon completing this chapter, the reader should be able to:

1. Classify the principal objections to generative AI use into reliability, ethical and legal, and resource categories.
2. Define *ethics* as the systematic study of what is good or right, and distinguish the ethicist's question from the engineer's.
3. Articulate a personal and professional value set and translate it into concrete constraints on AI use.
4. Identify the stages of the AI development pipeline at which bias enters, and explain why bias is a design consequence rather than a malfunction.
5. Explain why an AI system cannot cite sources in the sense in which a scholar cites sources, and rank model types by citation reliability.
6. Describe the material infrastructure of "the cloud" and quantify, with appropriate caveats, the energy and water costs of training and inference.
7. Apply the AI Use Roadmap and the FACT framework to a specific decision about whether to use an AI tool.
8. Select non-AI alternatives appropriate to a given task, and select the appropriate AI tool where an AI tool is warranted.

## Framing

Chapter 1 addressed *how* generative AI tools work. This chapter addresses *whether* they should be used, and if so, when and where.

It is easy to treat AI as a magic wand: a prompt is written, a button is pressed, a result appears. But every press of the enter key engages a global network of data, energy, and human labor. Work — in the physical sense of energy expended, and in the economic sense of labor performed — is being outsourced to somewhere else.

The purpose of this chapter is not to tell the reader to stop using AI, nor to tell the reader to use it. That judgment is individual and contextual. The purpose is to place the reader in the driver's seat rather than in the passenger seat of an algorithm someone else built, since all technology traces back to the people who built it.

The chapter therefore has a specific target: **skepticism in the true sense of the word** — the capacity to think critically enough to examine one's own use. Readers may well find themselves in workplaces where these tools are expected. Some of those expectations will have been set by people unfamiliar with the tools' actual capabilities and limitations. Being able to identify where the value lies, and where the pitfalls lie, is a professional asset rather than an obstruction.

---

## 2.1 The Landscape of Objections

![Issues of concern for responsible AI use.](assets/ch2-fig-01-issues-of-concern.png)

*Figure 2.1. Ongoing ethical, legal, and environmental concerns surrounding AI use.*

The most common objections to generative AI use fall into three families: the reliability of the technology, its ethical and legal implications, and its resource costs.

### 2.1.1 Veracity

The most persistent critique is that large language models are stochastic text predictors rather than reasoning engines. A phrase in common use is that they are **"reliably unreliable."** The specific failure modes are hallucination, an absence of pragmatics, and a tendency to parrot rather than to apply logic. Accuracy and reproducibility both suffer, and reproducibility matters: a result that cannot be obtained consistently cannot serve as the foundation of a project.

### 2.1.2 Intellectual Property and Privacy

**Copyright infringement.** Large language models have been called *plagiarism machines*: they ingest enormous quantities of material and reproduce patterns from it without attribution or compensation. High-profile litigation — *The New York Times v. OpenAI* among others — turns on whether training on copyrighted material constitutes fair use or data theft. The legal position is actively evolving.

**Data sovereignty.** Models have been trained on personal, sensitive, and child-related data scraped from social media without consent. A photograph posted years ago for family and friends was not offered for ingestion into a commercial model.

**Synthetic likeness.** The "No FAKES" concern addresses the synthesis of human likenesses and voices without authorization. Asking a model for a sonnet in the style of Shakespeare raises modest concerns; generating a video statement that appears to come from a head of state raises very different ones, both for individual sovereignty over one's own likeness and for the integrity of public discourse.

### 2.1.3 Resource Costs

Energy consumption, water use, and capital centralization are treated at length in Section 2.5. Two figures belong here. The AI industry's energy footprint now rivals that of mid-sized nations. And on capital centralization: the infrastructure required to train and serve these models is so expensive that ownership concentrates among the wealthiest firms and individuals. Projected capital expenditure by large technology companies was placed at **more than $700 billion in 2026**, and at the time of the workshop none of the major AI companies was profitable.

### 2.1.4 Safety and Liability

As systems move from chatbots toward **agents** capable of executing code, making purchases, and taking consequential actions without a human in the loop at each step, the security objections intensify.

**Prompt injection and logic abuse.** An attacker can manipulate a model's instructions to bypass its safety protocols. In agentic settings, where one AI system communicates with another and takes actions autonomously, the attack surface expands considerably.

**Agency law.** If an AI agent commits a binding legal error, liability is unresolved. The developer? The user? The company that deployed it? Legislation has not caught up, in part because the technology is poorly understood by legislators and in part because context matters greatly to any sensible rule. The analogous problem in autonomous vehicles has been open for years without satisfactory resolution.

### 2.1.5 Socio-economic Impacts

**Algorithmic bias.** Models inherit and amplify prejudices present in their training data, producing effects that have been described as digital redlining in hiring, lending, and healthcare. Section 2.4 treats this in detail.

**Deskilling.** Over-reliance is argued to degrade critical thinking, writing, and creativity. Chapter 3 examines the evidence.

**Displacement of work.** Concern that AI will eliminate jobs is longstanding in form — anxieties about the future of work date to the industrial revolution and have never abated — but the more precise observation is that traditional roles will change as these tools absorb particular tasks. A frequently offered formulation is that AI is less likely to take a job than a person using AI is.

### 2.1.6 Human Wellbeing

Evidence is accumulating that intensive use of these systems can contribute to declining mental health, and litigation is developing around cases in which individuals engaged deeply with these systems and were led by model output toward actions that harmed them. This is an area of active research rather than settled knowledge, but it belongs on the list.

---

## 2.2 Ethics as a Working Method

**Ethics is the systematic study of what is good or right.**

The word tends to summon philosophy — Aristotle, Kant, Nietzsche, Singer — and to feel remote from technical practice. It should not. The distinction that makes ethics operational is simple:

> An engineer or scientist asks about the capability of a tool: *Can we build or use this?*
>
> The ethicist asks: *Should we build or use this?*

It is convenient to decouple these questions and assign the second to somebody else. That convenience is unavailable here, because humans build these tools and humans use them, and so it falls to humans to decide whether doing so is right.

Ethics is not a list of prohibitions. It embodies what we value, individually and socially. Do we value speed over accuracy? Sometimes; and sometimes that trade carries an enormous cost. Do we value profit over privacy? Some organizations will say yes without hesitation — and the difficult cases are not the obvious ones. Consider a proposal to release the complete genome of an individual with a rare cancer so that more research teams can work toward a cure. The most private information a person possesses would be disclosed; the purpose is unambiguously good. Cases of this shape are why a worked-out sense of one's own values is useful rather than ornamental.

Ethics is also the framework used to navigate the gray areas where the law has not caught up. In the domain of AI, that is nearly everywhere.

**A crucial reframing:** when this book discusses AI ethics, it is not discussing robots becoming sentient and what to do about them. It is discussing **the values that are programmed into artificial intelligence tools**.

> **Every AI tool reflects the values of the people who funded it and the developers who built it. As users, when we choose an AI tool, we are participating in those values.**

Taking an ethical approach to AI therefore means asking, continually: *Does this tool's version of "good" match mine? Does using this tool align with my values?*

### 2.2.1 Understanding Your Own Values

Individual values are an internal compass — integrity, curiosity, privacy, ambition, autonomy, community. Social values are inherited: the "social contract" agreed upon within a community, profession, or institution. Justice, sustainability, democracy, and transparency are common examples. Members of UC Davis have already agreed to the values in the Principles of Community; students in a course have agreed to the values expressed in that course's syllabus, whether or not they read them closely.

> **Exercise 2.1 — Name your value.** Consider your major and the careers that interest you. Identify **one core professional value** that draws you to that field or that the field embodies. Truth? Safety? Human agency? Sustainability? Autonomy? Community? Then find a partner and exchange, in thirty seconds each, your field and your value.
>
> In the live workshop, this exercise reliably produced two findings. Some pairs discovered they had chosen the same or closely related values; others found their answers entirely unrelated. Both outcomes are informative. In a workplace, values will differ from those of teammates, supervisors, and the organization — and that is normal. Navigating it requires first knowing what is important to you, and second being able to distinguish a disagreement rooted in genuinely incompatible values from one rooted in minor differences or in simple misunderstanding.

**Ethics means putting your values into action.** The translation is direct:

- If you value **honesty**, your ethical stance involves clear disclosure. You tell your professor or your supervisor that a first draft was AI-generated — regardless of whether disclosure was required, on the same principle by which you would credit a peer who helped.
- If you value **equity**, your stance involves interrogating the bias present in the tool and in its output before you report results.
- If you value **sustainability**, your stance involves minimalism: not deploying a large generative model for a task a search engine or a calculator would perform better.
- If you value **privacy**, your stance involves a firm rule about what you will and will not place into a system you do not control.

Responsible use will therefore look slightly different for every person. One reason is that values clash — with each other, with social norms, with an employer's priorities. Efficiency against accuracy: do you use a fast, hallucination-prone tool to meet a deadline, or take the slow route for verified accuracy? Innovation against privacy: do you feed a model sensitive data to improve it, or protect the individual at the cost of progress? A tool may save ten minutes and cost a marginalized community its privacy or its job security.

**Responsible use is the act of consciously deciding which value matters most in a specific context.**

---

## 2.3 Where Bias Comes From

Bias enters at every stage of AI development. Its primary source, however, is at the beginning: data collection.

### 2.3.1 The Corpus

![The corpus as a collection of content scraped from the internet.](assets/ch2-fig-02-the-corpus.png)

*Figure 2.2. "Garbage in, garbage out."*

A large language model can be pictured as a giant sponge that has soaked up most of the internet. The resulting body of content is the **corpus**, and it is assembled largely by web crawling — the Common Crawl, a periodic large-scale snapshot of the public web, being the canonical mechanism for approximating "the whole internet." Books, media, Reddit, and considerably less reputable forums are all in there.

A striking consequence, raised in the first session: the companies themselves may not have a complete account of what is in their corpora. Reading through the material would take centuries of human effort, and the ingestion is automated. Some of the vagueness in public statements about training data is evasion; some of it is that nobody knows.

The internet is not a neutral place, and four distortions follow.

**What is present but should not be.** Copyright-protected work, private conversations, and a great deal of toxic content. The corpus contains everything from rigorous published research to conspiracy theories and conjecture, and the model does not distinguish among them by kind.

**What is absent.** Material behind journal paywalls and institutional firewalls does not enter the corpus. This disproportionately excludes recent, peer-reviewed, methodologically careful research — precisely the material one would most want a model to have. Meanwhile every blog post and social media message from every non-expert is included. The corpus is therefore simultaneously out of date and factually unreliable.

**What is over-represented.** Consider how much is written online about the White House, the United States, or the United Kingdom. Now consider a small rural village. Perhaps an anthropologist wrote a book; that is one item. The corpus is biased toward famous people, famous events, and Western societies. This is not malice; it is what exists. But it means model output will systematically reflect that perspective.

**What is added by annotation.** Training data is labeled, often by human annotators whose interpretations of the same material differ. Those interpretations are shaped by cultural and personal bias, including implicit bias. The guardrails that determine which topics are dangerous are likewise human-curated, and what one curator judges dangerous another does not.

The governing maxim is **garbage in, garbage out**. If a topic is not adequately represented in the corpus, no amount of prompting will retrieve it — there is nothing to retrieve. And if the corpus is biased, the output will be biased, arriving as high-quality, polished, confident bias.

### 2.3.2 Bias Across the Development Pipeline

![Bias occurring at each of five stages of AI development.](assets/ch2-fig-03-bias-throughout-ai-development.png)

*Figure 2.3. Bias occurs throughout AI development.*

| Stage | Bias mechanisms |
| --- | --- |
| **1. Project definition & data sourcing** | *Framing* (how the problem is defined); *selection* (non-representative data); *historical* (societal inequities embedded in the record) |
| **2. Data preprocessing & annotation** | *Annotation* (subjective labeling); *feature* (proxies for sensitive attributes) |
| **3. Model development & training** | *Algorithmic* (choice of objective function); *experimenter* (assumptions of the researchers); *optimization* (overfitting to majority groups) |
| **4. Evaluation & validation** | *Evaluation* (non-representative test data); *metrics* (focus on overall accuracy, ignoring subgroups and intersectionality) |
| **5. Deployment & monitoring** | *Feedback loop* (predictions reinforce themselves); *concept drift* (model decay); *usage* (misuse of the system) |

*Table 2.1. Points of bias entry across the development pipeline.*

The essential insight is this: **these biases are not glitches.** AI is a socio-technical system that reflects the biases, priorities, and blind spots of the people who built it and the data they fed it. The systems are working exactly as designed, and that is why they are biased.

### 2.3.3 Three Cases

**Facial recognition (Buolamwini & Gebru; *Coded Bias*).** Researcher Joy Buolamwini, a Black woman, found that commercial facial recognition systems did not work well on her face. Her research demonstrated that these systems performed best on lighter-skinned men and worst on darker-skinned women. The cause was not developer animus; it was the available training data. The developers used their own faces and images of celebrities scraped from the web — predominantly white men. The algorithm became excellent at detecting the faces it had seen. The problem is structurally identical to the classic cats-versus-dogs image classification task: a model trained only on cats and dogs performs badly when shown a rabbit.

**Amazon's résumé screening tool.** Facing a volume of applications that human reviewers could not process, Amazon built a programmatic screening system intended to evaluate candidates more equitably. To learn what a good résumé looked like, the model was trained on the application materials of people the company had already hired. Because the existing engineering staff was demographically skewed toward white men, the model learned to prioritize applicants of that race and gender rather than on skills or qualifications. Amazon abandoned the tool — a good outcome, and one that required someone to look. The system did not merely violate the company's values; it failed to meet its own stated objective of identifying the most qualified candidates.

**Name-based ranking (University of Washington, 2024).** Researchers presented three mainstream large language models, including ChatGPT, with lists of job applicants identified only by name, and asked the models to rank them. Under any defensible value system, a name should not predict job performance; absent bias, the output should have been effectively random. Every platform ranked applicants by perceived race and gender.

**Search engines themselves.** The pattern is not confined to purpose-built classifiers. Safiya Umoja Noble's *Algorithms of Oppression* documents how ordinary search engines — tools most people would not think to interrogate — have been found to reinforce racism through what they surface and how they rank it.

The general lesson: **if you ask these models to do something, they will do it, even when the request makes no sense — and the result will be informed by the biases in the corpus.** Used blindly, AI reinforces the status quo of the past rather than the fairness of the future.

Two practical conclusions follow, and both were stated explicitly in the session.

**Ask who is left out.** When using a tool — or, for readers who go on to build one — the operative question is *who is excluded here, and why?* Sometimes the exclusion is intentional; far more often it is a consequence of what data happened to be available. The effect on the excluded group is the same either way.

**This is the argument for diversifying technology.** A development team whose members bring different perspectives, backgrounds, and blind spots is more likely to notice an absence before it is trained into a product. The Amazon and facial recognition cases are not stories about malicious developers; they are stories about homogeneous ones.

---

## 2.4 Veracity: Probability Is Not Truth

![Statistical probability does not equal truth.](assets/ch2-fig-04-probability-is-not-truth.png)

*Figure 2.4. AI does not "know" things; for AI, truth does not exist.*

Most readers have encountered an AI response that was ridiculous — and delivered with complete confidence. That confidence is not a consequence of the biases described above. It is a consequence of the mathematics described in Chapter 1.

**AI does not "know" things. For an AI system, truth does not exist.** Outputs are generated by probability. The model predicts tokens. It does not understand truth; it reproduces patterns.

> **Demonstration: the cows at Shield Library.** The instructor generated an image showing cows loose in front of Shield Library on the UC Davis campus, complete with convincing detail down to manure on the ground. Asked whether it was real, the room was divided, and several plausible explanations were volunteered — the campus dairy is nearby, the animals are ordinarily contained but do occasionally escape, and so on.
>
> The image was synthetic. The point of the demonstration is not that the image was persuasive but that the scenario was *probable*. Cows could escape; they could reach the library; the result would look approximately like this. The model produced something entirely plausible and entirely false, and plausibility is exactly what its architecture optimizes for. The right instinct — and the one participants displayed — is to ask verifying questions: *How often do the cattle actually get out? Would this have been reported?*

The professional implication is direct. A graduate's role is not merely to use AI, but to be the **truth auditor**. If the human in the loop does not perform verification, the human in the loop is not adding anything, and the question of why an employer would pay for that role answers itself.

### 2.4.1 "AI Cites Its Sources": False

![Model types ranked by citation reliability.](assets/ch2-fig-05-does-ai-cite-sources.png)

*Figure 2.5. AI suggests sources related to your topic, which you must then read and verify.*

This is the trickiest of the common misconceptions, because output containing links and formatted references certainly *looks* like citation.

**What citation means.** To cite a source is to assert a relationship between a claim and a document: *I consulted this source, and it supports what I have said.* That is not what happens when a language model produces a reference.

**What actually happens.** Asked for a citation, a model will frequently produce one that looks perfectly real. It is not attempting deception; it is doing exactly what it was built to do — computing which words usually go together and formatting them to look like the thing that was requested. The result is generated probabilistically through next-token prediction, exactly as any other text is.

The model has **parametric memory**: information is blended into its parameters, and the model does not retain the specific article, book, or website from which any particular fact came. The analogy offered in the lecture is apt — imagine reading a thousand books, then being asked about a topic and naming the titles that seem related. Those titles are *probably* relevant. That is a different claim from *this specific fact came from this specific book*.

**Retrieval-augmented generation (RAG) improves matters without solving the problem.** In RAG, retrieved documents are added to the context window before generation. The cited source is therefore more likely to be real. But it still does not follow that the specific citation was consulted for the specific claim, or that the claim was extracted from that source.

**Why this is worse than fake citations.** A fabricated citation fails a basic existence check. A citation that is entirely real — real title, real journal, real authors — but that does not support the claim attached to it will pass that check and fail only under scrutiny. Detecting this requires either already knowing the source or being willing to read it. **A response containing sources is not a verification; it is one more thing to verify.** This can still be useful: a new potential source has been surfaced. It has not been read.

| Model type | How it works | Citation reliability |
| --- | --- | --- |
| **Base LLM** | Relies entirely on internal model weights | None |
| **Search-grounded LLM** (Copilot, Perplexity, Gemini with Search) | Includes live web results and synthesizes them | Low |
| **Enterprise RAG** (custom, domain-specific systems) | Searches a human-curated database of documents | Moderate |

*Table 2.2. Citation reliability by model type. No row reads "high."*

**Bottom line: never take an AI's word as truth. Treat AI as a brainstormer, not an encyclopedia.** Model outputs are claims that require evidence, not facts that supply it.

### 2.4.2 Language Models Are Not Logic Models

A related failure follows from the same source. Asked what two plus two is, a language model returns *four* — not because it computed a sum, but because those tokens co-occur overwhelmingly in the training data. Asked how many times the letter *r* appears in *strawberry*, models have historically failed, because they are not counting; they are estimating the probability of a particular number appearing next to words of that shape.

> **If you need mathematics or logic, use a tool built on logic.** A calculator. A statistical package. A programming language. Using a probabilistic language model for a deterministic task is a category error, and one that is committed constantly.

---

## 2.5 Technology Has Social and Environmental Costs

### 2.5.1 Ghost Work

![AI is not neutral software.](assets/ch2-fig-06-social-costs.png)

*Figure 2.6. AI is not neutral software. If we treat AI results as objective truth, we risk automating past injustices.*

AI feels like neutral software. It is built on the labor of millions of **ghost workers** — people, many in the Global South, who tag data and filter toxic content, populating the safety and responsibility filter described in Chapter 1, frequently at very low wages.

Access to these tools is a privilege, and the efficiency they afford is subsidized by precarious, invisible labor. The formulation offered in the lecture is worth sitting with: when we outsource our thinking to AI, we are also outsourcing it to these invisible laborers.

### 2.5.2 The Cloud Is Made of Metal, Water, and Electricity

![Data center energy and water requirements.](assets/ch2-fig-07-data-center-energy-water.png)

*Figure 2.7. A data center in New Albany, Ohio.*

Most people picture AI as happening in "the cloud," which sounds weightless. The cloud is a network of large, hot buildings filled with racks of servers.

The mechanism is easy to feel by analogy. A personal computer running a demanding task for a few hours becomes noticeably warm. A data center is that computer's processing units stacked in rows, thousands over. The heat must go somewhere, and water is an excellent coolant — clean water, because the cooling systems require it. Every cloud operation therefore consumes energy, space, and water somewhere real.

| Resource | Figure |
| --- | --- |
| **Energy** | Data centers accounted for **4.4% of annual U.S. electricity use in 2023**, projected to reach **12% by 2028** |
| **Water** | One medium-sized data center consumes roughly **110 million gallons per year**. The AI industry is projected to use approximately **1.7 trillion gallons of freshwater annually by 2027** — more than the total water use of the country of Denmark |

*Table 2.3. Data center resource requirements.*

Twelve percent of all U.S. electricity is a figure worth pausing on, because that energy is not created for the purpose; it is diverted from other uses.

> **A local consequence.** Residents in the Lake Tahoe region were notified that their power company would no longer service the area, because a new data center in Nevada had contracted for the supply. Tahoe has affluent residents who will litigate and negotiate. Smaller and more rural communities facing the same displacement generally do not have those resources.

### 2.5.3 The Cost of Training

![The training footprint of a large model.](assets/ch2-fig-08-training-footprint.png)

*Figure 2.8. Training GPT-3: the lifetime carbon emissions of five cars, and roughly 1.5 Olympic swimming pools of drinking water evaporated.*

The majority of energy and water is consumed in developing and training models. Published estimates for training GPT-3 — an older model, though "older" here means a matter of a few years — put the carbon cost at approximately the **lifetime emissions of five gasoline cars**, and the water cost at approximately **1.5 Olympic swimming pools of drinking water evaporated**.

> **An important caveat, stated by the instructor.** All of these statistics are simultaneously right and wrong depending on the model, the data center, the region, and the methodology. Accurate figures are difficult to obtain because companies are private and are not obliged to disclose. What is presented here represents researchers' best efforts. The reader should treat the numbers as orders of magnitude, and should re-verify any figure before relying on it.

### 2.5.4 The Cost of a Single Prompt

![Per-prompt resource costs.](assets/ch2-fig-09-per-prompt-costs.png)

*Figure 2.9. Everyday costs: water per email, energy per image, energy per prompt.*

| Task | Approximate cost |
| --- | --- |
| Writing a 100-word email with AI | ≈ **3 bottles** of fresh water (for cooling) |
| Generating one high-resolution image | ≈ **one full smartphone battery charge** |
| One AI prompt versus one conventional search | ≈ **10× the electricity** |

*Table 2.4. Per-prompt resource costs. Exact numbers are contingent on the model.*

The practical suggestion that follows is a heuristic rather than a rule: **be a minimalist**. Before prompting, ask whether the task warrants it. *Is it worth drinking that bottle of water?* If a task can be done better by a search engine or a calculator, the large generative model is the wrong instrument on efficiency grounds as well as environmental ones.

> **An aside on emails.** The instructors noted receiving obviously model-written email routinely, and being able to tell — usually because the message is far longer than its content requires. If the answer is "Great, I'll come to office hours on Tuesday," write that. Three bottles of water for a paragraph of padding around a one-line reply is a poor trade for everyone, including the recipient.

---

## 2.6 A Decision Framework

The remainder of this chapter converts the preceding analysis into a usable procedure. The process has three stages: **define the use case**, **evaluate the risk**, and **review the options**.

> **Knowing when *not* to use AI is perhaps the highest level of AI literacy you can achieve.** Most instruction concerns when to use these tools. The more valuable judgment is recognizing when using one is a bad idea.

### 2.6.1 Stage One: Define the Use Case

**Is it allowed?** Check first, because a negative answer ends the inquiry. Does the course syllabus prohibit generative AI? Does the workplace have a policy? Does the publication, the community, or the competition have rules? Note that policies are often broader than people assume — Grammarly is a language model, and a student who used it to check spelling under a no-AI policy has violated that policy without intending to. This is a genuinely complicated space in which norms are still being established.

**Is an AI tool the right instrument at all?** For mathematics, use a calculator or statistical software. For verified facts, use a library database. Do not use a sledgehammer to crack a nut, or a chainsaw to cut a sheet of paper.

**Are there privacy concerns? Is the data restricted?** The old advice that anything put on the internet is there forever applies to proprietary language models. Prompts are available to the company, to its developers, and potentially to future training runs. Most platforms have data-sharing settings; readers should locate and configure them, and should re-check them after every product update, since defaults are frequently reset.

A useful default: **unless the tool is running locally and is not connected to the internet, do not enter anything you would be uncomfortable seeing published.** A related and stricter principle concerns other people's information. One may reasonably choose to enter one's own medical test result to understand it; one has no standing to enter someone else's.

Institutional licensing changes some of this calculus, but less than users assume. At UC Davis, Gemini is provided under a contract stating that user prompts are not returned to Google for training. That is a meaningful protection. **It is not the same as compliance certification for personally identifiable or otherwise protected information**, and the licensed tool should not be treated as cleared for such data. Chapter 3 records a further, more skeptical view of such assurances from an instructor who has worked on internet infrastructure for three decades.

### 2.6.2 Stage Two: Evaluate the Risk

**Does accuracy matter?** Generating whimsical images for a child does not require accuracy. Detecting breast cancer does.

**Can you verify the result?** Do you possess the expertise to validate the output?

**Will you actually verify it?** These are different questions, and the second is where most failures occur. A person who can read code, asks a model to write code, and then ships it without reading it has the expertise and has not used it.

**Are you willing to be held accountable?**

> **A case that recurs.** A supervisor instructs an employee to produce a report quickly and suggests using a chatbot. The employee complies. The supervisor presents the report to a senior executive. The report is wrong. The supervisor returns and tells the employee they made a mistake.
>
> This feels unjust, and it happens. **Anything you produce with these tools remains yours.** You are the human who chose to use it.

### 2.6.3 Stage Three: Review the Options

The preference ordering that follows from the analysis above:

1. **An approved, licensed tool**, where the institution has vetted and licensed something appropriate.
2. **An open-source tool.** All the code is available for scrutiny: problems can be identified, behavior can be inspected, and transparency is substantially greater.
3. **A proprietary chatbot** — ChatGPT, Gemini, Claude, and similar — only after the preceding checks have been satisfied.

The final assessment — does this tool align with my values? — is the hardest, and readers should expect to remain somewhat unsatisfied when evaluating large proprietary models. They do not disclose everything. Some publish mission statements or value commitments, which may increase confidence, but a published commitment is not proof of adherence. This asymmetry is itself an argument for preferring open tools where they are adequate.

### 2.6.4 The AI Use Roadmap

![A decision flowchart for AI use.](assets/ch2-fig-14-ai-use-roadmap.png)

*Figure 2.10. AI Use Roadmap based on common values.*

The roadmap assembles the preceding questions into a decision procedure. No single guide works for all people, organizations, and situations; this is a scaffold for thinking rather than an algorithm.

The sequence of questions:

1. **Can you do it yourself?** If yes — stop. You probably do not need AI at all.
2. **Is the data restricted?** If yes — stop.
3. **Does truth or accuracy matter?** If no, proceed to the tool question. If yes, continue.
4. **Do you have the expertise to verify results?** If no — stop.
5. **Will you verify the results?** If no — stop.
6. **Are you willing to be held accountable?** If no — stop.
7. **Does the AI tool align with your values?** If no — stop. If yes — **maybe use AI.**

Note that the terminal state is *maybe*, not *yes*.

The underlying principle governing the branches: **where the cost of being wrong is high, a general-purpose AI tool should not be the primary approach.** A medical diagnosis or a legal brief carries real consequences and typically involves private personal data. There, a specialized tool developed, trained, and validated for that specific purpose is appropriate — and still requires a human in the loop. The instructor's formulation: *I want my radiologist using their own medical knowledge, supplemented by a cancer-detection AI tool, rather than a general-purpose chatbot.*

Where the cost is low and no private data is involved — a creative spark, a brainstorm, a summary of one's own messy notes — a mainstream tool is likely adequate.

### 2.6.5 The FACT Framework

![The FACT framework for assessing AI tools.](assets/ch2-fig-10-fact-framework.png)

*Figure 2.11. FACT: Fairness, Accountability, Confidentiality, Transparency.*

Where the roadmap governs the decision to use AI at all, **FACT** governs the assessment of a particular tool.

**Fairness.** Does the tool treat all groups equitably? Does the output reinforce stereotypes or exclude groups? Assume the answer is that it is biased; the operative question is whether you can discover the bias and mitigate it. This is difficult to test directly and can be probed by examining outputs and by asking the same question in several framings.

**Accountability.** If the AI makes a mistake, who is responsible? *Hint: it is you.* You are the human in the loop. Are you comfortable with that? Can you stand behind the work if your supervisor asks?

**Confidentiality.** Was private data used to build the tool? How does the tool use prompts and user data? Are you unwittingly training a public model with your organization's confidential information? Would you be comfortable seeing your prompt on the front page of a newspaper? Can you delete your data? Does the tool have opt-out settings? **A tool with no way to opt out of data sharing is a significant red flag.**

**Transparency.** How was the tool built, by whom, and for what purpose? Who benefits, and who is affected? Does the company disclose its training data and environmental impact? Does the system show its work? Can you explain how the result was reached? *If you cannot explain your methodology, even when assisted by AI, you are not doing research; you are guessing.* This criterion is very difficult to satisfy for proprietary models.

**If a tool fails these four tests, it is time to find a different solution.**

---

## 2.7 Choosing the Right Instrument

### 2.7.1 Alternatives to AI

![A table of non-AI alternatives by task.](assets/ch2-fig-11-better-alternatives.png)

*Figure 2.12. Better alternatives, all of which use less energy and water than an LLM.*

| Task | Alternative to AI | Why |
| --- | --- | --- |
| Fact-checking | Library databases, Google Scholar | Real, verified citations |
| Data analysis | R, Python | Transparency, accuracy, reproducibility |
| Literature review | Library database search; reading abstracts; Zotero | Nuance, context, organization |
| Math and logic | Calculator, specialized software | Calculation rather than prediction |
| Privacy-sensitive work | Local software, non-connected tools, paper | Data security |
| Deep thinking | Socratic dialogue with peers | Creativity and logic |

*Table 2.5. Non-AI alternatives by task.*

These alternatives are often faster and more accurate for their tasks, and they carry neither the environmental nor the ethical burden.

A specific observation on the last row: the impulse to brainstorm with a chatbot is understandable, and it is not a substitute for thinking with people. It is considerably easier to identify and correct for the biases of a colleague you know than for those of a system you cannot inspect. A number of groups have, notably, returned to pen and paper for privacy-sensitive deliberation, and that trend is likely to continue.

### 2.7.2 If You Do Use AI, Use the Right Tool

![A table of AI tools by task.](assets/ch2-fig-12-right-tool-for-the-task.png)

*Figure 2.13. Matching AI tools to tasks.*

| Task | Example tools |
| --- | --- |
| General chatbots, brainstorming | ChatGPT, Copilot, Claude, Gemini |
| Coding | Claude Code, Copilot |
| Literature searching | Elicit, Consensus, Scite |
| Reading and summarizing | NotebookLM, Scholarcy, SciSpace |
| Text editing | Grammarly, LanguageTool |
| Note taking | Zoom AI Companion, Otter.ai |

*Table 2.6. AI tools by task. Tool names date rapidly; the categories do not.*

> **Private or sensitive data should be used only with institution-approved or licensed tools, and only for approved purposes.**

Two cautions accompany this table. First, general-purpose chatbots are acceptable for brainstorming and for getting started; their output should never be treated as a definitive answer. Second, retrieval-based tools such as NotebookLM, which allow the user to supply the documents, improve grounding but do not eliminate the citation problem described in Section 2.4.1 — the system is still performing next-token matching over the supplied material, and a formatted citation may still fail to support the claim attached to it. Increasingly, users treat these tools as evidence of truth. They are not.

---

## 2.8 AI for Good

![Beneficial applications of AI.](assets/ch2-fig-13-ai-for-good.png)

*Figure 2.14. Applications in accessibility, medicine, environmental monitoring, and translation.*

It would be a mistake to leave this chapter believing that AI is a villain and its users are culpable. It is a tool, and tools can be destructive or can build extraordinary things.

- **Accessibility.** Systems that allow blind users to interpret their surroundings through a phone camera; real-time translation and visual description.
- **Medicine.** Detection of cancers earlier than the unaided human eye. Detecting a cancer four years earlier can save a life.
- **Scientific discovery.** Protein structure prediction (AlphaFold) supporting the development of new medicines.
- **Environmental monitoring.** Real-time climate tracking and satellite-based deforestation detection.
- **Legal access.** Translation of legal and workers' rights documents into the languages of migrant farm workers, enabling people to follow proceedings that affect their families and livelihoods, and to make better-informed decisions in the absence of accessible legal counsel.
- **Executive function support.** Task-decomposition tools developed in university settings that break large projects into checklists; automated flashcard generation from course material. Education and accessibility are among the areas in which these tools genuinely shine.

Two qualifications. First, a common argument holds that the environmental costs of AI need not concern us because AI will solve the environmental problems it creates. Some models may indeed contribute to progress on those problems, but the contributions will be specific and will be deeply dependent on human-led development. It is not a reason to defer the question. Second, and more affirmatively: **when we develop and use AI responsibly, it can empower human agency rather than replace it.**

---

## 2.9 Your Responsible AI Manifesto

> **Exercise 2.2 — Three non-negotiables.** Based on the values you identified in Exercise 2.1, write down **three personal red lines** you will not cross in using AI as you move into your career.
>
> Examples offered in the workshop:
>
> - *I will never input protected data into an open LLM.*
> - *I will always disclose when a first draft was AI-generated.*
> - *I won't use AI to do something I can easily do myself.*
> - *I won't use AI to make (too many) silly cat coloring pages.*
>
> You do not have to solve everything at once. Write down something. This is the beginning of a personal guide, and it should be kept in mind through Chapters 3 and 4.

Responsibility is not about restriction. It is about **intentionality**. It is easy to open a tab, type, and press enter. The whole of this chapter is an argument for thinking about what you are doing before you do it.

And whatever your values are, the most important component of artificial intelligence is the human using it.

---

## Chapter Summary

- Objections to AI cluster into reliability, ethical and legal, and resource concerns; all three are legitimate and none is decisive on its own.
- Ethics is the systematic study of what is good or right. The engineer asks whether a thing can be built; the ethicist asks whether it should be. Both questions belong to the person using the tool.
- Every AI tool embodies the values of its funders and developers. Choosing a tool means participating in those values.
- Bias enters at every stage of the pipeline, beginning with a corpus that over-represents the famous, the Western, and the online, and excludes the paywalled and the recent. These are design consequences, not malfunctions.
- Statistical probability is not truth. Model outputs are plausible by construction, and plausibility is precisely what makes them dangerous.
- AI does not cite sources in any meaningful sense. Retrieval-augmented systems improve reliability without solving the problem. A real citation that does not support its claim is harder to catch than a fabricated one.
- The cloud is physical. Training and inference consume large and growing quantities of electricity and fresh water, and the published figures should be treated as contested orders of magnitude.
- The AI Use Roadmap sequences the decision: can you do it yourself, is the data restricted, does accuracy matter, can you verify, will you verify, will you be accountable, does the tool match your values.
- The FACT framework — Fairness, Accountability, Confidentiality, Transparency — assesses a particular tool. A tool with no opt-out from data sharing is a red flag.
- Non-AI alternatives are frequently faster, more accurate, and cheaper for the specific task. Where AI is warranted, task-specific tools outperform general chatbots.
- AI delivers real benefits in accessibility, medicine, science, environmental monitoring, and legal access. Responsibility is about intentionality, not abstention.

## Key Terms

**ethics** · **values** · **social contract** · **corpus** · **garbage in, garbage out** · **algorithmic bias** · **historical bias** · **annotation bias** · **intersectionality** · **concept drift** · **feedback loop** · **veracity** · **hallucination** · **reproducibility** · **parametric memory** · **retrieval-augmented generation (RAG)** · **ghost work** · **data sovereignty** · **deepfake** · **prompt injection** · **agent** · **deskilling** · **capital centralization** · **FACT framework** · **AI Use Roadmap** · **human in the loop**

## Review Questions

1. Distinguish the engineer's question from the ethicist's question, and give an example of a decision about AI use in which the two produce different answers.
2. Explain why a language model's bias is best described as a design consequence rather than a defect. Use the Amazon résumé case in your answer.
3. A colleague argues that retrieval-augmented generation solves the hallucinated-citation problem. Respond, distinguishing between the existence of the source and its support for the claim.
4. Why is a real but non-supporting citation more dangerous than a fabricated one?
5. A student uses a chatbot to check whether 17 × 23 = 391. Explain, in terms of Chapter 1's account of the architecture, why this is the wrong tool.
6. Work through the AI Use Roadmap for two cases: (a) drafting a birthday message for a friend, and (b) summarizing patient interview notes for a clinical research project. State where each terminates and why.
7. Apply the FACT framework to a tool you currently use. Which of the four criteria can you actually evaluate, and which are foreclosed by the tool's opacity?
8. The instructor asks, before prompting, "Is it worth drinking that bottle of water?" Restate this heuristic precisely and identify the class of tasks for which it decisively rules out AI use.
9. Write your three non-negotiables. For each, identify the underlying value and the situation in which you expect it to be tested.

## Further Reading

- Bender, E. M., Gebru, T., McMillan-Major, A., & Shmitchell, S. (2021). On the dangers of stochastic parrots: Can language models be too big? *FAccT '21*. (The definitive paper on corpus bias and environmental impact.)
- Buolamwini, J., & Gebru, T. (2018). Gender shades: Intersectional accuracy disparities in commercial gender classification. *PMLR*.
- D'Ignazio, C., & Klein, L. F. (2020). *Data Feminism*. MIT Press.
- Luccioni, A. S., Viguier, S., & Ligozat, A.-L. (2023). Estimating the carbon footprint of BLOOM, a 176B parameter language model. *JMLR*.
- Li, P., Yang, J., Islam, M. A., & Ren, S. (2023). Making AI less "thirsty": Uncovering and addressing the secret water footprint of AI models. arXiv/NeurIPS.
- Noble, S. U. (2018). *Algorithms of Oppression: How Search Engines Reinforce Racism*. NYU Press.
- Strubell, E., Ganesh, A., & McCallum, A. (2019). Energy and policy considerations for deep learning in NLP. *ACL*. <https://doi.org/10.48550/arXiv.1906.02243>
- *Coded Bias* (documentary, dir. Shalini Kantayya, 2020).
- Congressional Research Service, R48646, on data centers. <https://www.congress.gov/crs-product/R48646>
- Data center and energy infrastructure map: <https://www.maps.com/data-center-map-shows-data-centers-and-energy-infrastructure/>

**Related UC Davis coursework mentioned in the session:** SOC 195; STS 111, 115, 195; PHI 133.
