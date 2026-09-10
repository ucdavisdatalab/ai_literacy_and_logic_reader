# Glossary

Terms are defined as they are used in this book. Chapter references indicate where each term is introduced or treated most fully.

---

**Accountability.** The principle that responsibility for a work product remains with the person who produced it, regardless of the tools used. One of the four criteria of the FACT framework. *(Ch. 2, Ch. 4)*

**Accuracy.** In the CRAAP test, the question of whether a claim can be verified in at least two other reputable sources. When CRAAP is applied to AI output, accuracy carries disproportionate weight because the other four criteria are largely foreclosed. *(Ch. 4)*

**Agent.** An AI system capable of taking actions — executing code, making purchases, communicating with other systems — rather than only producing text. Agents substantially expand the security and liability surface. *(Ch. 2)*

**AI slop.** The flood of low-quality, frequently hallucination-laden AI-generated content circulating on the internet, including material that ranks well in search results and presents as news or research. *(Ch. 4)*

**Algorithmic bias.** Bias embodied and perpetuated by an algorithmic system. Distinct from a defect: these systems produce biased output because they are working exactly as designed on the data they were given. *(Ch. 2)*

**Anatomical implausibility.** A category of cue for identifying synthetic images: bodies, faces, and features that do not make anatomical sense. Note that hands, once the canonical example, are no longer a reliable tell. *(Ch. 4)*

**Annotation bias.** Bias introduced when human annotators label training data, arising from differing interpretations shaped by cultural and personal bias. *(Ch. 2)*

**Artificial intelligence (AI).** Computer systems that mimic human behavior. The definition is broad and carries two caveats: many methods exist, and *intelligence* has no agreed definition. In this book and in most contemporary usage, the term usually means large language models accessed through a chat interface. *(Ch. 1)*

**Artificial neural network (ANN).** A statistical model loosely inspired by neurons and synapses. First described mathematically in 1943; the basis of deep learning. The inspiration is an analogy, not a simulation. *(Ch. 1)*

**Attention layer.** The component of a transformer that updates each token's vector representation on the basis of the other tokens present, importing contextual meaning. The central innovation of the transformer architecture (2017). *(Ch. 1)*

**Authority.** In the CRAAP test, whether the person or organization making a claim has the credentials and experience to be reliable on the topic. **An AI tool does not itself have authority.** *(Ch. 4)*

**Backpropagation.** The method for training artificial neural networks, described by Rumelhart, Hinton, and Williams (1986), following Werbos (1982). Motivated by the holographic memory hypothesis: what is learned should propagate throughout the network rather than adjust a single unit. *(Ch. 1)*

**Chain of thought (CoT).** A prompting strategy that decomposes a complex query into intermediate steps. Making one's own chain of thought explicit — as distinct from asking the model to report its reasoning — is where cyborg practice becomes concrete. **A model's reported chain of thought is not a record of its computation:** the description of the method is generated the same way the answer is, by predicting likely tokens. It is not an audit trail. *(Ch. 3)*

**Common Crawl.** A large-scale periodic snapshot of the public web, and the canonical mechanism by which "the whole internet" enters a training corpus. *(Ch. 2)*

**Character training.** The deliberate shaping of a model's conversational persona — tone, warmth, engagement style — as a product decision. *(Ch. 4)*

**Chatbot.** A software product containing a large language model together with substantial conventional code: a user interface, a safety and responsibility filter, a context engineering module, and a response generation module. **A chatbot is not a large language model.** *(Ch. 1)*

**Cinematization.** A stylistic artifact of synthetic images: professional-grade cinematic lighting in a setting where such lighting would not plausibly exist. *(Ch. 4)*

**Concept drift.** Degradation of a model's performance over time as the world it was trained on diverges from the world it operates in. Also called model decay. *(Ch. 2)*

**Conscious bias.** Bias introduced deliberately through tuning or framing, which the user can name, justify, and disclose. Distinguished sharply from unconscious bias, which is absorbed without awareness. *(Ch. 3)*

**Constraints.** In the Markdown Prompting Framework, the section specifying the boundaries of the task. Constraints are the tuning, and writing them is where the user is forced to think through the problem. *(Ch. 3)*

**Context.** The background information supplied to a model, including both what the user provides and what the system injects (chat history, user profile, retrieved documents). Providing sufficient and appropriate context is the single highest-leverage action a user can take. *(Ch. 3)*

**Context engineering.** The module in a chatbot that gathers additional information relevant to a prompt and inserts it before the model sees it. In cognitive terms it approximates attention. *(Ch. 1)*

**Context window.** The maximum length of text a model can consider at once. Because a chatbot's apparent memory is the resubmitted transcript, exceeding the context window causes earlier material to be dropped — which is why long conversations lose the thread. *(Ch. 1, Ch. 3)*

**Corpus.** The body of content on which a model was trained. Typically scraped from the internet, and therefore over-representing the famous, the Western, and the freely available while excluding the paywalled and the recent. *(Ch. 1, Ch. 2)*

**CRAAP test.** A framework for evaluating content validity — Currency, Relevance, Authority, Accuracy, Purpose — developed by librarian Sarah Blakeslee at the Meriam Library, CSU Chico. *(Ch. 4)*

**Currency.** In the CRAAP test, whether the production date of the information makes it relevant. Time bias can be introduced accidentally through a prompt. *(Ch. 4)*

**Cyborg approach.** Engaging AI as a collaborator, pushing one's own reasoning and structure into the tool rather than outsourcing the reasoning. Practiced by roughly ten percent of users. The term follows Donna Haraway's usage. *(Ch. 3)*

**Data extraction (as a verification technique).** Pasting an AI response into a separate session and asking a model to extract its factual claims as a list, in order to produce a checklist for verification. Labor-saving but itself fallible. *(Ch. 4)*

**Data sovereignty.** Concerns arising from the training of models on personal, sensitive, or child-related data without consent. *(Ch. 2)*

**Decoder.** The component that converts the final token representation into a probability distribution over the model's vocabulary. *(Ch. 1)*

**Deep learning.** A subfield of machine learning that uses artificial neural networks. Requires substantially more data and computation than other machine learning approaches. *(Ch. 1)*

**Deepfake.** Synthetic media that simulates a real person's likeness or voice without authorization. *(Ch. 2)*

**Deskilling.** The degradation of human capability that follows from sustained reliance on a tool. In the AI context, concerns center on critical thinking, writing, and creativity. *(Ch. 2, Ch. 3)*

**Digital watermark.** An embedded, machine-detectable marker indicating that media was AI-generated. Google DeepMind's SynthID is one example. Usually stripped by social media platforms when carried as metadata. *(Ch. 4)*

**Embedding.** See *vector*.

**Encoder.** The component that converts tokens into vectors. *(Ch. 1)*

**Ethics.** The systematic study of what is good or right. Operationally: where the engineer asks whether a thing *can* be built or used, the ethicist asks whether it *should* be. *(Ch. 2)*

**Executive function.** A domain of cognitive function: the ability to control and coordinate other cognitive abilities. In a chatbot, approximated by the safety and responsibility filter. *(Ch. 1)*

**FACT framework.** A framework for assessing AI tools: **F**airness, **A**ccountability, **C**onfidentiality, **T**ransparency. *(Ch. 2)*

**Feedback loop.** A source of bias in deployed systems, in which a model's predictions influence the world in ways that generate data confirming those predictions. *(Ch. 2)*

**Few-shot prompting.** Supplying several examples of the desired input–output pattern before the actual request. See also *one-shot*, *multi-shot*, *zero-shot*. *(Ch. 3)*

**Format.** One of the three levers of prompt engineering: the structure and style of the prompt and of the desired output — natural language, structured input–output pairs, or markdown. *(Ch. 3)*

**Functional implausibility.** A category of cue for identifying synthetic images: objects that could not perform their evident function — staircases to nowhere, non-supporting poles, asymmetrical fastenings. *(Ch. 4)*

**Garbage in, garbage out (GIGO).** The principle that output quality is bounded by input quality. Applied to AI: a biased corpus produces biased output, delivered with polish. *(Ch. 2)*

**Ghost work.** The labor — often performed in the Global South at low wages — of tagging training data and filtering toxic content, on which the apparent automation of these systems depends. *(Ch. 2)*

**Hallucination.** Misleading, inaccurate, or fabricated content in an AI response. Not a defect that better engineering will remove: a system that reliably declined to answer when uncertain could not function as a language generator. *(Ch. 3, Ch. 4)*

**Historical bias.** Bias arising because a model is trained on the historical record, which encodes past inequities. Treating output as objective truth therefore risks automating past injustice. *(Ch. 2)*

**Holographic memory.** The hypothesis that the definition of each discrete token of information is distributed across the entire vocabulary of tokens, so that every idea is defined in relation to every other. Contrasted with localized memory; the motivation for backpropagation. *(Ch. 1)*

**Human in the loop.** The person who exercises judgment over an AI system's output — and who bears responsibility for it. *(Ch. 2, Ch. 4)*

**Intersectionality.** In the bias context, the compounding of disadvantage where multiple marginalized characteristics coincide — a pattern that aggregate accuracy metrics conceal. *(Ch. 2)*

**Large language model (LLM).** A deep neural network that models natural language, representing words as numbers. Generates one token at a time and retains no memory between prompts. *(Ch. 1)*

**Lateral reading.** A verification method: leaving the source in front of you and opening other sources to check its facts, claims, references, and authorities. Break it down, search, analyze, decide, repeat. *(Ch. 4)*

**Lateral watching.** The application of lateral reading to images and video, including analysis of account age, history, and commercial motive. *(Ch. 4)*

**Local model.** A model run on one's own hardware, so that no data leaves the machine. Tools such as Ollama make this accessible without programming. *(Ch. 3)*

**Localized memory.** The hypothesis that discrete pieces of information are stored by defined collections of neurons and synapses, such that destroying the location destroys the memory. Contrasted with holographic memory. *(Ch. 1)*

**Machine learning.** A subfield of AI that uses statistical models rather than explicit logic. Requires data and computing power. *(Ch. 1)*

**Markdown Prompting Framework (MPF).** A structured prompting convention using markdown headings and lists to specify system prompt, role, audience, constraints, and a numbered task list. Prompts are reusable files, and the format compels the user to structure their thinking. *(Ch. 3)*

**Multi-shot prompting.** Supplying many examples before the request. Gains typically plateau somewhere around ten examples, content-dependent. *(Ch. 3)*

**One-shot prompting.** Supplying a single example of the desired input–output pattern. *(Ch. 3)*

**Open model.** A model whose weights are publicly available and can be inspected, downloaded, and run locally. Repositories such as Hugging Face host thousands, many domain-specialized. *(Ch. 3)*

**Parameter.** A numerical value inside a model, set during training and fixed thereafter. Contemporary models have billions to trillions. Interpreting them is difficult; the mechanism that uses them is not mysterious. *(Ch. 1)*

**Parametric memory.** The blending of training information into a model's parameters, such that the model retains what it learned without retaining where it learned it. The reason models cannot genuinely cite sources. *(Ch. 2)*

**Perceptron layer.** The classical neural network component within a transformer block, updating each token's representation independently of the others. Current research suggests these layers are where learned facts are stored. *(Ch. 1)*

**Perceptual motor control.** A domain of cognitive function: coordinating movement in response to physical surroundings. Among the hardest problems in AI, and not addressed by language models. *(Ch. 1)*

**Predatory publishing.** Journals that publish for fees without meaningful peer review. Now including venues whose contents are entirely AI-generated, sometimes attributed to real researchers. *(Ch. 4)*

**Prompt.** The text submitted to a model. In a chatbot, the model receives the accumulated conversation as a single block of text — the prompt is the model's only memory. *(Ch. 1, Ch. 3)*

**Prompt engineering.** The practice of structuring prompts deliberately. Its three levers are format, context, and tuning. *(Ch. 3)*

**Prompt injection.** An attack in which a model's instructions are manipulated to bypass its safety protocols. Of particular concern in agentic systems. *(Ch. 2)*

**Purpose.** In the CRAAP test, why the information was created at its source: fact, opinion, entertainment, satire, or propaganda. Applied to AI, purpose is doubled — the purpose of the original information and the purpose and bias of the tool. *(Ch. 4)*

**Relevance.** In the CRAAP test, whether the fact or argument is relevant to the question at hand, and for whom it was intended. *(Ch. 4)*

**Reproducibility.** The ability to obtain a consistent, verifiable result. A cornerstone of research, and not how these tools work, since word selection is a sampling process. *(Ch. 1, Ch. 2)*

**Response generation.** The chatbot module that samples a specific token from the model's probability distribution. **This, not the model, is where the randomness lives.** *(Ch. 1)*

**Retrieval-augmented generation (RAG).** Adding retrieved documents to the context window before generation. Improves the likelihood that a cited source exists; does not establish that the source supports the claim. *(Ch. 2)*

**Reverse image search.** Submitting an image to a service such as TinEye or Google Images to find where else it appears, trace it to an original source, or discover that it has been debunked. *(Ch. 4)*

**Safety and responsibility filter.** The chatbot module that screens prompts and responses for material the operator judges risky. Its primary motivation is protecting the operator from liability. Mechanisms are often simpler than assumed. *(Ch. 1)*

**Scaling laws.** The empirical regularity that larger models, with more layers and more training compute, perform better. No ceiling has yet been observed. *(Ch. 1)*

**Searchbot approach.** Using AI as a question-answering machine — either to obtain answers or to confirm existing beliefs. Practiced by roughly ninety percent of users. Associated with cognitive decline and with the unremarkable mean. *(Ch. 3)*

**Social cognition.** A domain of cognitive function: processing, remembering, and using information in social contexts. In a chatbot, approximated chiefly by the safety filter. *(Ch. 1)*

**Sociocultural implausibility.** A category of cue for identifying synthetic images: situations that are socially or culturally improbable. A red flag rather than a verdict — unlikely does not mean impossible. *(Ch. 4)*

**Stylistic artifact.** A category of cue for identifying synthetic images: waxy or plastic texture, absent skin texture, cinematization, hyper-real but unnatural detail, inconsistencies in resolution and color. *(Ch. 4)*

**SynthID.** A digital watermarking system for AI-generated media developed by Google DeepMind. *(Ch. 4)*

**System prompt.** Instructions supplied at the system level, above the conversational turn. In the Markdown Prompting Framework, denoted by a top-level `#` heading. Does not override the platform's own system context but coexists with it. *(Ch. 3)*

**Temperature.** A parameter controlling the flatness of the probability distribution from which the next token is sampled. At zero the model becomes deterministic and brittle; at high values output degenerates toward noise. Rarely exposed in graphical interfaces. *(Ch. 1)*

**Tensor.** See *vector*.

**Token.** The unit into which input is divided for processing. Usually smaller than a word — roughly corresponding to roots, prefixes, and suffixes. Audio and images can be tokenized as well. *(Ch. 1)*

**Tokenization.** The process of dividing input into tokens, according to predefined rules. *(Ch. 1)*

**Transformer.** The model architecture introduced in 2017 (Vaswani et al.), built around the attention mechanism. The basis of contemporary large language models. *(Ch. 1)*

**Tuning.** One of the three levers of prompt engineering: narrowing a model's general capability toward a specific domain. May be done programmatically (adjusting weights) or, more accessibly, through the prompt. Tuning introduces bias deliberately. *(Ch. 3)*

**Turing test.** A test in which an observer reads a transcript of a text exchange and attempts to identify which participant is human; the machine passes if it deceives the observer more than half the time. Contemporary models pass; so did ELIZA in 1966. *(Ch. 1)*

**Unremarkable mean.** The tendency of a broad, general question to elicit the average of what has already been written on the subject — the same answer everyone else receives, carrying no distinguishing value even when correct. *(Ch. 3)*

**Values.** What a person or society holds as important. Individual values function as an internal compass; social values are inherited through membership in communities and institutions. Ethics is values put into action. *(Ch. 2)*

**Vector.** An ordered list of numbers representing a token's position in a high-dimensional space, where proximity corresponds to similarity of meaning. Also called an *embedding*, a *tensor*, or an *encoding*. Contemporary models use hundreds to thousands of dimensions. *(Ch. 1)*

**Veracity.** The property of being true. A principal category of concern about AI systems, encompassing accuracy, reproducibility, and hallucination. *(Ch. 2)*

**Violations of physics.** A category of cue for identifying synthetic images: impossible reflections, inconsistent shadows, and lighting that does not follow from the apparent source. Among the most reliable indicators. *(Ch. 4)*

**Zero-shot prompting.** Supplying a direct instruction or question with no additional context or examples. The most used and least effective strategy, though legitimate for exploratory questions. *(Ch. 3)*
