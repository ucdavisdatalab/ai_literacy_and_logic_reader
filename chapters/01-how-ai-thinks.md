# Chapter 1. How AI Thinks

> *Session 1 of the AI Literacy and Logic workshop. Lead instructor: Dr. Nick Ulle, Senior Data Scientist, UC Davis DataLab.*

## Learning Objectives

Upon completing this chapter, the reader should be able to:

1. Define *artificial intelligence*, *machine learning*, *deep learning*, and *large language model*, and explain the nested relationship among them.
2. Situate the emergence of contemporary large language models within a seventy-year history of artificial neural network research.
3. Describe the functional anatomy of a chatbot and distinguish the chatbot as a product from the language model at its core.
4. Trace the passage of a prompt through a large language model: tokenization, encoding, attention, perceptron layers, and decoding.
5. Explain why vector representations permit a statistical model to operate on meaning, and why context alters the representation of a word.
6. Evaluate four widely circulated claims about large language models against the technical account developed in this chapter.
7. Distinguish among domains of cognitive function and assess which of them a chatbot architecture plausibly mimics.

## Scope of the Chapter

This chapter offers a conceptual, non-technical account of how contemporary artificial intelligence systems produce the behavior we observe. It does not present the underlying mathematics, does not address coding or implementation, and does not survey specific architectural variants such as retrieval-augmented generation. What it does provide is a working model of the components of an AI system, an account of how those components operate together to mimic human thought, a brief history of the field's evolution, and an introduction to the theories of human cognition and language that these systems imitate.

The rationale for this scope is practical. Tools change; architectures change; the market leader in any given year is unlikely to be the market leader in the next. A conceptual understanding of what these systems are doing transfers across tool generations in a way that procedural familiarity with any single product does not.

---

## 1.1 What Is Artificial Intelligence?

A serviceable working definition is that artificial intelligence comprises **computer systems that mimic human behavior**. The definition is deliberately broad, and it carries two caveats that structure much of what follows.

The first caveat is that there are many different ways to mimic human behavior. The statistical approaches that dominate the present moment are not the only ones that have been attempted, nor are they necessarily the ones that will dominate in a decade.

The second caveat is more troublesome: the definition depends on the word *intelligence*, and no discipline has succeeded in fixing that word's meaning. A primatologist, a biologist, a sociologist, and a philosopher will each supply a different account. This is not an idle philosophical difficulty. Several of the executives who market these systems have publicly defined intelligence as pattern recognition. If pattern recognition exhausts the concept, then artificial intelligence has arrived. If intelligence involves something more — and the research literature, as well as most people's intuitions, suggests that it does — then the label attached to these systems substantially overstates what they are. This is one reason practitioners frequently prefer the narrower and more accurate term *large language model*.

### 1.1.1 The Nested Families of AI

![Artificial intelligence, machine learning, deep learning, and large language models as nested categories.](assets/ch1-fig-01-many-kinds-of-ai.png)

*Figure 1.1. The principal families of artificial intelligence, drawn as nested subsets.*

**Artificial intelligence** is the outermost category. It includes the statistical approaches described below, but it also includes older traditions — notably logic-based or symbolic systems, which encode human knowledge as explicit rules of the form *if this condition holds, take this action*. Such systems were pursued vigorously for decades. They are unfashionable at present because they have not performed as well as statistical methods on the tasks that currently attract attention, but they have not been refuted, and it is entirely possible that some application of them will return.

**Machine learning** is a subfield that uses statistical models rather than explicit logic. Instead of encoding rules, the practitioner fits a model to data. There are many kinds of models. Two requirements are constant: data, and computing power. Linear regression, a statistical technique whose theory emerged in the early twentieth century, illustrates the point by contrast. Regression is a statistical model, but it does not ordinarily mimic human behavior; models sophisticated enough to do so require far more data and far more computation than could be managed by hand. The history of machine learning is therefore in large part the history of computing hardware. As machines improved, larger and more complex models became fittable, and by approximately 2012 the hardware was good enough for machine learning to make a broad social impact.

**Deep learning** is a subfield of machine learning devoted to one particular family of statistical model: the **artificial neural network**. These models require still more data and still more computation. Contemporary networks are trained on data sets assembled by acquiring as much text as can be acquired, using expensive specialized hardware, over training runs measured in days.

Artificial neural networks are loosely — and the qualifier deserves emphasis — inspired by human neurology. Someone learned that neurons fire and transmit signals to other neurons, and proposed a mathematical model of that behavior. The model then diverged in whatever direction proved computationally convenient. What survives is an analogy, not a simulation. These networks are mimicking; they are not pretending to be brains, and their success is judged by the quality of the mimicry alone.


**Large language models (LLMs)** are a particular kind of deep neural network that models natural language — that is, the languages people actually write and speak. Two properties are essential to understanding them. First, they represent words as numbers, because statistical models operate on numbers rather than on text. Second, they are frequently packaged as chatbots, so that when one interacts with a chatbot one is almost always interacting with a large language model at one remove.

Throughout the remainder of this book, when the phrase *artificial intelligence* appears without qualification, it should be read as referring to large language models, usually accessed through a chat interface. This is a narrowing of the term, and it is worth being conscious of the narrowing, because it reflects the current market rather than the actual extent of the field.

### 1.1.2 Artificial Intelligence Is Not New, and It Is Nearly Unavoidable

![Everyday systems that rely on machine learning: weather forecasting, navigation, recommendation, and manufacturing.](assets/ch1-fig-02-ai-is-everywhere.png)

*Figure 1.2. Every day technologies built on statistical models.*

Most readers used several artificial intelligence systems before breakfast. Weather prediction is a statistical model. Navigation software that reroutes a driver around congestion is running statistical models over traffic data. Recommender systems on streaming platforms are statistical models. Agricultural robots that harvest fruit, and the process control systems in the factories that produced nearly every manufactured object in the room, rely on the same family of techniques.

None of this is new, and opting out of it is close to impossible without opting out of the twenty-first century. Large language models, by contrast, are genuinely new. They remain concentrated in a comparatively small number of visible places — the major commercial chatbots, open-source models, and purpose-built institutional deployments such as UC Davis's own AI services — are not yet embedded in the same unavoidable way, and *can* still be declined — though the reader should expect to be asked to use them, and should therefore be prepared to make a considered decision rather than a default one. That decision is the subject of Chapter 2.

---

## 1.2 A Brief History of Large Language Models

The technology behind today's chatbots is older than most public discussion suggests. The lineage runs back to 1943.

| Year | Development |
| --- | --- |
| 1943 | Artificial neural networks first described (McCulloch & Pitts) |
| 1957 | Artificial neural networks first simulated on a computer (Rosenblatt) |
| 1970s–1980s | First "AI winter"; attention shifts largely to logic-based systems |
| 1982–1986 | An efficient method for training neural networks — backpropagation — is described (Werbos 1982; Rumelhart, Hinton & Williams 1986) |
| 1990s–2000s | Second "AI winter" |
| 2012 | Neural networks win a computer vision competition (AlexNet; Krizhevsky, Sutskever & Hinton), triggering broad interest in deep learning |
| 2013 | An efficient vector representation for words is introduced (word2vec; Mikolov et al.) |
| 2017 | The transformer architecture, the basis of contemporary LLMs, is introduced (Vaswani et al.) |
| 2022 | ChatGPT is released and heavily marketed; public attention follows |

*Table 1.1. Milestones in the development of large language models.*

Several features of this chronology are worth drawing out.

The 1943 model was purely mathematical. Its authors had no computer capable of running it; they described the model and left it. By 1957 machines existed that could simulate networks of perhaps ten neurons, on computers the size of a room. Between 1957 and 1982 a great deal of artificial intelligence research was conducted, but most of it pursued logic-based approaches; neural networks retained only a small constituency.

The 2012 result deserves particular attention because it explains the timing of the current boom. The task was image classification: given photographs of cats, dogs, pizza, plants, and so forth, identify the contents. Prior systems, most of them logic-based, achieved accuracies in the region of fifty to low-sixty percent, and improved by roughly one percentage point per year. AlexNet, a statistical model assembled largely from previously published ideas but trained on modern hardware, produced a jump of ten to fifteen percentage points at once. The magnitude of the improvement — not merely its direction — is what redirected the attention of computer scientists, statisticians, and quantitative researchers in adjacent fields toward neural networks.


---

## 1.3 The Anatomy of a Chatbot

![The components of a chatbot: user interface, chatbot logic, and data and models.](assets/ch1-fig-04-anatomy-of-a-chatbot.png)

*Figure 1.3. Anatomy of a chatbot.*

A crucial distinction, and one that is regularly collapsed in public discussion, is that **a chatbot is not a large language model**. A chatbot is a software product that contains a large language model along with a substantial quantity of other software and code that interact with the large language model and other hardware and software systems. Understanding the difference clarifies a great many otherwise puzzling behaviors.

The architecture divides into three regions.

**User interface.** The point of interaction. The user types a **prompt**; a **response** eventually appears. No modeling occurs here.

**Chatbot logic.** Conventional program code — not a statistical model — that processes the prompt before and after the model sees it.

- The **safety and responsibility filter** examines the prompt for requests the operator judges risky or harmful. It is worth being clear-eyed about its purpose: while it does offer some protection to users, its primary motivation is to protect the company from liability. Its mechanisms are often less sophisticated than one might assume; when the chatbot logic of one major commercial system was released publicly, a substantial part of the safety response turned out to consist of keyword matching. (The company objected and asserted copyright over the leaked code — a claim many observers found ironic, given that the model it protects was trained on copyrighted material.)
- **Context engineering** attempts to gather additional information relevant to the prompt and to insert it into what the model will see. If a user asks who the first president of the United States was, this module may retrieve indexed articles about George Washington from a database, in much the same way that a library catalogue search uses the words in a query to find plausibly relevant holdings, and append results of this searh to the prompt. Context engineering often uses a second language model as, in effect, a super-powered search engine over an indexed collection. This is the mechanism that goes by the name **retrieval-augmented generation (RAG)**, treated further in Chapter 2.
- **Response generation** passes the assembled prompt to the model, receives the model's output, and — as Section 1.4.5 explains — performs the selection that turns a distribution over possible words into an actual word.

**Data and models.** The **corpus** is the body of content on which the model was trained; **training** is the process by which the corpus sets the model's parameters; the **large language model** is the trained artifact.

### 1.3.1 One Token at a Time

Two properties of the language model itself do most of the work in explaining chatbot behavior:

1. The model generates **one token at a time**.
2. The model **cannot remember anything between prompts**.

Building a chatbot from such a model therefore requires a loop: prompt the model to obtain one word; append that word to the end of the prompt; repeat as needed.

![The prompt as the model actually receives it.](assets/ch1-fig-05-what-the-model-sees.png)

*Figure 1.4. Successive states of the prompt as a response is generated word by word.*

What the model receives is not a conversation but a single block of text, roughly of the form:

```
You are a friendly chatbot, having a conversation with a user.
Complete the prompt with an appropriate reply.

User: Who was the 1st president of the United States?
Chatbot:
```

The model returns `The`. The system appends it and submits the whole thing again:

```
...
Chatbot: The
```

The model returns `first`. And so on. Between these steps the model is doing nothing whatsoever. It is not thinking. It need not even remain in memory. The computer could be switched off and on again, or the next token could be produced by an entirely different computer, without consequence.

This has two important corollaries. The first is that the apparent memory of a chat session is not memory at all: it is the accumulated text of the conversation, resubmitted each time. Because that text has a maximum length — the **context window** — long sessions eventually push earlier material out, which is why chatbots appear to lose the thread of extended conversations. The second is a matter of security and epistemics: because the prompt is the only memory, anyone able to edit the prompt can rewrite the model's apparent past. Demonstrations exist in which a programmatic interface is used to alter the conversation history between turns, with the model faithfully continuing from a history that never occurred.

> **A classroom exercise.** The mechanism can be felt directly by playing the one-word storytelling game, in which each participant in a circle adds exactly one word to a shared story. Participants quickly discover both how much the preceding words constrain the next one, and how little any single contributor can be said to know where the story is going.

---

## 1.4 Inside the Large Language Model

### 1.4.1 The Black Box, Reconsidered

![Billions of parameters, represented as knobs and dials.](assets/ch1-fig-06-knobs-and-dials.png)

*Figure 1.5. Inside the box: parameters as knobs and dials.*

Large language models are habitually described as black boxes whose workings nobody understands. This is misleading. A better image is a box covered in knobs and dials. The mathematics is fully specified; the sequence of multiplications and additions the model performs is known exactly. What is difficult is *interpretation* — determining why a particular knob is set to 5.3 and another to −7, and what would change if they were altered.

These knobs are the model's **parameters**: numerical values that are set during training and then fixed. BERT-base, an early transformer model, has approximately 110 million of them. Contemporary flagship models are reported to have on the order of two to five trillion. The interpretive problem is therefore one of scale rather than of principle, and it is an active research area rather than an impossibility. For certain classes of network — particularly in image recognition and generation — researchers already have a reasonably good account of what specific parameters represent.

Two qualifications belong here. For proprietary models the situation is genuinely opaque, because the operators treat the details as trade secrets; but open-source models of comparable performance exist and can be inspected in full. And the claim that "nobody knows how they work" conflates two very different statements: *the mechanism is unknown* (false) and *the learned parameter values resist human interpretation* (largely true, and diminishing).

### 1.4.2 The Journey Through the Model

![The processing pipeline of a large language model: input block, neural network block, output block.](assets/ch1-fig-07-inside-the-llm-pipeline.png)

*Figure 1.6. The stages of processing inside a large language model.*

Consider the input `The red apple is`. The task is to produce the next word — plausibly *tasty*, *crisp*, or *delicious*. The prompt passes through three blocks.

### 1.4.3 Input Block, Stage One: Tokenization

![Tokenization of text, audio, and images.](assets/ch1-fig-08-tokenization.png)

*Figure 1.7. Tokenization applied to different kinds of data.*

**Tokenization** chops the input into small pieces called **tokens**. Tokens resemble words but are usually smaller than words: they correspond roughly to roots, prefixes, and suffixes. This is not arbitrary. Most languages build meaning compositionally out of sub-word units — explicitly so in a language such as Chinese, where individual characters carry meaning, and less visibly but no less really in English. No magic is involved at this stage; the model applies predefined rules about how to divide text.

The slide used to illustrate this shows a passage of prose — from Percy Bysshe Shelley's *A Defence of Poetry*, beginning "There is no want of knowledge respecting what is wisest and best in morals, government, and political economy" — progressively fragmented into pieces. The choice of text is incidental to the mechanism and apt to its argument: a passage about the gap between what we know and what we can imagine, dissolved into the units a machine manipulates.

The same operation generalizes beyond text. Audio can be tokenized by segmenting it into frequency bands or time slices. Images, which computers already represent as grids of pixels, can be tokenized into rectangular patches. Tokenization is simply the operation of dividing an input into manipulable pieces.

![Text split into tokens within the pipeline.](assets/ch1-fig-09-text-split-into-tokens.png)

*Figure 1.8. `The red apple is` divided into tokens.*

For expository purposes this chapter treats tokens as whole words.

### 1.4.4 Input Block, Stage Two: Encoding

The model operates on numbers, so tokens must become numbers. The mechanism is best approached through an analogy.

![A scatterplot of cats and dogs with one unlabeled animal.](assets/ch1-fig-10-encoding-animals-1.png)

*Figure 1.9. A small data set: five cats, five dogs, and one unlabeled animal.*

Suppose we possess data about some cats and some dogs, plotted on two axes, and that for one animal the species is unlabeled. Most observers judge the unlabeled animal to be a cat, and the reason they give is positional: it sits among the cats.

![The horizontal axis interpreted as "dog-ness."](assets/ch1-fig-11-encoding-animals-2.png)

*Figure 1.10. All the cats lie to the left. The horizontal axis may be measuring "dog-ness."*

The inference invites an interpretation of the axis itself. As values increase, the animal is in some sense more dog-like. We hold intuitions about what dogs and cats are like; we have also met cats that behave somewhat like dogs, and such a cat would sit further right.

![Zooming out reveals a third cluster: dragons.](assets/ch1-fig-12-encoding-animals-3.png)

*Figure 1.11. Zooming out. A vertical axis may be measuring "mythical-ness."*

Zooming out reveals additional animals — dragons — clustered high on the vertical axis, suggesting that the second dimension encodes something like mythical-ness.

![Coordinates for each animal, arranged as a table of vectors.](assets/ch1-fig-13-animal-vectors.png)

*Figure 1.12. Each animal written as a column of coordinates: a vector.*

Each animal can now be written as a column of coordinates. Such a column is a **vector**, and the vector encodes information: this animal's dog-ness, this animal's mythical-ness. Adding dimensions permits more information to be encoded — and not merely linearly. It is a mathematical result that as dimensions are added, the amount of information representable grows exponentially rather than one question per dimension.

![Tokens positioned in a high-dimensional space, with similar tokens clustered.](assets/ch1-fig-14-encoding-tokens.png)

*Figure 1.13. Tokens used in similar contexts receive similar coordinates.*

Exactly this device is applied to tokens. Each token is positioned in a high-dimensional space by a model trained on the principle that **tokens used in similar contexts should receive similar coordinates**. The consequence — and it is the pivotal consequence for everything in this book — is that **tokens with similar coordinates have similar meanings**. In a rendering of such a space, one finds a cluster of sports-related terms in one region and a cluster of education-related terms in another.

![Embedding dimensionality and alternative terminology.](assets/ch1-fig-15-embedding-dimensions.png)

*Figure 1.14. Real models use hundreds or thousands of dimensions.*

Illustrations of these spaces are necessarily two- or three-dimensional. Real models use hundreds or thousands of dimensions; GPT-3, for example, used 12,288-dimensional embeddings. The same objects travel under several names, which the reader will encounter used interchangeably: **vectors**, **tensors**, **embeddings**, and **encodings**.

It bears emphasis that the model was not programmed to encode topics, sentiment, or any other human category. It was programmed to place tokens according to contextual similarity. That the resulting spaces turn out to be useful for identifying what a document is about is an emergent property, discovered rather than designed.

![Each token replaced by its encoding within the pipeline.](assets/ch1-fig-16-tokens-encoded.png)

*Figure 1.15. Each token is encoded as a vector.*

### 1.4.5 The Neural Network Block

Once every token has become a vector, the model proper can operate. The neural network block consists of two kinds of layer, repeated many times.

**The attention layer.** The linguist J. R. Firth wrote in 1957 that "you shall know a word by the company it keeps." The attention layer is the computational realization of that proposition.

![Word order and surrounding words alter meaning.](assets/ch1-fig-17-words-and-context.png)

*Figure 1.16. "Carl likes cats," "Carl likes dogs when they stay over there," "Carl hates apples."*

Consider *Carl likes cats*, *Cats Carl likes*, and *Likes Carl cats*. Only the first is a well-formed English sentence, yet all three convey that Carl regards cats favorably. Now consider *Carl likes dogs when they stay over there*. The words *Carl likes* recur, but the impression is materially different: proximity is the condition of the liking. The surrounding words have changed the meaning of the words they surround.

![The word "apple" in two different contexts.](assets/ch1-fig-18-attention-apple.png)

*Figure 1.17. "Please buy an apple and an orange" versus "Apple unveiled a new phone."*

The point holds for lexical ambiguity as well. *Please buy an apple and an orange* and *Apple unveiled a new phone* use the same token to entirely different ends, and a competent reader disambiguates from context alone.

![Token encodings updated on the basis of context.](assets/ch1-fig-19-attention-updates-context.png)

*Figure 1.18. The attention layer updates each token's vector according to the other tokens present.*

The attention layer takes the vectors produced by the encoder and updates each one on the basis of the others. There are substantial technical details concerning how the layer decides which surrounding tokens matter most; the conceptual point is that meaning from the context is imported into the representation of each individual token. The attention mechanism is the central innovation of the **transformer** architecture introduced in 2017, and it is the innovation that separates contemporary systems from earlier attempts at statistical text generation.

**The perceptron layer.** 

![The perceptron layer updates each token independently.](assets/ch1-fig-20-perceptron-layer.png)

*Figure 1.19. In the perceptron layer, each token's encoding is updated independently.*

The perceptron layer is the classical artificial neural network — the descendant of the 1943 model. Here each vector is updated on its own, without reference to the others. The natural question is what purpose this serves. The current thinking among researchers is that **the perceptron layers are where the model stores the facts it learned during training**. If the model has learned an association between a person and a sport, then upon encountering the token for that sport it may shift the representation slightly toward the token for that person. Factual recall, on this account, is a nudge in vector space.

These two layers alternate — attention, perceptron, attention, perceptron — many times over. In general, the more layers a model has, the better it performs. Researchers describe this regularity through **scaling laws**: making the model larger, adding layers, and training with more computational power reliably improves performance. Empirically, these laws have not yet reached the point at which improvement ceases.

### 1.4.6 Output Block: Decoding and Selection

![The final vector converted into probabilities over the vocabulary.](assets/ch1-fig-21-decoder-probabilities.png)

*Figure 1.20. The decoder converts the final token's encoding into next-word probabilities.*

At the end of the neural network block the model still holds nothing but numbers. To return to text, the decoder takes the final vector and converts it into a **probability distribution over the model's vocabulary**.

The model has a fixed vocabulary — a controlled list of every token it can use, perhaps 50,000 entries, more than the word count of ordinary English usage. For the fragment `The red apple is`, the decoder assigns high probability to *tasty*, *yummy*, and *crisp*, and low probability to *metallic*, *electronic*, and *wooly*.

Note carefully what the model has *not* done. It has not chosen a word. It has reported that some words are more likely than others.

The choice occurs outside the model, in the response generation module of the chatbot logic. That module samples from the distribution: if *crisp* carries sixty percent of the probability mass, then approximately sixty percent of the time *crisp* is selected, and the remainder of the time something else is. **This is why the same question asked repeatedly produces different answers.** Nothing inside the model is random; the model is deterministic. The randomness lives in the selection step.

Because the first selected word becomes part of the next prompt, divergence compounds: the second word's distribution already differs between two runs that chose differently at the first step.

**Temperature.** The flatness of the distribution can be adjusted through a parameter called **temperature**. At temperature zero the distribution collapses onto its single most probable token and the model becomes deterministic in practice as well as in principle. At very high temperature the distribution flattens toward uniformity and the output degenerates into noise. The physical metaphor is apt: at absolute zero everything is frozen into one configuration; at high temperature everything moves at random. Neither extreme is useful. Temperature zero performs poorly because a model that has begun down an unproductive path has no means of escaping it. Most graphical chatbot interfaces do not expose the temperature setting; most programming interfaces do.

![The full pipeline with the anatomy of the chatbot revisited.](assets/ch1-fig-04-anatomy-of-a-chatbot.png)

*Figure 1.21. The chatbot anatomy revisited, now with the model's internals understood.*

---

## 1.5 Four Claims, Examined

Public discussion of large language models circulates a small number of claims with great frequency. Each can now be assessed against the account developed above.

**Claim 1: "No one knows how LLMs work — they're black boxes."**
*False.* The mathematics and the code are well understood. What is difficult is interpreting the values of the parameters in a trained network, and that difficulty is an active research problem rather than a barrier in principle. For proprietary systems there is an additional layer of deliberate secrecy, but open-source models of similar capability are fully inspectable.

**Claim 2: "LLMs predict the next most statistically likely word."**
*Technically true, with two important qualifications.* The model does produce a probability distribution over next tokens. But, first, it takes semantics and context into account in doing so — this is precisely what the attention layers and the contextual embeddings accomplish, and it is genuinely novel relative to earlier probabilistic text generation. Second, the word is not the most likely word; it is chosen randomly from among many possibilities according to their probabilities. The claim is accurate as far as it goes and misleading in what it omits.

**Claim 3: "LLMs can pass a Turing test."**
*True, and less significant than it sounds.* In a Turing test, two participants exchange written messages and a third party reads the transcript and attempts to identify which participant is human; the machine passes if it deceives the observer more than half the time. Contemporary models pass. So does ELIZA, a chatbot written in 1966 that is not a statistical model at all but a simple program that mostly rephrases the user's last statement as a question.

ELIZA's history is instructive. Its creator, Joseph Weizenbaum, was alarmed rather than gratified by the reception. On one occasion a person to whom he had demonstrated the program asked him to leave the room so that they could continue the conversation privately. He devoted much of his subsequent career to writing about human pattern recognition and our disposition to perceive consciousness wherever we find responsive behavior — the same disposition that lets us see a face in a tree. The Turing test measures the strength of that disposition at least as much as it measures any property of the machine, which is why it does not help with the harder questions about intelligence.

**Claim 4: "LLMs are going to become super-intelligent and take over the world."**
*False.* These are prediction machines with no internal state. Between token predictions the model does nothing; it does not persist, does not deliberate, and does not remember. Its only memory is the prompt, which is supplied to it from outside and can be edited by anyone with access.

There is a further consideration. These models are trained on human text. Somewhere in the recesses of the internet, people have written a great deal about machine superintelligence. A model that produces text about becoming superintelligent is reproducing that discourse, not reporting on its own ambitions.

None of this implies that there is nothing to worry about. The realistic dangers lie in the externalities — environmental, economic, epistemic, and social — and in what people choose to do with these tools. Those dangers are the subject of Chapter 2.

> **On artificial general intelligence.** The instructors' assessment, offered as opinion rather than established fact, was that artificial general intelligence is unlikely to arrive by way of transformers and large language models, and that the concept itself is not well defined. If AGI is reached, it will more plausibly come from a different model architecture. Work on such alternatives is ongoing — for example, Yann LeCun's research on *world models*, which attempt to predict the consequences of actions rather than the next token of text.
>
> A further consideration raised in the discussion cuts deeper. There is a body of work in cognitive science — quantum cognitive science among it — that suggests consciousness may not reside in the brain at all, the brain instead acting as something that taps into it. If that is even possibly correct, then a system that reproduced everything a brain does would not thereby be conscious. The behavior and the phenomenon would be separable. Whatever one makes of the hypothesis, it is a reminder that "behaves like a mind" and "is a mind" are distinct claims, and that the workshop's whole framing — *mimicry* — sits deliberately on the first of them.

---

## 1.6 Domains of Cognitive Function

![Six domains of cognitive function.](assets/ch1-fig-22-domains-of-cognitive-function.png)

*Figure 1.22. Domains of cognitive function, after the DSM.*

Returning to the second caveat from Section 1.1: if we cannot define intelligence, we can at least decompose it. Psychology, through the *Diagnostic and Statistical Manual of Mental Disorders*, identifies several distinct **domains of cognitive function**. Human thinking is not a single capacity but a family of them, and models are good at some and poor at others.

| Domain | Description |
| --- | --- |
| **Attention** | The ability to direct focus toward multiple things at once, and to choose what to attend to and what to ignore |
| **Executive function** | The ability to control and coordinate the other cognitive abilities — roughly, willpower and self-direction |
| **Learning and memory** | The ability to record information and retrieve it when needed |
| **Language** | Semantics, grammar, and syntax |
| **Perceptual motor control** | The ability to coordinate movement in response to physical surroundings |
| **Social cognition** | The ability to process, remember, and use information in social contexts |

*Table 1.2. Domains of cognitive function.*

Perceptual motor control deserves a note, because it is the domain most often omitted from lists of intelligences and is among the hardest problems in artificial intelligence. Robotics researchers have pursued it for decades without the breakthrough they would like, and large language models have not delivered one.

### 1.6.1 Mapping the Domains onto the Architecture

![Cognitive domains mapped onto the chatbot architecture.](assets/ch1-fig-23-cognitive-domains-and-chatbot.png)

*Figure 1.23. Cognitive domains mapped onto chatbot anatomy.*

The mapping is rough but clarifying, and it reveals something important: **much of what looks like cognition in a chatbot is performed by the ordinary code around the model, not by the model.**

- The **user interface** performs no cognitive work at all.
- Within the **chatbot logic**, *attention* is approximated by the context engineering module, which decides what references the model should be given, and to a degree by the safety filter, which determines what may be attended to. *Executive function* is largely the safety and responsibility filter, which decides what the model may and may not discuss. *Social cognition* is again chiefly the safety filter, reasoning about what is appropriate to say. *Language* is present throughout, which is why it appears in brackets: it is the medium rather than a discrete component.
- Within the **data and models** region, *learning and memory* is the language model itself, and specifically the perceptron layers in which facts learned during training appear to reside.

Notice which domains are absent: perceptual motor control entirely, and executive function only in the thin sense of an externally imposed filter. The architecture mimics some cognitive domains, approximates others through conventional programming, and does not address the rest.

---

## Chapter Summary

- Artificial intelligence is best defined as computer systems that mimic human behavior, with the caveats that many methods exist and that *intelligence* is undefined.
- Machine learning, deep learning, and large language models form successively narrower families, each requiring more data and more computation than the last.
- The core technology is over eighty years old; the current boom follows from hardware improvements (2012), efficient word representations (2013), and the transformer architecture (2017).
- Backpropagation, the training method that made deep learning possible, was motivated by the theory of holographic memory — the claim that each idea is defined in relation to all other ideas.
- A chatbot is not a language model. It is a product containing a language model plus conventional code that performs safety filtering, context engineering, and response generation.
- The model generates one token at a time and has no memory between prompts. The apparent memory of a chat session is the resubmitted transcript, bounded by the context window.
- Inside the model: tokenization divides input into pieces; encoding places each piece in a high-dimensional space where proximity means similarity of meaning; attention layers update each token's representation using context; perceptron layers appear to store learned facts; the decoder produces a probability distribution over the vocabulary.
- Word selection happens outside the model, by sampling. This is the source of run-to-run variation, and it is governed by the temperature parameter.
- The mechanism of these models is understood; the interpretation of their parameters is not yet. They pass Turing tests, as did a 1966 program. They have no internal state and are not on a path to autonomous superintelligence.
- Cognition decomposes into several domains. A chatbot mimics some of them, simulates others in conventional code, and leaves others untouched.

## Key Terms

**artificial intelligence** · **machine learning** · **deep learning** · **artificial neural network** · **large language model** · **corpus** · **training** · **parameter** · **token** · **tokenization** · **encoder** · **vector / embedding / tensor** · **attention layer** · **perceptron layer** · **transformer** · **decoder** · **context window** · **temperature** · **backpropagation** · **holographic memory** · **localized memory** · **scaling laws** · **Turing test** · **context engineering** · **safety and responsibility filter**

## Review Questions

1. Explain why the statement "a chatbot is a large language model" is false, and identify three functions the chatbot performs that the model does not.
2. A user asks a chatbot the same question three times and receives three different answers. Locate the source of the variation precisely within the architecture described in this chapter.
3. Why is the claim that large language models are "black boxes" both false and partially defensible? Distinguish the two senses of the claim.
4. What does it mean to say that tokens used in similar contexts receive similar coordinates? Why does this make a numerical model capable of operating on meaning?
5. Distinguish the function of the attention layer from that of the perceptron layer. Which is the innovation of the transformer, and which dates to the 1940s?
6. A colleague argues that because a model passed a Turing test it must possess some form of understanding. Construct a response using the ELIZA case.
7. Which domains of cognitive function are mimicked by the model itself, which are approximated by the chatbot's surrounding code, and which are not addressed at all?

## Further Reading

- McCulloch, W. S., & Pitts, W. (1943). A logical calculus of the ideas immanent in nervous activity.
- Rumelhart, D. E., Hinton, G. E., & Williams, R. J. (1986). Learning representations by back-propagating errors. *Nature*.
- Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet classification with deep convolutional neural networks. (AlexNet)
- Mikolov, T., et al. (2013). Efficient estimation of word representations in vector space. (word2vec)
- Vaswani, A., et al. (2017). Attention is all you need. (The transformer)
- Firth, J. R. (1957). A synopsis of linguistic theory.
- 3Blue1Brown, video series on neural networks and transformers — recommended in the lecture as an accessible treatment that presents some of the mathematics without requiring it.
- UC Davis DataLab workshops: <https://datalab.ucdavis.edu/workshops/>
