# Introduction

## About This Book

*AI Literacy and Logic* provides reference material in support of the one-day workshop of the same name offered by the [UC Davis DataLab](https://datalab.ucdavis.edu) and the College of Letters and Science. Its contents are drawn from the workshop's four instructional sessions — the presentation slides and the recorded lectures, including the questions, demonstrations, and discussions that arose during delivery.

The intended audience for both the workshops and this material is undergraduate and graduate students in any discipline, and for staff and faculty who wish to develop a principled rather than incidental relationship to generative artificial intelligence. It presumes no mathematical background, no programming experience, and no prior exposure to machine learning.

### The Instructional Team

| Instructor | Role | Session led |
| --- | --- | --- |
| **Dr. Carl G. Stahmer** | Director, UC Davis DataLab; Science and Technology Studies; L&S AI | Introduction; Session 3, *How to Talk to AI* |
| **Dr. Nick Ulle** | Senior Data Scientist, UC Davis DataLab | Session 1, *How AI Thinks* |
| **Dr. Pamela Reynolds** | Associate Director, UC Davis DataLab | Session 2, *How to Use AI Responsibly* |
| **Rebeccah Yterdal** | STEM Librarian, Researcher Services, UC Davis Library | Session 4, *How AI Talks to You* |

*Table I.1. The instructional team.*

---

## Why This Subject, and Why Now

![Society is at an inflection point.](assets/ch0-fig-01-why-were-here.png)

*Figure I.1. The rationale for the course.*

The premises of the course can be stated in four propositions.

**Society is at an inflection point.** Artificial intelligence technologies are permeating education, industry, and government at a rate without clear precedent in the history of technology adoption.

**Understanding how to use AI tools is becoming a condition of participation.** Effective use bears on professional prospects, on the conduct of ordinary life, and on the capacity to participate in collective decisions about how these systems should be governed.

**The pace of change is exponential.** Any curriculum organized around the features of particular products is obsolete before it is delivered.

**Because of this last fact, understanding how AI works matters more than knowing how to operate any particular tool.** Conceptual understanding of the components of these systems is what allows a person to interpret, evaluate, and adapt to technologies that do not yet exist. This is the central pedagogical commitment of this material, and it explains why a text nominally about using AI devotes its first chapter to how a language model represents the world.

A note on the choice framed by the course as a whole: the question is no longer whether these systems will be present in professional and academic life. The question is how they should be governed and wielded, and by whom. These materials aim to leave the reader capable of answering that question for themselves rather than deferring it to whoever designed the tool.

---

## How the Book Is Organized

The book follows the structure of the workshop day as the workshop was presented. Each chapter corresponds to one session.


| Time | Session | Lead instructor |
| --- | --- | --- |
| 9:00 am | Welcome | Carl Stahmer |
| 9:15 am | How AI Thinks | Nick Ulle |
| 10:45 am | Break | — |
| 11:00 am | Responsible AI | Pamela Reynolds |
| 12:30 pm | Lunch | — |
| 1:15 pm | How to Talk to AI | Carl Stahmer |
| 2:30 pm | Break | — |
| 2:45 pm | How AI Talks to You | Rebeccah Yterdal |
| 4:00 pm | Wrap-up and Reflection | All |
| 4:30 pm | Dismissal | — |

*Table I.2. The orignial workshop schedule.*


| Chapter | Title | Question it answers |
| --- | --- | --- |
| **1** | How AI Thinks | *How do these systems do what they do?* A conceptual, non-technical account of the machinery. |
| **2** | How to Use AI Responsibly | *Should I use this, and when?* Ethics, bias, veracity, environmental cost, and a decision framework. |
| **3** | How to Talk to AI | *How do I get useful results?* Prompting strategy, and its consequences for one's own thinking. |
| **4** | How AI Talks to You | *How do I know whether to believe it?* Hallucination, validation, lateral reading, and synthetic media. |

*Table I.3. Chapter structure.*

The order is not arbitrary. Chapter 1 establishes the mechanism; Chapter 2 asks whether and when the mechanism should be invoked; Chapter 3 addresses the input side of the interaction; Chapter 4 addresses the output side. A reader who begins at Chapter 3 in search of prompting techniques will find them, but will not understand why they work.

Supporting material follows the chapters:

- **Chapter 5, Glossary** — definitions of the technical and conceptual vocabulary introduced throughout.
- **Chapter 6, Appendices** — prompt templates, decision aids, evaluation checklists, tool tables, and consolidated references.

### Apparatus

Each chapter opens with **learning objectives** and closes with a **chapter summary**, a list of **key terms**, **review questions**, and **further reading**. Figures are reproduced from the workshop slides. Case studies, demonstrations, and classroom exercises from the recorded sessions are preserved and set off from the main exposition.

---

## Four Ideas That Recur

Four propositions appear in every chapter of this book, in different registers, because the four instructors arrived at them independently from statistics and data science, from science and technology studies, from the biological and environmental sciences, and from librarianship. They are worth stating at the outset.

**1. Statistical probability is not truth.** These systems produce what is probable given their training data. Probability and truth coincide often enough to be useful and diverge often enough to be dangerous. Nothing in the architecture distinguishes the two cases.

**2. Every tool embodies values.** An AI system reflects the values of those who funded it and those who built it — in what entered the corpus, in what the guardrails forbid, in what the interface makes easy. Choosing a tool is participating in those values.

**3. You are the human in the loop, and you will be held accountable.** Responsibility for a work product does not transfer to the instrument used to produce it. This is true academically, professionally, and increasingly in law.

**4. Knowing when *not* to use AI is perhaps the highest level of AI literacy.** Much popular instruction concerns when and how to use these tools. The harder and more valuable judgment is recognizing when a search, a calculator, a library database, a colleague, or one's own thinking is the better instrument.

---

## About the UC Davis DataLab

The workshop from which this book derives was produced by the *UC Davis DataLab: Data Science and Informatics* in collaboration with the College of Letters and Science.

DataLab is a cross-university effort that fosters, promotes, and facilitates data science to accelerate discovery within and across the scientific, engineering, social and humanities disciplines.

We collaborate and problem solve with researchers to enable qualitatively novel, interdisciplinary research. We also provide an innovative training environment for students at all levels to meet academic and industry needs for skilled graduates. We partner with external agencies and organizations to grow our impact and further opportunities for our students.

Further learning opportunities are listed at <https://datalab.ucdavis.edu> and <https://datalab.ucdavis.edu/workshops/>.

Participants who completed the live workshop received a certificate issued by the College of Letters and Science upon completion of the post-workshop reflection survey.

---

## A Note on Sources and Currency

This book was assembled from a specific delivery of the workshop. Two consequences follow.

First, the quantitative claims about model sizes, energy consumption, water use, and the capabilities of named products were accurate as presented and will drift. Where the instructors themselves flagged a figure as contested or model-dependent, that qualification is preserved in the text. The reader should treat every number in this book as a figure to be re-verified rather than a constant.

Second, the reasoning is more durable than the numbers. The argument that training a large model carries a substantial and largely invisible resource cost does not depend on the specific multiple by which a prompt exceeds a search query. The argument that a citation produced by a language model is a claim requiring verification rather than evidence supporting one does not depend on which model produced it.

Applied to this book itself, the fourth chapter's advice holds: read laterally, verify the claims, and consult the primary sources listed at the end of each chapter.
