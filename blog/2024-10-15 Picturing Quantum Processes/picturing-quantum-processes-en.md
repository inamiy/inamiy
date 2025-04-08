# [Book] Picturing Quantum Processes: A First Course in Quantum Theory and Diagrammatic Reasoning

[Book Review: An Introduction to Categorical Quantum Mechanics | Yasuhiro Inami / @inamiy](https://note.com/inamiy/n/nb919778c28e7)

![](images/picturing-quantum-processes.webp)

(This is the English translation of the original blog post in Japanese, translated by Gemini 2.0 Flash)

For the past year or two, I've been dedicating my hobby time to studying quantum theory in between my main professional duties. Recently, I finally finished reading [『圏論的量子力学入門』（An Introduction to Categorical Quantum Mechanics）by Bob Coecke and Aleks Kissinger, translated by Haruyuki Kawabe](https://www.amazon.co.jp/dp/4627170114), and I was deeply impressed by its content. While the lingering emotions are still fresh, I'd like to jot down my thoughts on this book.

[『圏論的量子力学入門』(An Introduction to Categorical Quantum Mechanics) | Bob Coecke, Aleks Kissinger, Haruyuki Kawabe | Book | 通販 | Amazon](https://www.amazon.co.jp/dp/4627170114)

[inamiy: "After many twists and turns, I finally finished reading 'An Introduction to Categorical Quantum Mechanics' after about a year. I was deeply moved by how easily ZX-calculus could explain such difficult quantum theory. It might be the most influential quantum theory reference book I've ever read." — Bluesky](https://bsky.app/profile/inamiy.bsky.social/post/3l64ruu6sfs2l)

## Introduction (About Categorical Quantum Mechanics)

**"Categorical Quantum Mechanics"** is, as the name suggests, an academic field that aims to elucidate the mathematical structure of quantum mechanics using "category theory," a foundational area of mathematics. This field is relatively new, experiencing rapid development over the last two decades. However, this book doesn't delve heavily into category theory itself. With a basic understanding of quantum theory and linear algebra at the undergraduate first or second-year level, one can read it without any prior knowledge of category theory. The reason for this is that most of this nearly 900-page tome is filled with **"string diagrams,"** which are "pictures of boxes and wires." Furthermore, the explanations for each diagram (and its proof) are exceptionally thorough. Therefore, progressing through this book feels akin to being slowly read a picture book, making it a gospel for those (like myself) who faint at the sight of complex mathematical formulas filled with Dirac's bra-kets and tensor symbols. Moreover, in the latter half of the book, **"spider (multi-legged node) diagrams"** and **"ZX-calculus"** appear as further extensions of string diagrams. By decomposing the contents of the boxes into "nodes with phase information" and representing "complementarity," a crucial property of quantum theory, in two colors, one can enjoy even simpler and more colorful diagrams.

Incidentally, the original English title is "[Picturing Quantum Processes: A First Course in Quantum Theory and Diagrammatic Reasoning](https://www.amazon.co.jp/dp/110710422X)." The cover features an enigmatic dodo bird and an illustration of quantum teleportation, and the absence of "category theory" in the title gives a more approachable impression compared to the Japanese translation. On the other hand, the lack of explicit emphasis on the author's proposed "quantum picturalism" creates an interesting gap.

It's also worth noting that this book falls under the category of "quantum information science" rather than the physics of "quantum mechanics." The historical background of quantum mechanics is limited to standard topics like Young's double-slit experiment and the Stern-Gerlach experiment. Those seeking the romance of the history and development of physics might find it somewhat lacking. However, for theorists who haven't yet encountered category theory, the sharp insight with which these experimental contents are explained succinctly using only diagrams, without mathematical formulas, will surely leave them in awe. In any case, it's recommended to set aside the knowledge cultivated in traditional quantum mechanics and proceed by reading this as an entirely new book on quantum information. As you delve deeper, the remarkable correspondence between "traditional quantum mechanics" and "categorical quantum mechanics" should gradually emerge.

## String Diagrams

In 『圏論的量子力学入門』 (An Introduction to Categorical Quantum Mechanics), **"string diagrams"** take on a central role, replacing traditional formula-based quantum theory. String diagrams visually represent "monoidal categories" in category theory, providing a thinking framework for handling composite systems through tensor products. They can be widely applied to various process theories. If the reader has ever drawn any kind of flowchart or relationship diagram on a whiteboard, as shown in the figure below, they may have already been unconsciously using string diagrams.

<figure>
  <img src="images/string-diagram.webp">
  <figcaption>Example of a string diagram. It consists of boxes (morphisms) and wires (objects) (parentheses indicate category theory terms)</figcaption>
</figure>

In this book, (in the categorical sense) string diagrams are finely classified into "circuit diagrams," "general diagrams," and "(what this book calls) string diagrams." In category theory, these correspond to "strict symmetric monoidal categories," "traced strict symmetric monoidal categories," and "dagger compact (symmetric monoidal) closed categories," respectively, with the latter becoming increasingly powerful in terms of diagrammatic reasoning.

For example, a circuit diagram is like an electronic circuit. Connecting the input and output of the same gate can create a feedback loop, potentially damaging the gate. Similarly, in programming, inputting the output of a function back into the same function can create non-terminating recursion. In both cases, allowing loops can lead to the world going haywire (i.e., creating contradictions).

This idea can be similarly applied to the time-series world of events. It's generally considered normal that an event that has occurred once does not occur again at the same time and in the same way by going back in time. In other words, the time series follows causality, and the arrow of time moves in only one direction, without time leaps like in fiction movies. This is within the bounds of our common sense.

<figure>
  <img src="images/string-diagram2.webp">
  <figcaption>Example: A string diagram of a cooking recipe. There are no loops in the cooking process. Note that writing this diagram in mathematical notation (or programming style) would look like: (crack ⊗ crack ⊗ id) ▹ (id ⊗ swap ⊗ id) ▹ (whisk ⊗ beat ⊗ id) ▹ (id ⊗ stir) ▹ fold. Source: Crema di Mascarpone and Diagrammatic Reasoning | Graphical Linear Algebra</figcaption>
</figure>

However, in quantum theory, according to the Born rule, it is possible to calculate the trace of a matrix, allowing for loop structures back to the event itself in the diagram, as if going back in time (general diagrams). If this concept of self-loops is further promoted, it even becomes possible to "freely connect with other events (inputs connected to inputs, outputs connected to outputs)," breaking the causal relationships in the quantum world (due to the compactness property of string diagrams). This leads to the establishment of new physical theories and computational systems that were unimaginable with conventional wisdom, such as **"quantum entanglement"** and its application, **"quantum teleportation."**

<figure>
  <img src="images/teleportation.webp">
  <figcaption>Example of quantum teleportation. Using a quantumly entangled Bell state between Alice and Bob, a quantum state can be instantaneously transferred. (However, Bob doesn't know anything about the correction $${f}$$ until he receives classical information separately from Alice)</figcaption>
</figure>

## Dualization of String Diagrams

The first highlight of this book is in Chapter 6, where the **dualization of string diagrams** usable in classical theory is performed to make them applicable to the non-deterministic system of quantum theory, as one transitions from a classical probabilistic statistical framework to the quantum realm. This corresponds to the categorification of von Neumann's introduction of density operators and projection operators when formalizing quantum mechanics. This allows for the visual manipulation of the quantum world while preserving the properties of string diagrams.

The book first constructs the **"category of pure quantum maps"** by dualizing the classical **"category of linear maps."** Here, dualization means taking the adjoint of the original linear map and arranging the two maps in parallel. In the category of pure quantum maps, these are bundled together as a single map, and this category also satisfies the properties of string diagrams. However, it's important to note that this process does not mean that "classical behavior can be directly transplanted into the quantum world." For example, even if one dualizes a classical copying map, it's impossible to create a (pure) quantum map that copies an arbitrary quantum state (no-cloning theorem).

<figure>
  <img src="images/pure-quantum-map.webp">
  <figcaption>Definition of a pure quantum map (quoted from the book). A dualized linear map f is combined into a single map f^.</figcaption>
</figure>

After this dualization, the book introduces **discard effects** to extend to a more general and mixable **"category of quantum maps."** Discard is a quantum effect that cannot be expressed by dualization and corresponds to ignoring a part of the quantum system. Here, by slightly modifying the form of a quantum map (completely positive map), the Kraus representation $${Φ(ρ)=Σ_iK_iρK_i^†}$$ is easily obtained. Therefore, according to Choi's theorem, a quantum map is a CP (completely positive) map, and even if a quantum map is applied only to a subsystem of a quantum state, the property of the overall system being a quantum state (completely positive) is preserved.

Furthermore, by adding **quantum non-determinism**, it evolves into the **"category of quantum processes."** Although a complex temporary non-deterministic diagram is used at the stage of Chapter 6, even at this point, a rough understanding of the flow of quantum teleportation can be achieved.

Then, after understanding the mechanism of bridging quantum and classical systems through Chapter 7's "quantum measurement" (measurement by orthonormal basis, projection measurement, POVM), Chapter 8 introduces **"spiders (multi-legged nodes)"** and their diagrams, which refresh the complexity of non-determinism. This leads to an extension to the **"category of classical-quantum maps,"** including the concepts of quantum measurement and decoherence.

## Spider (Multi-legged Node) Diagrams

<figure>
  <img src="images/spider.webp">
  <figcaption>Spider (multi-legged node) diagram and fusion rule</figcaption>
</figure>

As shown in the figure above, a **spider (multi-legged node)** is a node with an arbitrary number of legs in the shape of a spider, and its definition is a "giant Kronecker delta symbol (multivariable version)." In other words, each orthonormal basis (state and effect) inside the spider synchronizes, and their sum is taken. Specific examples include the resolution of identity $${\sum_{i,j} \delta_{ij} |i\rangle \langle j| = 1}$$, copying $${\sum_{i,j,k} \delta_{ijk} |ij\rangle \langle k|}$$, and XOR operation $${\sum_{i,j,k} \delta_{ijk} |i\rangle \langle jk|}$$. In mathematics, this is called a "Frobenius algebra," possessing both monoid and comonoid properties while satisfying the Frobenius condition. Further development of this leads to "dagger special symmetric Frobenius algebras (isomorphic to C\*-algebras)," and important rules for basic spider operations, such as the "fusion rule," are incorporated into diagrammatic calculations. The fusion rule allows for the simplification of diagrams by reducing the number of spiders that have proliferated within the diagram.

Here, there are two types of spiders: **"dualized quantum spiders,"** which are connected only by double wires representing the quantum world, and **"single classical spiders,"** which include some classical connections. It's important to note that the fusion rule "prefers classical spiders." That is, once a classical spider mixes into a diagram, the surrounding quantum spiders connected by wires (which have good quantum properties) are caught up in its classicalization (quantum measurement or decoherence) and are considered non-existent. In other words, the collapse of the wave function occurs, and classical information is extracted or ignored (= classical deletion).

<figure>
  <img src="images/spiderman.webp">
  <figcaption>Dualized spider</figcaption>
</figure>

Note that this classical information, unlike quantum information, cannot be instantaneously transmitted faster than the speed of light, thus preserving Einstein's theory of relativity and the causal law of time. Therefore, looking at the overall diagram of quantum teleportation mentioned earlier, it is necessary to separately transfer the classical information $${i}$$ to convey the correction $${f_i}$$, and as a result, it is concluded that (classical) information cannot be shared instantaneously.

## Multi-colored Phase Spider Diagrams

Chapter 9 details **"phase spiders"** and **"colored spiders,"** which are further refinements of spiders. For the former, the concept of **relative phase** is added to spider diagrams, and since the phase forms a commutative group, the phases are summed when quantum spiders are fused. For the latter, by adding **quantum complementarity**, spiders can be distinguished by assigning them colors.

<figure>
  <img src="images/phase-spider.webp">
  <figcaption>Complementary two-colored spiders with phases and an example of their rules. Source: Quantum Picturalism: Learning Quantum Theory in High School | Abstract</figcaption>
</figure>

Interestingly, there's a property that "when two complementary spiders of different colors are connected by two wires, those wires can be considered non-existent." This is the definition of complementarity, and its mathematical background lies in Hopf algebras. By choosing self-adjoint orthonormal bases (e.g., the Z-axis and X-axis directions of the Bloch sphere) for the two complementary colors, the antipode of the Hopf algebra becomes the identity map. Furthermore, the rules of bialgebras (which are the parent class of Hopf algebras and also possess both monoid and comonoid properties) are incorporated into diagrammatic calculations (strong complementarity).

Once one understands spiders and their complementary properties, it finally becomes possible to interpret the mechanisms of **"Stern-Gerlach experiment,"** **"quantum cryptographic communication,"** and **"quantum non-locality,"** among others, using only diagrams without mathematical formulas (although simple mental arithmetic with phases is required). With this, one can finally read the quantum teleportation diagram using spiders on the original cover and stand shoulder to shoulder with the dodo bird.

## ZX-calculus

<figure>
  <img src="images/zx-diagram.webp">
  <figcaption>Calculation rules of ZX-calculus</figcaption>
</figure>

**ZX-calculus** is a specialization of the multi-colored phase spider diagrams from the previous section to the case of a single qubit (two-dimensional complex vector space $${ℂ^2}$$). From two-colored phase spiders (phase gates) and the quantum CNOT gate, one can construct quantum circuits for an arbitrary number of qubits. The book introduces Clifford diagrams (where phases are limited to integer multiples of $${π/2}$$, allowing for the simulation of classical computation) and Clifford+T diagrams (where phases are limited to integer multiples of $${π/4}$$).

Furthermore, ZX-calculus serves as a tool for deciphering quantum algorithms. The book covers the Deutsch-Jozsa algorithm, quantum search, and the hidden subgroup problem, using "quantum oracles" that unitarize arbitrary functions using complementarity.

## My Thoughts on the Book

In addition to the above, this book meticulously explains the basics of string diagrams, their applications to linear algebra, classical logic gates, relations (and their category), and Hilbert spaces from scratch, resulting in a very well-structured composition that considers beginners. Moreover, the author's skill in skillfully separating the abstract discussions of category theory from the main narrative, so as not to burden the reader, shines through. Perhaps my introduction to this article should have followed a similar approach.

Personally, I was particularly moved and pleased by the following points:

  - The density operator and Kraus representation, which I learned in university, can be expressed using diagrams of quantum maps (dualization and discard).
  - The resolution of identity, also learned in university, is closely related to COPY and XOR, familiar from programming, and can be generalized to the spider of the giant delta symbol.
  - The Stern-Gerlach experiment, another topic from university, can be easily shown using spider diagrams.
  - The mechanisms of pioneering technologies such as quantum teleportation and quantum cryptographic communication can be understood even by non-experts.

Looking at this list, I am reminded that my excitement often arises not from entirely new concepts (such as quantum algorithms for me) alone, but more often from unexpected connections with known concepts.

## Summary

As I wrote at the beginning, 『圏論的量子力学入門』 (An Introduction to Categorical Quantum Mechanics) is a groundbreaking masterpiece of quantum theory that breaks away from the traditional formula-centric approach and heavily utilizes diagrams. Coupled with its thorough explanations, anyone with a basic understanding of linear algebra and quantum theory at the university freshman or sophomore level can comprehend the book's content.

The only drawback is its high price of 13,200 yen. However, considering the volume and quality of the content, it is well worth the investment. I highly recommend interested readers to embrace the "shut up and take my money" spirit and give it a read. Personally, it is the most impactful quantum theory book I have ever read.

## References

"Quantum in Pictures," which summarizes the "spider diagram" story introduced in this blog post in a simpler way, is published by the same authors (it's in English, but the Kindle version is reasonably priced).

  - [Amazon.co.jp: Quantum in Pictures: A New Way to Understand the Quantum World (English Edition) 電子書籍: Coecke, Bob , Gogioso, Stefano: 洋書](https://www.amazon.co.jp/dp/B0BTTLDFT7)

Here is a book with an even stronger mathematical focus (a good book, but personally, I recommend buying the dodo bird first):

  - [圏論的量子力学 | Chris Heunen, Jamie Vicary, 川辺治之 |本 | 通販 | Amazon](https://www.amazon.co.jp/dp/4627157215)

Finally, for an introduction to string diagrams for beginners and their application to linear algebra, there are many articles available online. For example, the following are helpful:

  - [String Diagram を学ぶ -- カテゴリー論入門 (1) | Maru Labo]([https://www.marulabo.net/docs/category01/](https://www.marulabo.net/docs/category01/))
  - [【ストリング図で学ぶ圏論 #1】圏の定義と具体例 | Mathlog](https://mathlog.info/articles/cXg7yUBgxVoiDZYdu96l)
  - [図式で学ぶ線形代数 #1 ～図式の基礎と線形代数の基礎～｜Kenji Nakahira](https://note.com/kenji_nakahira/n/n5c9b86a59af5)
