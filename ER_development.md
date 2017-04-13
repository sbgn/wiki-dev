Survey on clarification of the "outcome"
----------------------------------------

In SBGN Entity Relationships L1V1, an "outcome", visualised by a black disc, represents the truth of a statement, such an interaction or a variable assignmment. One can then use the outcome as an interactor, or as the source of an influence. Over the past few years, we have discussed much of the meaning of the outcome. Such discussions can be found at:

[SBGN-6 Breakouts - Differentiating continuant and occurrent entities](SBGN-6-Breakout-Topics#differentiating-continuant-and-occurrent-entities)

<https://lists.caltech.edu/pipermail/sbgn-discuss/2011-February/000475.html>

<https://lists.caltech.edu/pipermail/sbgn-discuss/2011-April/000578.html>

Prior to HARMONY 2011, the outcome was interpreted by some as the result of the statement (e.g. a complex created by an interaction) or the statement itself becoming true (e.g. the interaction itself). SBGN aiming to be unambiguously interpreted, this was an unsatisfactory situation. During HARMONY 2011, the discussion led to the conclusion that for most people (not all since the specification is fuzzy on this point), the outcome

-   currently\* represents a restriction of the possible states of the

participants. For an interaction between an entity A and an entity B, the outcome of an interaction between A and B would represent (the instances of B bound to A) AND (the instances of A bound to B). This interpretation was confirmed without dissent by the participants of COMBINE 2011.

This let us to the question of representing the interaction itself, or a phosphorylation event (by opposition to the phosphorylated entity) etc. It was proposed (see discussions referenced above) to create another glyph.

------------------------------------------------------------------------

A vote was opened on September 9th 2011 and closed on September 30th 2011. 8 votes have been expressed. Two questions aimed at assessing the background understanding of the specification, and two questions aimed at taking decisions.

1. In your understanding of the current ER specification, what can be represented by an entity glyph

|                                   | yes | no  | not sure |
|-----------------------------------|-----|-----|----------|
| a material entity (e.g. molecule) | 7   | 1   | 0        |
| a process (e.g. glycolysis)       | 1   | 4   | 3        |
| a variable (e.g blood pressure)   | 2   | 2   | 4        |

Comments: "An entity can be anything..."

While the answers are diverse, a trend emerges to say that an ER entity is currently representing continuants and not occurrents. This calls for the creation of another glyph to represent occurrent. That issue will be the topic of a further vote.

2. In your understanding of the current ER specification, what does the outcome of an interaction represent?

|                                               |     |
|-----------------------------------------------|-----|
| A material complex formed by the interactors? | 7   |
| The interaction itself when realised?         | 0   |
| None of the above                             | 1   |
| Not sure                                      | 0   |

Comments: "It's the result of the interaction where both entities are in a bound state. But NOT a new complex entity."

There seems to be a consensus here that the current outcome represents a continuant, whether material complex, or restriction of the states of the participants.

3. There is a proposal to split the ER "outcome" glyph into the current filled disk, that would then represent the result of a statement, e.g. a complex, and another symbol, representing the realisation of the statement, e.g. an interaction. Do-you agree with this proposal?

|        |     |
|--------|-----|
| yes    | 6   |
| no     | 6   |
| unsure | 1   |

Comments: "I think the working of this question is not clear. I'm not sure what is the diff between result and realisation"

Decision: Creation of two outcome glyphs, with the current one representing the result of the interaction.

4. Several proposition were made to represent the new outcome. An empty square would remind of the process in Process Descriptions, and the activity in Activity Flows. But it would potentially be confusing with the cardinality of an interation, also represented by a square (but tangent to the interaction arc). A filled square would remind of the current outcome, but may be confused with the circle outcome if too small. If we introduce a new glyph to represent the realisation of a statement, should it be:

|               |                                 |
|---------------|---------------------------------|
| filled square | 1                               |
| empty square  | 4                               |
| Others        | 2 ("Not sure.", "empty circle") |

Decision: The outcome glyph representing the interaction itself will be an empty square.

Domains, sites and motives
--------------------------

SBGN ER Level 1 Version 1 does not provide structures to represent physical or functional subdivisions of entities. Nevertheless, it is clear that domains are important, and that people want, and need, to represent them.

Different approaches have been proposed so far, in particular the nesting and the subdivision. Both have advantages and disadvantages. Nesting is closer to the underlying, or conceptual, representation, and will probably be favored by computer scientists. Subdivision is closer to the physical structure of the entities and to what we draw in the back on an envelop and in a power-point presentation. It will likely be preferred by biologists. Designing a consistent and robust system will require a significant amount of work and discussion and this page provide materials to base the discussion.

### Proposal by Kurt Kohn

Kurt Kohn proposed a comprehensive proposal to encode structures using subdivisions.

-   [detailed proposal](uploads/Proposal-FineStructure.doc) to represent internal structures of entities.
-   [map of p53](uploads/P53-structure.pdf)
-   [explanation of the map](uploads/P53-structure-description.doc)

### Proposal by Michael Blinov

A proposal for hierarchical nesting of entities. It provides a description of domains, sites and individual atoms of biomolecules. The proposal is designed to cover all the requirements and capabilities of subdivision proposal of MIM group. The proposal is consistent with rule-based description used in BioNetGen software and it is expected to be consistent with SBML level 3 extension describing multi-state multi-component species.

-   [Proposal (pdf)](uploads/SBGN-hierarchical-blinov.pdf) to represent internal structures of entities usinh hierarchical nesting.
-   [MS Word file](uploads/SBGN-hierarchical-blinov.doc).
-   [Inkscape file](uploads/SBGN-hierarchical-blinov.svg) with all pictures used in the proposal.

Chylek et al. published a paper on "Guidelines for visualizing and annotating rule-based models" (http://www.ncbi.nlm.nih.gov/pubmed/21647530) describing a human-readable (vs machine-readable, as the main focus of SBGN efforts) way to describe rule-based models. This approach can be restricted to the SBGN domain to describe multi-component multi-state features, as illustrated in [this figure (pdf)](uploads/Chylek2011.pdf)

### Current state of discussion

[Minutes of the discussion at SBGN 5 in Stanford](Entity_Relationship_domains)