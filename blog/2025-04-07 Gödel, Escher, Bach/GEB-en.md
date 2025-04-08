# [Book] Gödel, Escher, Bach: An Eternal Golden Braid (GEB)

[[Book] Gödel, Escher, Bach: An Eternal Golden Braid (GEB)｜Yasuhiro Inami / @inamiy](https://note.com/inamiy/n/nea36a55a60ab)

![GEB](images/godel-escher-bach.png)

(This is the English translation of the original blog post in Japanese, translated by Gemini 2.0 Flash)

When I started to become interested in mathematical logic, there was a book title I kept seeing: Gödel, Escher, Bach: An Eternal Golden Braid. Abbreviated as "GEB."

The author is Douglas Hofstadter. Published in 1979 and awarded the Pulitzer Prize the following year, this book explores contemporary themes such as "self," "consciousness," "life," "AI," and "computation," while traversing mathematical logic, art, and music. Its characteristic style involves weaving in allegorical dialogues and delving into thought from a unique perspective. It's a philosophical work, a scientific essay, and metafiction all at once—inviting readers into such a wondrous experience. The first Japanese edition was published in 1985, and a 20th-anniversary edition appeared in 2005. Despite being a massive work of over 700 pages, it continues to be read and loved by many.

It had been out of stock on Amazon for a long time, but I finally managed to get my hands on a copy a year before last. Overwhelmed by its sheer thickness, I left it unread for a while. However, as soon as I started reading, I was captivated by its difficulty and strange fascination, and before I knew it, I was deeply immersed in the profound swamp of GEB. In this article, I'd like to write about my reading experience (**spoiler alert below**).

## Introduction

The greatest appeal of GEB lies in how the author Hofstadter's exceptional knowledge is comprehensively interwoven across genres. Logic, programming, art, molecular biology, artificial intelligence, cognitive neuroscience, Zen—none of these are independent; every field is organically intertwined. This is solely thanks to the author's vast curiosity.

At the heart of this book is the **"self-reference" and its paradox** that appears in **"Gödel's incompleteness theorems."** Examples of self-reference in Japanese include sentences like:

- This sentence is false (the liar's paradox)
- This sentence has twelve characters.
- I am unprovable (Gödel sentence G)

All of these have a **cyclical structure** where the subject, such as "this sentence" or "I," refers to the sentence itself. And this circularity overlaps with what the book's subtitle, An Eternal Golden Braid, symbolizes.

The structure of self-reference frequently appears in the realm of art as well. The book introduces the ingenuity of this structure by using **Escher's impossible print "Waterfall"** and musical expressions like **Bach's canons and fugues** as examples. Especially regarding Escher, many of his works adorn the pages, and even if one is overwhelmed by the difficult content of the main text, simply being captivated by Escher's imagery makes encountering this book worthwhile.

<figure>
  <img src="images/escher.png">
  <figcaption>M.C. Escher, Waterfall, 1961, Lithograph</figcaption>
</figure>

However, if you want to deeply understand the "infinite circularity" that permeates Gödel, Escher, and Bach, the "Gödel" part, that is, **"logic,"** is something you inevitably cannot avoid. To remove this major hurdle, Hofstadter introduces simple formal systems at the beginning of the book. He carefully unravels the relationship between **syntax as "symbols"** and **"numbers" that give them meaning**, as well as the **isomorphism** that connects the two, from scratch. Personally, I don't recall reading any other book that handles the basics of formal logic so plainly and accurately, and it felt clearer than ever before.

However, before reaching the middle of the book, readers are confronted with a sudden appearance of **first-order predicate logic** and are required to understand classifications such as **primitive recursive, total recursive, and partial recursive functions**, one difficult point after another, sifting through the readers. Therefore, I personally felt that proceeding with just this one book would be a thorny path without prior study in logic or computer science.

If there is anyone reading this article who has hit a wall with logic, wandered through web searches, and ended up on such a narrow-minded blog—for your reference, I'd like to introduce some books on first-order predicate logic that I personally found helpful (in order of ease):

- Logic by Shigeki Noya
- Mathematical Girl / Gödel's Incompleteness Theorem by Hiroshi Yuki
- Logic in Information Science by Hiroaki Ono
- A Mathematical Introduction to Logic by Herbert B. Enderton

## Gödel's First Incompleteness Theorem

In this section, I will summarize Gödel's first incompleteness theorem within the scope of my understanding.

First, in logic, the standard flow is to learn the basics of propositional logic and then move on to **first-order predicate logic**, which serves as the starting point for discussing Gödel's incompleteness theorems. However, to handle complex structures like self-reference, this alone is not enough; a more powerful formal system that can treat **"numbers" as "terms"** is necessary. In GEB, such a formal system is called **TNT (Typographical Number Theory)**. This is a system that formalizes number theory and allows for self-reference, satisfying the following conditions:

- It is based on **first-order predicate logic**.
  - Function symbols and predicate symbols appear in logical formulas.
  - Existence of terms (internal structure) and their meaning.
- The **language system (formal system)** is sufficiently **powerful**.
  - It can handle number terms and primitive recursion (arithmetic's $${IΣ_1}$$ formalization, from a finitist perspective).
  - Gödel numbering is possible (symbol → number → number term).
  - Expressibility of primitive recursive functions and relations.

At the core of the idea of **self-reference** is the ability to construct the form $${p(⌜p⌝)}$$ by substituting a number term (written as $${⌜p⌝}$$), which is the encoding of $${p}$$ itself, into a 1-variable logical formula $${p(x)}$$. This is called **diagonalization (Quining)**. In ordinary logical formulas, notation like $${p(p)}$$ is not valid (because the term $${x}$$ and the logical formula $${p}$$ have different types), but using Gödel's construction, it becomes possible to **legally create a "logical formula that talks about itself" by substituting "its own code" as a term**.

This also appears in the context of computer science. For example, consider giving the code (data) $${⌜P⌝}$$ of a program $${P}$$ as input to itself. In von Neumann architecture, there is no distinction between program and data; both are stored as the same binary numbers in memory space. Therefore, within the dynamic interpretation by the CPU, the boundary between the two remains ambiguous, and it is theoretically possible for a program to execute itself with its own code as an argument.

This self-referential structure becomes clearer when considered within the framework of a **Turing machine**. First, let's implicitly acknowledge the existence of a universal function (universal Turing machine) $${Φ: ℕ×ℕ→ℕ}$$ (where $${ℕ}$$ is the set of natural numbers) such that for a program $${P: ℕ→ℕ}$$:

$$Φ(⌜P⌝, n) = P(n)$$

Here, $${Φ}$$ takes an encoded program $${⌜P⌝}$$ and an input $${n}$$ and returns the result as $${P(n)}$$. In other words, $${Φ}$$ implies that $${⌜P⌝}$$ can be **restored (decoded)** to the original $${P}$$.

A crucial point here is that this **universal function is not total**. That is, the program cannot be restored for every argument (natural number) in the domain. If we assume it is totally universal, then from the surjectivity (due to universality), $${Φ}$$ becomes a total surjective function (more precisely, a weakly-pointed surjective function, where the curried $${Φ': ℕ→ℕ^ℕ}$$ is surjective). Then, **Cantor's diagonal argument** can be applied, leading to a contradiction. Specifically, consider a $${ℕ×ℕ}$$ dimensional matrix representation (table, list) of $${Φ}$$, and analogous to collecting the results on the diagonal into a 1-variable program $${Φ(x, x)}$$, consider the imitation by the universal function for a 1-variable program $${P(x) = f(Φ(x, x))}$$ for any $${f: ℕ→ℕ}$$.

$$Φ(⌜f(Φ(x, x))⌝, n) = f(Φ(n, n))$$

Now, substituting $${n = ⌜f(Φ(x, x))⌝}$$, we get:

$$Φ(⌜f(Φ(x, x))⌝, ⌜f(Φ(x, x))⌝) =f(Φ(⌜f(Φ(x, x))⌝, ⌜f(Φ(x, x))⌝))$$

That is, for any $${f: ℕ→ℕ}$$, a fixed point $${\mathrm{fix}\ f = Φ(⌜f(Φ(x, x))⌝, ⌜f(Φ(x, x))⌝)}$$ exists.

In the general explanation of Cantor's diagonal argument, to show that the set of real numbers is larger than the set of natural numbers, a new real number $${Φ(x, x)}$$ is constructed by collecting the numbers on the diagonal of a $${ℕ×ℕ}$$ table $${Φ}$$ listing the real numbers in $${(0, 1]}$$, and then applying a clever manipulation $${f}$$ to it (e.g., if the $${x}$$ th decimal place is odd, make it 0; if even, make it 1). Then, by assuming that $${Φ(x, x)}$$ is equal to the $${k}$$ th real number in the table, it is shown that the $${k}$$ th decimal place $${Φ(k, k)}$$ does not match $${f(Φ(k, k))}$$, thus proving the assumption wrong.

In the context of Gödel's incompleteness theorem, we view a program that determines "Yes or No" as a 1-variable logical formula. Here, we rewrite the universal function as $${Φ: ℕ×ℕ→ 2}$$ ($${2}$$ is the Boolean type). By introducing the negation symbol $${¬}$$ for the manipulation $${f}$$, we get:

$$Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝) = ¬Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝)$$

Comparing both sides, the contradictory form $${G = ¬G}$$ emerges.

$$G = Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝)$$

This $${G}$$ is what is called the **Gödel sentence**.

In the book, instead of using a universal function, it takes the form of a logical formula concerning provability: $${Φ(⌜p⌝, x) = \mathrm{isProvable}(\mathrm{subst}(⌜p⌝, x)) = ∃p'. \mathrm{proves}(p', \mathrm{subst}(⌜p⌝, x))}$$ (this is a more common explanation):

- $${\mathrm{subst}(⌜p⌝, a) = ⌜p(a)⌝}$$ ⇔ The Gödel number of the sentence (closed logical formula) obtained by substituting the number $${a}$$ for the variable in the 1-variable logical formula $${p}$$
- $${\mathrm{proves}(p', x)}$$ ⇔ The predicate "the proof sequence with Gödel number $${p′}$$ can prove the sentence with Gödel number $${x}$$"
- $${\mathrm{isProvable}(x)}$$ ⇔ The predicate "the sentence with Gödel number $${x}$$ can be proven (using some proof sequence)"
- $${G = Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝) = ¬Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝) \\ = ¬\mathrm{isProvable}(\mathrm{subst}(⌜¬Φ(x,x)⌝, ⌜¬Φ(x,x)⌝)) \\ = ¬\mathrm{isProvable}(⌜¬Φ(⌜¬Φ(x,x)⌝,⌜¬Φ(x,x)⌝)⌝) \\ = ¬\mathrm{isProvable}(⌜G⌝)}$$⇔ The self-referential sentence " $${G}$$ (itself) is unprovable"

It is important to note here that $${\mathrm{subst}}$$ and $${\mathrm{proves}}$$ are **primitive recursive functions**, meaning they always finish computation within a finite time, but $${\mathrm{isProvable}}$$ is not (it is a **partial recursive function**). The difference arises because the **existential quantifier $${∃}$$ without an upper bound** appears in the logical formula, and **verifying its existence may require an infinite search**. Such logical formulas of the form "searching for one among infinity" are called $${Σ_1}$$ logical formulas. Furthermore, with $${IΣ_1}$$, which can handle number terms and induction, we can say we have a "sufficiently powerful formal system."

From the above, to avoid the contradiction of $${G = ¬G}$$, the universal function $${Φ}$$ and provability $${\mathrm{isProvable}}$$ must remain partial recursive functions. Therefore, to treat $${G=Φ(⌜¬Φ(x, x)⌝, ⌜¬Φ(x, x)⌝)}$$ as uncomputable, we are forced to conclude that **" $${G}$$ and $${¬G}$$ are both unprovable."** This fact is **"syntactically" incomplete**, hence the name **Gödel's first incompleteness theorem**. And due to this self-referentiality, **"provable" becomes a weaker concept than "true."**

💡 It is very important to distinguish whether "complete" or "incomplete" in logic refers to "syntactical" or "semantical" completeness.

As an aside, this discussion of Gödel's first incompleteness theorem is deeply connected not only to Cantor's theorem mentioned above but also to **Russell's paradox**, the **halting problem**, the **recursion theorem**, the **fixed-point combinator**, **Tarski's undefinability theorem of truth**, and the **`eval` function** in programming. A unified perspective for understanding this entire picture is Lawvere's fixed-point theorem, and the following literature is helpful:

- F. William Lawvere, "Diagonal arguments and cartesian closed categories" (1969).
- Noson S. Yanofsky, "A Universal Approach to Self-Referential Paradoxes, Incompleteness and Fixed Points" (2003).
- Tobias Reinhart, Sebastian Stengele, "Lawvere's Theorem" (2022)

## Life, AI, Self-Awareness

...So far, I have discussed the difficult topic of mathematical logic, but from this section, let's temporarily forget about it and delve into the "backside" of GEB. By "backside," I mean what I arbitrarily call the new scientific fields that emerged from the mid-20th century—**molecular biology, artificial intelligence (AI), cognitive neuroscience**—which did not yet exist (or were in their infancy) in the eras when past greats like Gödel, Escher, and Bach lived (this is Part 2 of the book). Hofstadter also provides readers with deep insights into ¬GEB.

### The "Central Dogma" in Molecular Biology

In GEB, to show that the structure of self-reference is not limited to the world of logic, the **"central dogma"** of molecular biology is discussed. The basic elements to keep in mind are as follows:

- **DNA** = Blueprint of life (sequence of bases A, C, G, T)
- **mRNA** = DNA information transcribed (**transcription**) (sequence of bases A, C, G, U)
- **Primary structure protein** = Sequence of amino acids (polypeptide) generated by **ribosomes** translating (**translation**) mRNA information
- **Tertiary structure protein** = The completed form of the primary structure protein that has physically folded. This three-dimensional structure allows some proteins to become **enzymes** with specific catalytic functions.

<figure>
  <img src="images/central-doma.webp">
  <figcaption>Central Dogma flow (excerpt from Wikipedia)</figcaption>
</figure>

What's interesting here is that the arrows in the diagram don't simply proceed in one direction and end. In reality, some of the proteins produced become "**devices that operate the next process itself**," such as DNA polymerase (DNA replication machinery), RNA polymerase (transcription machinery), and ribosomes + tRNA (translation machinery). And the created devices return to the flow of the central dogma. The diagram itself is a bit linear and difficult to understand, but in reality, **circularity occurs everywhere invisibly**.

Here, if we liken DNA, RNA, and proteins to "data" and enzymes to "programs," **the mechanism of life looks just like a computer**, which makes it all the more mysterious:

- Enzymes are a type of protein ⇔ Programs are a type of data.
- Proteins, by folding into a tertiary structure, can become enzymes ⇔ Data can become programs.
- Ribosomes + tRNA can synthesize almost all proteins via mRNA ⇔ Universal program.

Thus, we can see a **surprising similarity between the self-referential structure shown by Gödel and the mechanisms of life**.

And the following question about the "origin of life" is even more profound:

> To make a ribosome, certain proteins must already exist, and so must rRNA. Of course, for proteins to exist, ribosomes must already exist to make them. How could this vicious circle have arisen? Which came first—ribosomes or proteins?
>
> GEB Chapter 16 "Self-Reference and Self-Reproduction" p521

Personally, I only had fragmented knowledge of the central dogma before reading GEB. However, the moment I learned that **this grand process of life is actually continuous with symbolic logic and computation theory, and moreover, is self-referential**, my perspective on molecular biology completely changed. And I felt a pang of regret for my own blindness, having missed so many opportunities to touch such a deep and rich structure.

### Intelligence (AI)

The first edition of GEB was in 1979, so from the perspective of 2025, when AI is a hot topic, it might be called an ancient text from nearly half a century ago (forgive me). However, the descriptions of artificial intelligence at the time, even if somewhat dusty with age, still offer sharp insights.

For example, there is this passage:

> What is cruelly missing from artificial intelligence is the ability to "step back" and look at what is going on, and then to modify its approach to the task at hand in the light of this perspective. To write a program that is expert at some single task which seems to require intelligence when done by humans is quite a different thing from writing a program that is intelligent! It is the difference between the ant colony, whose rigid and stereotyped behavior can seem deceptively intelligent, and the human being who observes the ant colony.
>
> GEB Chapter 18 "Artificial Intelligence: Retrospects" p602

What Hofstadter is arguing here is that (at least rule-based) AI lacked **"metacognition"**—the ability to look at its own actions from a bird's-eye view, survey the situation, and flexibly adjust its course as needed. Without it. The act of observing oneself is also an entry point for referring to oneself and correcting one's own regularities and behaviors.

<figure>
  <img src="images/metarecognition.png">
  <figcaption>Metacognition (generated by ChatGPT 4o)</figcaption>
</figure>

So, what about 2025? The "frame problem" of artificial intelligence, once discussed as a philosophical issue, is now being resolved to some extent in practical terms due to the emergence and evolution of deep learning. Especially since 2022, the evolution of generative AI has been remarkable, reading context and producing unpredictable answers one after another without being bound by given frameworks, continuing to surprise us humans every day—here I wrote "us," but in an era where we must seriously consider, not as a joke, whether the one reading this sentence is truly human. Perhaps an AI is reading it right now.

In that case, the mechanism of "reading" sentences by AI is neither simple syntactic analysis nor just semantic analysis with a slight addition. As can be inferred from the fact that Transformer-based models, representative of recent large language models (LLMs), represent syntax and semantics in the same vector space, the **boundary between syntax and semantics almost merges** when AI understands natural language. Regarding this point, Hofstadter repeatedly and deeply delves into the importance of the **"tangled hierarchy"** that arises between syntax and semantics, drawing on Gödel's incompleteness theorems.

(My personal impression, not being well-versed in AI) Perhaps "our" thinking also deeply understands things by navigating a world where syntax and semantics are intricately intertwined, constructing a cognitive model internally, and layering metacognition on top of it. And just as human metacognition is imperfect and sometimes manifests in thoughts and words in a distorted way, AI is also not perfect and sometimes hallucinates. Moreover, there is no means, in principle, to perfectly prevent these errors in advance. This is also a point where GEB's claims and the limitations of AI resonate.

<figure>
  <img src="images/llm-transformer.webp">
  <figcaption>The Transformer architecture from "Attention Is All You Need" (2017). It is divided into a left Encoder part and a right Decoder part, each using self-attention mechanisms and feed-forward networks to capture syntactic and semantic relationships in pairs, deepening them through multiple layers.</figcaption>
</figure>

### Hardware and Software

Not limited to AI, in grasping the phenomenon of **intelligence** as a whole, Hofstadter emphasizes the difference between **"hardware" and "software"** as follows:

> Intelligence can be taken out of the hardware in which it resides and moved around. It has its own higher-level laws which depend on and yet are "detachable" from the lower level.
>
> GEB Chapter 11 "The Brain and Thought" p359

In other words, intelligence, while strongly dependent on the physical, "immutable" foundation in which it resides, also possesses a **"variable" nature** that can be abstracted and carried to other places. Moreover, this abstraction includes metacognition.

Considering this difference between hardware and software, and applying it to the large language models mentioned earlier, we can see the following interesting analogies:

- **Transformer (computational model)** = Fixed wiring = Hardware-like
- **Feature representation** = Numerical representation output by the self-attention mechanism (for input) = Software-like

If we apply this to molecular biology:

- **Central dogma** = Follows physical laws (fixed wiring) = Hardware-like
- **DNA (genetic information)** = Meaning in the sequence of A, C, G, T = Software-like

Furthermore, from the perspective of neuroscience:

- **Brain** = Network of neurons and synaptic connections = Hardware-like
- **Neural activity** = Signals by electricity and chemical substances, etc. = Software-like

And in mathematical logic:

- **Formal system** = Rigid symbols and inference rules = Hardware-like
- **Meaning by arithmetic** = The content of symbols (terms) is natural numbers = Software-like

(Note: Although I have used "hardware-like" and "software-like," this is a relative discussion, and "hardware" here does not necessarily mean physical matter.)

The common points among these are as follows:

- **(The entanglement of) software is supported by (the entanglement of) hardware.**
- The entanglement of software can change its own rules and lead to contradictions, but it is **(usually) indestructible to the higher-level hardware**.
  - Hardware operates without the permission of software.
- There are **many layers of entangled layers**.
- However, the **lowest level of hardware exists as matter and physical laws**.

Thus, Hofstadter believes that "our" **"self-awareness"** is born as a result of the boundary between hardware and software becoming ambiguous, entanglement calling forth entanglement, and self-referential structures being layered many times.

<figure>
  <img src="images/GEB-art.png">
  <figcaption>Example of human character art (generated by ChatGPT 4o). In this case, people are hardware, and letters are software.</figcaption>
</figure>

### Self-Awareness and Creativity

The greatest characteristic of a being with metacognitive abilities and the budding of self-awareness is **"creativity."** In this book, Hofstadter suggests that ultimately, neither the self nor the world surrounding it can be "completely understood." And while embracing these limitations, we still move forward, judge what is important, and continue to choose our path. He sees the essence of **artistic beauty and creativity** in such endeavors.

> The approach to creativity began when programs became opaque even to their creators.
>
> GEB Chapter 19 "Artificial Intelligence: Prospects" p662

The author's words above carry particular weight in modern times. Both humans and AI, precisely because they are creative, become beings that "we" cannot fully understand and cannot control.

By the way, in GEB, as an explanation using mathematical logic, there is a discussion of adopting either the Gödel sentence $${G}$$ or its negation $${¬G}$$, which could lead to contradictions in a sufficiently powerful formal system of arithmetic $${IΣ_1}$$, as a new axiom. The former $${IΣ_1+G}$$ is called the **standard model**, and the latter $${IΣ_1+¬G}$$ is called the **non-standard model**.

In the case of the standard model $${IΣ_1+G}$$, it is possible to extend the theory of natural numbers to a broader system including integers, rational numbers, irrational numbers, and imaginary numbers. Moreover, even after the extension, the basic properties of natural numbers are preserved. This **axiomatic extensibility can be considered one of the essences of creativity**.

A similar story can be found in the **history of human scientific discovery**. In the paradigm shift from classical Newtonian mechanics to quantum theory, the old laws were not completely discarded but continue to live on, contained within the new theory. On the other hand, even with the full mobilization of modern theories including quantum theory, we have not reached a complete understanding of everything. It is believed that this is because we cannot escape Gödel's incompleteness. However, it is possible to extend and continue to understand theories. Therefore, "our" curiosity will never cease.

> 💡 On the other hand, if we turn our attention to the non-standard model $${IΣ_1+¬G}$$, the story becomes even more complicated. For example, if we add a new element to the set of all natural numbers $${N}$$, then $${1⊕N=N}$$ while $${N⊕1≠N}$$ (where $${⊕}$$ is not the usual sum of natural numbers but the sum of ordinals). Such strange non-commutativity that appears in this world might also be related to the story of creativity, but since I don't understand anything at this point, I won't delve any further (or rather, don't want to).

Let's get back to the main topic.

Hofstadter also talks about creativity as follows:

> What a poor mental life we would have if we lacked the creative ability to slip out of the real and into the soft "what ifs"!
>
> GEB Chapter 19 "Artificial Intelligence: Prospects" p632

> One must be able to bend concepts at the right times. Nothing is absolutely rigid. On the other hand, things must not be so flimsy that they can mean anything at all. The trick is to know when and how to let one concept slip into another.
>
> GEB Chapter 19 "Artificial Intelligence: Prospects" p644

The concept of **"slippage (considering 'if')"** plays a particularly important role in this context. Perhaps its mechanism lies in the variability of the variables contained in the functions and predicates in first-order predicate logic. Using the technique of Gödel numbering and incorporating another logical formula as a term into an expression as if slipping types, the logical system itself expands into realms such as self-reference, contradiction, fantasy, and fiction. What is born from this is a freer and more imaginative space for thought. As long as "we" love creativity, we also love fiction. And that fiction sometimes intersects with the horizon of reality and even takes on the potential for realization.

### Zen (Ism)

GEB can also be read as an unexpected gateway to the world of **Zen Buddhism**. Chapter 9 of the book, "Mumon and Gödel," richly introduces Zen kōans (paradoxical questions or anecdotes for practitioners to reach enlightenment) and their explanations.

For example, there is this famous line from a kōan:

> A monk asked Zhaozhou, "Has a dog Buddha-nature or not?" Zhaozhou said, "無 (Mu)."
>
> The Gateless Gate, Case 1, Zhaozhou's Dog - Wikipedia

As is well known, this **"無 (Mu)"** is not simply a negative "No." It is a deliberate retort to strike at the essence of a question that cannot be grasped by words or logic. It aims to overturn the assumptions behind the question and fundamentally shake the disciple's thinking. In this way, Zen is an intellectual attempt beyond logic, using the limitations of language to continue questioning the complexity of reality. To develop a transcendent dualism with a self-referential structure, rather than traditional dualism, it throws unfamiliar readers into a vortex of confusion.

Usually, in our daily lives, we passionately talk about the "meaning of life" or "xxx-isms." Sometimes, this leads to fruitless arguments. However, the Zen approach transcends such individual positions and claims, attempting to see the whole from a meta-perspective. In this book, such an attitude is deliberately called **"Ism"** without a prefix.

> To suppress perception, to suppress logical, verbal, dualistic thought—that is the essence of Zen, the essence of Ism.
>
> GEB Chapter 9 "Mu Mu and Gödel"

My own understanding is as follows: This "Ism" can be thought of as something that negates the validity of any local "-ism," claim, or proof $${p}$$. Here, let's call it the predicate $${\mathrm{muIsm}}$$. Also, if we define $${\mathrm{ism}(p,x)}$$ as when a claim of a certain $${p}$$-ism can make a true/false judgment about a matter $${x}$$ (e.g., asking a believer, "Is $${x}$$ God?"), then this becomes similar to the previously mentioned 2-variable predicate concerning proof, $${\mathrm{proves}(p,x)}$$.

$$\mathrm{muIsm}(x) = ∀p. (¬\mathrm{ism}(p, x)) = ¬∃p. \mathrm{ism}(p, x) \\ = ¬∃p. \mathrm{proves}(p, x) = ¬\mathrm{isProvable}(x)$$

Therefore, in the world of "Ism" ($${\mathrm{muIsm}}$$), one slips through every question ($${x}$$) without answering, like a Zen kōan. Because it cannot be proven. And asking about "Ism" within "Ism" becomes equivalent to diagonalization with self-reference.

$$\mathrm{無} = \mathrm{muIsm}(⌜\mathrm{muIsm}⌝) = ¬\mathrm{isProvable}(⌜\mathrm{muIsm}⌝)$$

This is how I interpret "無". This form somehow reminds me of the Gödel sentence $${G=¬\mathrm{isProvable}(⌜G⌝)}$$. "無" cannot be proven even by those who believe in "Ism."

## Conclusion

In this way, through GEB, it becomes clear that the cyclical structure of "self-reference" transcends the realm of mere logical puzzles and paradoxes, becoming a profound theme that spans diverse fields such as mathematics, art, and science. The way concepts like infinity and recursion are not limited to abstract play but connect to the complex systems of reality and the very formation of intelligence is truly impressive.

Although I couldn't write about it this time, the perspective of "self-reference" seems applicable to phenomena such as dissipative structures in non-equilibrium systems and the formation of emergent patterns. There, too, a path to new understanding might be found.

Finally, I would like to once again express my gratitude to the author, Douglas Hofstadter, for brilliantly weaving together a vast amount of knowledge into a single work and providing intellectual excitement. And with respect for the predecessors who achieved the numerous discoveries behind it, I will conclude this review.

<figure>
  <img src="images/godel-escher-bach-hofstadter.png">
  <figcaption>Gödel, Escher, Bach, and Douglas Hofstadter (generated by ChatGPT 4o)</figcaption>
</figure>
