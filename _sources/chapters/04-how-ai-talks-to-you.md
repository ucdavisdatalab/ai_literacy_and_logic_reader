# Chapter 4. How AI Talks to You

> *Session 4 of the AI Literacy and Logic workshop. Lead instructor: Rebeccah Yterdal, STEM Librarian, Researcher Services, UC Davis Library.*

## Learning Objectives

Upon completing this chapter, the reader should be able to:

1. Describe how the tone and confidence of AI output are engineered, and explain why friendliness is a design choice with epistemic consequences.
2. Define *hallucination* and *AI slop*, and give examples ranging from the trivial to the actively harmful.
3. Explain why AI output constitutes a claim requiring evidence rather than evidence supporting a claim.
4. State the accountability principle and identify who bears responsibility when AI-assisted work is wrong.
5. Apply the CRAAP test to a source, and explain which of its five criteria are difficult or impossible to apply to AI output.
6. Execute the lateral reading workflow — break it down, search, analyze, decide, repeat — on an AI response.
7. Select appropriate tools for lateral reading, and explain why another chatbot is generally a poor verification instrument.
8. Evaluate images and video for signs of synthetic generation across five categories of implausibility, and apply verification techniques including reverse image search and account-history analysis.

## Recap and Framing

![Recap: prediction, bias, and prompting.](assets/ch4-fig-01-how-ai-sounds.png)

*Figure 4.1. How AI sounds: confident, adjustable in friendliness, built to give you an answer.*

Three points from earlier chapters set up this one.

**AI output is confident.** As Chapter 2 established, and as is worth restating: an AI response will sound confident the overwhelming majority of the time, regardless of whether the statement is true.

**Tone is a product decision.** Companies tune their models to be more or less friendly. Most contemporary general-purpose chatbots are quite friendly — one instructor's comparison was to a golden retriever. Anthropic's Claude has undergone explicit "character training." Models can be built and tuned to be more engaging, warmer, even romantic. A model that sounds one way today may sound different after an update.

**They are built to give you an answer.** Marketing language positions these systems as personal assistants that will save time on scheduling, correspondence, and routine tasks. The design consequence is that they always produce a response, including when they do not have one.

> **The golden retriever.** The metaphor, from a cartoon a colleague generated in Gemini, is worth keeping. A chatbot wants to please you. You throw the ball; it goes to fetch. But sometimes it sees a chicken along the way and decides the chicken is more valuable, and brings you the chicken instead.
>
> That is a hallucination.

---

## 4.1 Hallucination and AI Slop

![Hallucinations and AI slop.](assets/ch4-fig-02-hallucinations-and-slop.png)

*Figure 4.2. Misleading, inaccurate, or fabricated content.*

**Hallucination:** misleading, inaccurate, or fabricated content in an AI response.

**AI slop:** the flood of low-quality, frequently hallucination-laden AI-generated content overwhelming parts of the internet — including material that ranks well in search results and presents as news or research.

### 4.1.1 The Range of Harm

Hallucinations run from the silly to the dangerous.

**Trivial.** A widely circulated example: a user searching for advice on cheese sliding off pizza received an AI search summary suggesting the addition of non-toxic glue to the sauce. The failure is funny, and it illustrates a structural point about search-integrated AI summaries. When you type into a search box you are not constructing a prompt: you are not defining a speaker, establishing an audience, or supplying context. Everything in Chapter 3 that improves output quality is absent by construction, which makes these summaries *more* susceptible to error than a considered prompt would be.

> **Practical measures.** Appending `-AI` to a search query on Google suppresses the AI summary at the top of the results. In-page AI overviews further down the results remain, but the initial summary does not appear — which also avoids the energy and water cost of generating it, and the effort of scrolling past it. Alternatively, some search engines allow AI features to be disabled entirely in settings; DuckDuckGo was recommended for this and for its data practices.

**Harmful.** OpenAI's Whisper speech recognition system, used to produce transcripts including in medical settings, has a documented tendency to fill silences by inventing content. In some cases the invented content included descriptions of violent acts. Research found that transcripts of patients with aphasia — reduced ability to express oneself in speech, typically following stroke or brain injury — contained *more* of these fabrications than transcripts of other patients. The failure mode falls hardest on the people least able to correct it.

### 4.1.2 Friendliness and Sycophancy

There is evidence that friendlier tools may hallucinate more (Ibrahim et al., 2026), and popular reporting has noted that users who are friendlier to a system sometimes get better answers. The corollary is less comfortable: **models can be tuned to validate you**, which means that a false premise supplied in a prompt may simply be reinforced.

> **Demonstration: Jim Henson at Ohio State.** The prompt asked ChatGPT to write a short essay about Jim Henson's undergraduate years at Ohio State University. The response began by describing Henson as the visionary creator behind the Muppets and asserting that his undergraduate years at Ohio State played a formative role in shaping his artistic sensibility and approach.
>
> The first claim is true. The second is not: Jim Henson attended the University of Maryland. But the prompt asserted Ohio State, and the model built an essay on that premise.
>
> This is a distinct species of hallucination — not invention out of nothing, but the confident elaboration of a falsehood the user supplied. It is precisely the failure mode that the 20% "confirm my assumptions" usage pattern in Chapter 3 produces at scale.

### 4.1.3 Is the AI Lying to You?

No. It is not intentionally deceiving you, and when it hallucinates it is not, technically speaking, doing anything wrong. It is doing exactly what it was built to do.

OpenAI's own research offers a useful account (Kalai et al., 2025): **language models are optimized to be good test-takers, and guessing when uncertain improves test performance.** Consider a multiple-choice exam. You do not know the answer. You do not leave it blank; you choose an option, because a guess might earn credit and a blank certainly will not. That is what these systems do. Lacking the fact, they guess — fluently.

The additional caution: the semantic similarity and contextual processing described in Chapter 1 permit these systems to operate on something resembling meaning. That is not the same as comprehension, and it does not mean the outputs carry meaning or intention in the sense a human utterance does.

**Every AI tool will hallucinate to some extent.** No tool is exempt. It is also worth remembering that the general-purpose chatbots most people encounter are not experts in anything. A tool trained specifically to analyze scans for cancerous masses is a different case — and even that tool is producing a claim that requires human review. Unless a system was built for a niche purpose, it is not an expert in anything.

---

## 4.2 AI Outputs Are Not Evidence

![AI outputs are claims, not evidence.](assets/ch4-fig-03-outputs-are-not-evidence.png)

*Figure 4.3. Claims, not evidence; usually not built to cite sources; and hallucinated sources.*

Every session of this workshop hammers the same point, and this is the chapter in which it becomes operational.

**What an AI gives you cannot serve as evidence** — not for an argument, not for a paper, not for a professional recommendation. **Everything that comes out of an AI tool is a claim that you need evidence to support.**

The citation problem was treated in Chapter 2, and two empirical findings sharpen it:

- GPT-4o produced citation fabrications in which references were either wholly invalid or carried a DOI or link that was not real or that resolved to an entirely different article.
- In a mental health literature review, GPT-4o fabricated close to **20% of citations** (Linardon et al., 2025).

Models are generally not built to cite sources, except where they have been specifically constructed for research or educational use — and retrofitting citation onto a system that generates text probabilistically does not make its citations trustworthy.

There *are* AI tools built specifically to locate real citations, which returns to the principle of using the right tool for the task. And there are a great many tools built for different tasks and audiences; the general-purpose chatbot is the least specialized instrument available.

---

## 4.3 You Will Be Held Accountable

![You are responsible for your work products.](assets/ch4-fig-04-you-will-be-held-accountable.png)

*Figure 4.4. You are responsible for your work products, regardless of the tools used to create them.*

> **You are responsible for your work products, regardless of the tools you use to create them.**

The consequences are not hypothetical.

**Law.** Attorneys who filed briefs citing cases that did not exist, supplied by an AI tool, have been fined and subjected to discipline by bar associations. The AI is not sanctioned; the attorney is.

**Marketing and communications.** An advertisement designed with AI assistance that contains a hallucination is the responsibility of the person who failed to catch and correct it.

> **Google's Bard advertisement (2023).** In the promotional launch material for Bard, the model gave an incorrect answer about which telescope took the first image of a planet outside our solar system, attributing it to the James Webb Space Telescope. In fact the first exoplanet image was captured by the European Southern Observatory's Very Large Telescope in 2004.
>
> The error's origin is instructive: many news articles had used constructions like "the first picture of an exoplanet from the JWST," meaning the first such picture *that telescope* had taken — not the first ever taken. The model reproduced the pattern without the distinction. The error was in the company's own launch advertisement, and it was expensive.

**Finance and small business.** A small business owner using AI for financial management who acts on a hallucinated figure has spent the money. There is no recourse to the tool.

The instruction that follows is the AI Use Roadmap from Chapter 2, re-encountered from the far side. Before using the tool, ask whether you are willing to be held accountable for the result. After using it, recognize that you now are.

---

## 4.4 Validate

![Validate.](assets/ch4-fig-05-craap-test.png)

*Figure 4.5. The CRAAP test: a framework for evaluating content validity.*

So what should be done? **Do not believe it.** Begin from the assumption that what you received is not true, and validate it. Skepticism — in the constructive sense established in Chapter 2 — is the appropriate posture.

### 4.4.1 The CRAAP Test

The CRAAP test is an evaluation method developed by librarian Sarah Blakeslee at the Meriam Library, California State University, Chico. Librarians have taught it for years, and it applies to anything you read, not only to AI output.

| Criterion | Question |
| --- | --- |
| **C — Currency** | Is the production date of the information such that the information can be considered relevant? |
| **R — Relevance** | Is the fact or argument (and its source) relevant to my question or problem? Who is the intended audience? |
| **A — Authority** | Does the person or organization making the claim have the necessary credentials and experience to be a reliable source on your topic? |
| **A — Accuracy** | Can you verify the accuracy of the claim in at least two other reputable sources? |
| **P — Purpose** | Why was the information originally created at its source? Is it fact, opinion, entertainment, satire, or propaganda? |

*Table 4.1. The CRAAP test.*

Applied notes on each criterion:

- **Currency.** Note that you can introduce time bias accidentally through your prompt.
- **Relevance.** Even if a claim is true, it may not be relevant — and a lack of relevance often traces back to insufficient specificity in the prompt.
- **Authority.** Consider whether you can trace the information back to its original source and evaluate that source. **The AI tool does not itself have authority.**
- **Accuracy.** Verification in at least two other reputable sources.
- **Purpose.** Essentially: what bias is present in the information?

### 4.4.2 The AI Validation Problem

![The CRAAP test applied to AI.](assets/ch4-fig-06-craap-test-in-ai.png)

*Figure 4.6. CRAAP applied to AI output: four of five criteria become difficult or impossible.*

Here is the difficulty. Nearly everything the CRAAP test asks cannot be determined by looking at a chatbot response.

| Criterion | The problem with AI output |
| --- | --- |
| **Currency** | How do you know the date of the information? |
| **Relevance** | Is the fact or argument relevant to your question — and did your prompt actually ask what you meant? |
| **Authority** | How do you know the original source? Does the tool even have the training and corpus to answer this question? |
| **Accuracy** | *This one you can still do.* Verify each claim in at least two other reputable sources. |
| **Purpose** | Can you find the purpose of the information at its source? And additionally: what is the purpose of the AI tool, and what bias exists in it? |

*Table 4.2. The CRAAP test in AI.*

Purpose becomes doubly difficult, because two purposes are now in play: that of the original information, which the model cannot report, and that of the tool itself, along with its underlying bias.

**The consequence is that accuracy carries the weight.** Because the other four criteria are largely foreclosed, verification of each claim against at least two other reputable sources becomes the essential step. **When using AI, this is the most important thing you can do.**

---

## 4.5 Lateral Reading

![The lateral reading workflow.](assets/ch4-fig-07-lateral-reading-workflow.png)

*Figure 4.7. Lateral reading: break it down, search, analyze, decide, repeat.*

**Lateral reading** means leaving the source in front of you and consulting other sources in order to evaluate its facts, claims, references, quotations, and authorities. Every professional fact-checker works this way.

The name comes from the physical action. Instead of reading *vertically* — proceeding down the page — you read a little, then open another tab and move *laterally* to verify what you have just read, then return. It might equally be called tabbed reading.

| Step | Action |
| --- | --- |
| **1. Break it down** | Identify specific facts, claims, references, and sources of authority |
| **2. Search** | Search other sources to verify facts, references, and credentials |
| **3. Analyze** | Analyze the results of your external verification |
| **4. Decide** | Determine whether the claim is valid |
| **5. Repeat** | Repeat the cycle for each claim, fact, or source |

*Table 4.3. The lateral reading workflow.*

The technique applies in two directions. **Evaluating a source:** encountering an unfamiliar website or publication, open a new tab and see what other sources say about *it* — verify early, so you can decide whether it is worth reading at all. **Evaluating a claim:** read until you reach a fact, then move laterally to check it.

### 4.5.1 Why AI Requires More

Lateral reading is good practice for everything. With AI it becomes mandatory, and the reason is structural.

When reading an article written by a human, you may fact-check the first several claims, find them sound, form a judgment about the author's reliability, and extend provisional trust to the rest. **That inference does not hold for AI output.** The first ten claims may be true and the eleventh may be a hallucination. There is no author whose track record accumulates across the piece, because there is no author — only a token-by-token process that is equally capable of accuracy and fabrication at every position.

**You must check every fact.** You cannot stop checking, or continue reading on trust, based on the first few.

> A parallel worth noting from the media-literacy literature: a good deal of misinformation is constructed to sound credible at the outset and to place the false or conspiratorial material later, once the reader's guard has lowered. The AI case is not adversarial in the same way, but it produces the same requirement.

### 4.5.2 Demonstration: Evaluating an Unfamiliar Source

The session's first worked example concerned a conspiracy claim — an article asserting that technology companies were demanding increased atmospheric intervention to cool AI data centers — published on a site nobody in the room recognized.

Rather than beginning with the claim, the instructor began with the **source**. A new tab, a search on the publication's name, and a Wikipedia entry established that the site had operated previously under a different name and was a known purveyor of fabricated news; it had rebranded.

That single lateral move settled the question before any individual claim in the article had been examined. It illustrates the half of lateral reading that is easiest to skip: **verify early, so that you can decide whether the source is worth reading at all.** Wikipedia serves this purpose well — not as an authority on the underlying subject, but as an orientation to who is speaking and what is known about them, with a reference list attached.

### 4.5.3 Lateral Reading an AI Response

Contemporary chatbots sometimes — but not always — include links to sources within responses, both inline and in a source list at the end.

Recall from Chapter 2 that these are not references in the scholarly sense. **Think of AI sources as "read more" links rather than as the sources of the information.** Note also that not every claim will carry one.

The workflow applied to a response:

1. **Break it down.** The opening paragraph is often a summary of the whole; the substantive claims follow. Identify the first specific fact or claim.
2. **Search** for independent confirmation.
3. **Analyze** what you find.
4. **Decide** whether the claim holds.
5. **Repeat** for the next claim.

**When the tool supplies a source, apply lateral reading to the source as well:**

- Click the source — it may not be reputable.
- Follow the link — the source or the link may be hallucinated.
- Read it and apply CRAAP — currency, relevance, authority, accuracy, purpose. **It may exist, be real, and still fail to support what the AI response claims it supports.**

### 4.5.4 Tools for Lateral Reading

![Tools for lateral reading.](assets/ch4-fig-08-lateral-reading-tools.png)

*Figure 4.8. Where to verify.*

| Tool | Notes |
| --- | --- |
| **Library resources** | Scholarly sources; the most reliable starting point |
| **Search engines** | Useful for surfacing coverage and provenance |
| **Wikipedia** | Useful for orientation and for its reference lists |
| **Multiple trusted news sources** | Plural is the operative word |
| **News fact-checkers** | Purpose-built for exactly this. Snopes was named repeatedly in the session as a first stop for viral images and claims |
| **An alternate LLM** | Only with significant caveats — see below |
| **An LLM for data extraction** | A specific, limited, legitimate use — see below |

*Table 4.4. Lateral reading tools.*

> **On using another chatbot to check the first one.** This is generally a poor idea. The major models are trained on approximately the same material and function in approximately the same way; agreement between them is not verification. Their access to current information also varies unpredictably — some can retrieve material from minutes ago, others cannot.
>
> There is a narrow benefit: a fresh session in a different tool removes the accumulated context of the original conversation, which may itself have been steering the answer. If you do this, do not simply ask *is this true* or re-submit the identical prompt. Use it to investigate further. And where you have access to a **specialized model** appropriate to the specific claim — a medical model for a medical fact — that is a materially different and better proposition, though it is not available to most people most of the time.

> **The data-extraction technique.** Breaking a long AI response into its individual claims is itself laborious. One practical approach — suggested during the workshop by Dr. Stahmer — is to paste the response into a *separate* session and ask the tool to extract only the factual claims as a bulleted list. You then have a checklist to verify, without having done the extraction work by hand.
>
> **The caveat is essential:** the extraction may miss claims, and the extraction step can itself hallucinate. Keep everything you know about these tools in mind while using one. This is a labor-saving device for a step you still perform, not a shortcut around verification.

---

## 4.6 Synthetic Images and Video

![AI-generated images and video.](assets/ch4-fig-09-ai-generated-images.png)

*Figure 4.9. A second validation problem.*

We are accustomed to treating photographs as representations of fact. This was never entirely accurate — an event can look one way from one vantage and differently from another — but it is now far more complicated.

There are two distinct problems here. First, a picture may no longer validate a claim. Second, **pictures themselves must now be validated.** And the material arrives not only in response to your prompts: AI slop is encountered incidentally, everywhere on the internet, and it is increasingly difficult to evaluate.

### 4.6.1 A Diagnostic Exercise

> **Exercise 4.1 — Nine images, two real.** The workshop presented a grid of nine images and disclosed that only two were authentic. Participants were asked to examine them and say which looked real, which looked wrong, and why.
>
> Several observations from the room proved productive, and several confident judgments proved wrong. This is the expected result. The instructor — who has studied this material for years and continues to take detection quizzes — reported still finding it difficult. **Getting them wrong is not a failure; it is the current state of the technology.**

### 4.6.2 Five Categories of Implausibility

![What to look for in a suspect image.](assets/ch4-fig-10-what-to-look-for.png)

*Figure 4.10. Categories of implausibility. After Kamali et al. (2024).*

The overarching question is simply: **what generally doesn't make sense?** Beneath it sit five categories.

**1. Functional implausibilities.** Objects that could not perform their function.

![Asymmetrical buckles on a garment.](assets/ch4-fig-11-functional-implausibility-buckles.png)

*Figure 4.11. Functional implausibility: asymmetrical buckles.*

![A pole that supports nothing.](assets/ch4-fig-12-functional-implausibility-pole.png)

*Figure 4.12. Functional implausibility: a non-functional pole.*

Architecture is a particularly rich source: staircases that lead nowhere, columns with holes that make no structural sense, railings at levels that would not function. In one exercise image, the strongest cue was that a figure appeared to have walked *out of the air* across the safety line onto a railway platform; the platform railings and levels then compounded the impression.

![Merged earpieces on eyeglasses.](assets/ch4-fig-13-merged-earpieces.png)

*Figure 4.13. Merged earpieces.*

**2. Anatomical implausibilities.**

![A missing eye detail.](assets/ch4-fig-15-anatomical-implausibility.png)

*Figure 4.14. Anatomical implausibility: missing eye detail.*

![A visual artifact between teeth.](assets/ch4-fig-14-visual-artifact-teeth.png)

*Figure 4.15. Anatomical implausibility: a visual artifact between teeth.*

In the exercise, one image looked convincing in clothing, perspective, and background — and, on magnification, showed a fully formed eye socket without an eyeball. Facial expressions can be subtly wrong; mouths and teeth are frequent failure points.

> **Hands are no longer a reliable tell.** Image generators were famously bad at hands. They have improved substantially. Do not rely on hands.

**3. Violations of physics.**

![An impossible reflection.](assets/ch4-fig-16-violations-of-physics.png)

*Figure 4.16. Violations of physics: an impossible reflection.*

**Reflections are among the most reliable indicators.** Mirrors, windows, puddles, and lakes are all difficult for generators to render consistently. In the exercise image, the subject's head and gaze angle did not match the reflection, and the shirt showed incongruities between the direct view and the reflected one.

**Lighting and shadow direction** is the second common physics failure: the sun appears to come from one direction while shadows fall in a way inconsistent with it.

**4. Sociocultural implausibilities.**

![A sociocultural implausibility.](assets/ch4-fig-17-sociocultural-implausibility.png)

*Figure 4.17. Sociocultural implausibility — but remember that unlikely does not mean impossible.*

Situations that are socially or culturally improbable. The widely circulated image of the Pope in a large white puffer jacket is the canonical example.

> **The essential caution: unlikely does not mean impossible.** Probabilistically, an unusual thing could have happened. This category yields a red flag, not a verdict — which is precisely why it must be combined with the others.

**5. Stylistic artifacts.**

![Stylistic artifacts in a synthetic image.](assets/ch4-fig-18-stylistic-artifacts.png)

*Figure 4.18. Stylistic artifacts: plastic or waxy texture, cinematization, unnatural detail, inconsistent resolution and color.*

- **Plastic or waxy texture**, and skin with no visible texture at all.
- **Cinematization** — professional-grade lighting in a setting where professional lighting would not exist.
- **Hyper-real but unnatural detail** — more detail than the scene would plausibly contain.
- **Inconsistencies in resolution and color** across regions of a single image.

> **Why this category is hard.** A skilled photographer produces genuinely striking images: highly produced lighting, unusual moments, deliberate stylistic choices. These signals are red flags to weigh, not proof.

**A sixth cue: text.** Generators remain poor at rendering written language. Signs in the background, product labels, and street names frequently contain text that is not real language, or that resembles words without being them. Where an image contains legible writing, it is worth examining.

### 4.6.3 The Technology Is Improving

![Newer images from the same synthetic account.](assets/ch4-fig-18-stylistic-artifacts.png)

The workshop showed two images from the same Instagram account — `fit_aitana` — an earlier one exhibiting several of the artifacts above, and a newer one in which the tells were essentially absent. **The second is not a real person and not a real influencer** — but it is an account with followers, comment activity, and advertising revenue.

There is a self-financing loop here worth naming: synthetic influencer accounts that sell advertising use the revenue to purchase better generation technology, which produces more convincing images, which sustains the account.

There is also a hard economic constraint that currently helps:

> **The video heuristic.** Generated video is expensive to produce. Consequently, almost nobody makes long ones, and generation quality degrades as length increases — errors accumulate. **At the time of the workshop, a video running over about a minute, particularly with sustained dialogue, was very likely authentic.**
>
> This heuristic has a shelf life. It will fail as costs fall and quality improves. It is included here as a worked example of the kind of *economic* reasoning that supplements visual inspection, not as a permanent rule.

### 4.6.4 The Cognitive Cost of Verification

A theme runs through the exercise that is worth making explicit. Detection rarely rests on one decisive artifact. It rests on **accumulated information that does not add up** — the same judgment one exercises reading a paper closely.

And that judgment cannot be exercised at scrolling speed. **It takes time.** Things we used to be able to assume are most likely true can no longer be taken for granted, and the labor of verification has been transferred to the reader.

### 4.6.5 Where to Learn and Practice

Communities have formed around this problem, and they are worth using.

- **Reddit communities** devoted to identifying AI-generated images and video, where creators sometimes appear and confirm that a piece was generated, and where the rest is worked out by collective investigation.
- **Riddance.ai**, and the personal account maintained by one of its operators, which focuses specifically on identifying AI-generated video and explaining the tells.
- **Detection quizzes**, of which many now exist: a set of images is presented and the participant judges which are authentic. This is the most efficient way to calibrate, and — as the instructor noted of her own results — remaining difficult after years of practice is the normal outcome, not a personal failing.

---

## 4.7 What to Do About It

![Healthy skepticism, verification, and source analysis.](assets/ch4-fig-19-what-to-do-about-it.png)

*Figure 4.19. What to do.*

**Healthy skepticism.**

- Look for improbabilities.
- Ask whether context and purpose make sense. Is someone selling something? Is the image engineered to make you click — perhaps onto a page that harvests your information?
- Follow links. **Do not just trust the AI overview.** Even while lateral reading, open the actual sources rather than relying on a generated summary of them.

**Verify through other sources.**

- **Different angles.** If a photograph documents a real event, other photographs of that event, from other people and other vantages, will usually exist. A single sensational image with no corroborating imagery is itself evidence.
- **Reputable textual references.** Is anyone credible writing about this?

**Analyze the source.**

- Is there a named creator or photographer? Real photographs usually carry attribution, though it can be stripped as an image circulates.
- What are the credentials of the producer or publisher? What is the website?

### 4.7.1 Lateral Watching

![Evaluating social media accounts.](assets/ch4-fig-20-lateral-watching.png)

*Figure 4.20. "Lateral watching": applying lateral reading to images and video.*

The same tabbed-verification discipline applies to visual media. On social media specifically:

- **Are they selling something?** The workshop's examples were mundane and instructive: an account circulating a fabricated image in order to sell a dental plan, and images purporting to document the aftermath of Hurricane Ian that had been generated rather than photographed. Disaster imagery is a recurring vector, because it travels fast and invites emotional rather than analytic response.
- **How old is the account?**
- **What is the account history?**
- **Are the videos short?**

> **Why account history is diagnostic.** One example shown in the workshop was an image that had since been deleted: when the underlying generation technology improved, the account's operator removed every earlier image that was easy to identify as synthetic, leaving only newer, more convincing material.
>
> **Five hundred thousand followers and two weeks of history is a substantial red flag.**

Note also that AI influencer accounts frequently do disclose, though not always plainly: the disclosure may be in the account name, in a pun, in the biography, or behind an external link. Enforcement of disclosure requirements on social platforms is currently weak.

### 4.7.2 Reverse Image Search and Watermarking

![Reverse image search and digital watermarks.](assets/ch4-fig-21-reverse-image-search.png)

*Figure 4.21. Reverse image search and digital watermarks.*

**Reverse image search.** Take a screenshot and submit it to a reverse image search service — TinEye or Google among them. This surfaces where else the image appears, which can trace it to an original source, show whether reputable news outlets are discussing it, or reveal that fact-checking services have already identified it as fabricated.

**Digital watermarks.** Some generated media carries an embedded watermark — Google DeepMind's SynthID is one such system. Metadata can also carry provenance information, though it is usually stripped by social media platforms. These signals are chiefly usable by professional fact-checkers rather than by a person scrolling a feed, but the infrastructure is developing.

---

## 4.8 Case Study: AI-Generated Journals

The session closed with a problem posed to the room, and it is the most demanding application of everything in this chapter.

> **The problem.** New journals have appeared in which all of the articles are AI-generated. They present as legitimate peer-reviewed research journals. How would you verify that an article is not AI-generated?

Participants proposed a reasonable sequence, and each proposal was met with a complication.

*Search for the authors; check whether they have institutional affiliations or personal websites.* — A good starting point. But these operations frequently use the **real names of real researchers**, on topics those researchers plausibly write about.

*Check the researcher's other publications.* — But the fabricated article is within their actual area, and a recent publication might simply not be listed yet.

*Go to the library.* — **This is the answer.** Consult the library's journal databases and the list of journals to which the institution subscribes, which are vetted and reputable. Absence from that list does not prove illegitimacy; it establishes that the item requires substantially more scrutiny.

> **The case that motivated the question.** One such fabricated article took a chapter from a book by a real researcher and converted it into an article — same topic, same subject matter, and language closely resembling the author's own. Interviewed afterward, the researcher said it could have fooled his best friend and colleagues in his own department. It used his own idiom. He had not written it and had not submitted it anywhere.
>
> What ultimately exposed it: a passage in the paper **contradicted the researcher's own body of work**. A reader who knew the field wrote to him asking about the inconsistency.

**Why would anyone do this?** The motive discussed in the room was corrosive rather than commercial: flooding the literature with plausible-looking bad science degrades trust in the scientific process itself, and scientists cannot readily tell which items are fabricated. (Fee-charging predatory publishing, in which a venue's revenue does not depend on its contents being real, is a second and well-documented motive, though it was not the one raised in the session.) The instructors' broader point: this chapter has largely concerned the limitations of the models, but **these tools are also actively used, deliberately, by people whose interests are not yours.** That is a reason for more skepticism, not less, and a reason that verification must move outside the space in which the claim was encountered.

Three further conclusions were drawn, and they generalize well beyond journals.

**Skepticism is local, not global.** The lesson is not that science is unreliable or that the peer-review process should be distrusted. It is that *this particular item in front of you* warrants verification. Healthy skepticism is a practice applied to specific claims.

**Read what you cite.** You should never cite something you have not read and judged to be methodologically sound. A fabricated paper can occasionally be good enough to escape detection — but the vast majority of them, read carefully by someone with expertise in the field, contain something that does not make sense or is not scientifically sound. As your expertise develops, use it: read the whole paper rather than the abstract.

**The obligation is not new.** We have always had to verify information; photographs were never simply true. What has changed is that a habit of taking things at face value became widespread, and the current environment punishes it severely. You cannot glance at something, understand it immediately, and use it immediately — and you cannot delegate that understanding to an AI tool either.

> **A closing note from the industry panel.** Employers convened by the workshop organizers were asked what they want from graduates. Their answer: not completed assignments. In professional work there are no grades for turning something in. *Did you learn something? Is there something interesting here? Can you think deeply about this topic?*
>
> That is the same argument the unremarkable mean makes in Chapter 3, arriving from the employer's side of the desk.

---

## Chapter Summary

- AI output is engineered to sound confident and friendly. Tone is a product decision, and friendliness may correlate with increased hallucination.
- Hallucination ranges from the comic (glue in pizza sauce) to the harmful (fabricated content inserted into medical transcripts, disproportionately for patients with aphasia).
- Search-integrated AI summaries are especially error-prone, because a search query is not a constructed prompt.
- Models can elaborate confidently on false premises the user supplies. The Jim Henson case shows a hallucination that the user caused.
- The system is not lying; it is optimized to be a good test-taker, and guessing when uncertain improves test scores.
- AI output is a claim requiring evidence, never evidence supporting a claim. Citation fabrication rates near 20% have been documented in a peer-reviewed context.
- You are accountable for work you produce with these tools. Attorneys have been fined; companies have shipped errors in their own advertising.
- The CRAAP test evaluates currency, relevance, authority, accuracy, and purpose. Applied to AI output, four of the five become difficult or impossible, which puts the weight on accuracy: verify each claim in at least two reputable sources.
- Lateral reading — break it down, search, analyze, decide, repeat — is the working method. With AI you must check *every* claim, because reliability does not accumulate across a response.
- Another chatbot is a poor verification tool; specialized models and library resources are better. Extracting a claim list with an LLM saves labor but is itself fallible.
- Synthetic images can be assessed across five categories of implausibility: functional, anatomical, physics, sociocultural, and stylistic — plus rendered text. Hands are no longer a reliable tell; reflections and shadows remain among the best.
- Detection depends on accumulated inconsistency, not a single artifact, and it takes time that scrolling does not allow.
- Verify through other angles, reputable text sources, creator attribution, account age and history, reverse image search, and where available digital watermarks.
- Fabricated scholarship using real researchers' names and idiom is now circulating. The library's vetted databases and actually reading the work remain the defenses.

## Key Terms

**hallucination** · **AI slop** · **character training** · **sycophancy** · **claim versus evidence** · **accountability** · **CRAAP test** · **currency** · **relevance** · **authority** · **accuracy** · **purpose** · **lateral reading** · **lateral watching** · **data extraction** · **functional implausibility** · **anatomical implausibility** · **violations of physics** · **sociocultural implausibility** · **stylistic artifacts** · **cinematization** · **reverse image search** · **SynthID** · **digital watermark** · **predatory publishing**

## Review Questions

1. Explain why an AI-generated summary in a search results page is *more* likely to contain errors than a response to a carefully constructed prompt.
2. In the Jim Henson example, who introduced the error? What does this case demonstrate about the 20% of users identified in Chapter 3 as seeking confirmation?
3. Restate the "good test-taker" account of hallucination. Why does it imply that hallucination cannot be eliminated by better training alone?
4. Apply the CRAAP test to a specific AI response. Which criteria could you evaluate, which could you not, and what would you have to do to evaluate the remainder?
5. Explain why extending trust to the remainder of an AI response after verifying its first several claims is invalid, while doing the same for a human-authored article may be reasonable.
6. Why is checking one chatbot's answer against another chatbot generally poor verification? Under what narrow conditions does it have value?
7. Examine an image you encounter this week. Work through all five categories of implausibility and state your conclusion, along with the confidence you have in it and why.
8. The "videos over a minute are probably real" heuristic rests on an economic constraint rather than a technical one. Explain the constraint, and predict what will invalidate the heuristic.
9. You encounter an article in an unfamiliar journal, attributed to a researcher who genuinely works in the field. Describe the full verification sequence, including the step the workshop identified as decisive.

## Further Reading

- Kamali, N., et al. (2024). How to distinguish AI-generated images from authentic photographs. arXiv. <https://doi.org/10.48550/arXiv.2406.08651>
- Kalai, A. T., et al. (2025). Why language models hallucinate. (OpenAI's account of guessing behavior and test-taking optimization.)
- Linardon, J., et al. (2025). On citation fabrication rates in AI-assisted mental health literature review.
- Ibrahim, et al. (2026). On the relationship between conversational warmth and hallucination rates.
- Van Kampen, K. Evaluating resources and misinformation. University of Chicago Library. <https://guides.lib.uchicago.edu/c.php?g=1241077&p=9082343>
- University of Maryland Libraries. Artificial intelligence (AI) and information literacy: Fact-checking AI with lateral reading. <https://lib.guides.umd.edu/c.php?g=1340355&p=9880575>
- Anthropic. Claude's character. <https://www.anthropic.com/research/claude-character>
- NASA. 2M1207 b — first image of an exoplanet. <https://science.nasa.gov/resource/2m1207-b-first-image-of-an-exoplanet/>
- Riddance.ai and associated commentary on identifying AI-generated video.
- TinEye reverse image search; Google Images reverse search.
- Google DeepMind SynthID.
