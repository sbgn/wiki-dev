Creation of an equivalence node to link generics and specifics
--------------------------------------------------------------

The necessity to convey the idea that a given EPN represents an entity that is in fact a generic form of other entities, represented by other EPNs in the same map, has been around for a long time. It was already mentioned in annex C.4 page 68 of SBGN PD L1V1.0, released in 2008.

An example of genericity would be a "generic gene product" representing a group of orthologous gene products that we do not need or want to discriminate. For instance, protein Erk, meant to represent any of the proteins Erk1 and Erk2. Another example would be a "generic protein" representing many different variants. For instance, a protein Erk-P meant to represent any state of phosphorylation of Erk.

For more information, one can consult the detailed document written by Emek Demir for the needs of BioPAX: <http://archive.biopaxwiki.org/GenericParticipants>

The first focused discussion on the topic took place at the SBGN forum 2009 in Palo Alto. We have an [audio recording of the event](http://sbgn.org/files/Discussion_Generics_SBGN5.mp3).

Alexander Mazein later [proposed an "identity gate"](https://utils.its.caltech.edu/pipermail/sbgn-discuss/2010-October/000306.html) that essentially provided a mean to represent the link between generics and related specifics. He presented the use of this glyph at COMBINE 2010 in Edinburgh. We have [a video of his presentation](http://sbml.org/Special/Events/COMBINE-2010/mazein-2010-10-08.mov).

Finally, we had a long discussion about the issue at COMBINE 2011 in Heidelberg. The [video is also available](http://co.mbine.org/sites/combine/files/2011-09-06-combine-mazein.mov).

Although all the issues are not totally settled, and in particular the rules and restrictions of use are not fully defined, it seems there is a consensus for the use of an "equivalence gate". It would be represented by a circle (like all the other logical gates) containing the symbol "equivalence" (LaTeX \\equiv). This gate would be attached on each side to equivalence arcs, that is arcs without specific end-symbols. On one side there could be only one arc, linking to the generic EPN. On the other side there could one or more arcs, linking to the specifics.

------------------------------------------------------------------------

A vote was completed on 27 Sep 2011.

### "Do-you agree that we need a symbol to explicitly link generics and specifics depicted on the same map?"

| Choice   | Votes | Fraction |
|----------|-------|----------|
| yes      | 7     | 70%      |
| no       | 0     | 0%       |
| not sure | 3     | 30%      |

Comments provided:

-   *In L2 we may come up with another solution.*
-   *I believe that we need to consider a side-tree option for representing stateless generic relationships ( mostly homologies)*

### "Do-you agree that the equivalence node must be a logical operator, and neither an entity pool node nor a process node?"

| Choice   | Votes | Fraction |
|----------|-------|----------|
| yes      | 8     | 80%      |
| no       | 1     | 10%      |
| not sure | 1     | 10%      |

Comments provided:

-   *But not a process node!*
-   *We don't know the mechanism so I can't see how we can answer this question.*

### " If you answered no to question 2, what do-you think this symbol should be?"

| Choice                   | Votes | Fraction |
|--------------------------|-------|----------|
| an entity pool node      | 0     | 0%       |
| a process node           | 0     | 0%       |
| not sure                 | 1     | 50%      |
| Something else (specify) | 1     | 50%      |

Comments provided:

-   *In many ways it is similar to a logical operator - but that operates on the input/output*

### "Do-you agree that the arcs linking the equivalence symbol to the relevant EPN should be equivalence arcs?"

| Choice   | Votes | Fraction |
|----------|-------|----------|
| yes      | 8     | 80%      |
| no       | 2     | 20%      |
| not sure | 0     | 0%       |

Comments provided:

-   *See above. Without knowing how the glyph works and what it means we cannot give a meaningful answer.*

### "If you answered no to question 4, what do-you think those arcs should be?"

| Choice                          | Votes | Fraction |
|---------------------------------|-------|----------|
| consumption and production arcs | 0     | 0%       |
| modulation arcs                 | 0     | 0%       |
| not sure                        | 1     | 50%      |
| Something else (specify)        | 1     | 50%      |

Comments provided:

-   *Something describing "could be" relationships*

### " When do-you think the equivalence gate should be introduced?"

| Choice                                  | Votes | Fraction |
|-----------------------------------------|-------|----------|
| In the forthcoming PD Level 1 Version 2 | 4     | 40%      |
| In a subsequent version of PD Level 1   | 3     | 30%      |
| In a future Level of the PD language    | 2     | 20%      |
| Other (specify)                         | 3     | 30%      |

Comments provided:

-   *Perhaps it could be a "recommendation" for version 2, while reserving the right to modify the semantics for V3? That way tools can start early to adapt to the new symbol, while there is some expectation that things might change?*
-   *Asap... But not sure what is realistic*
-   *We need to solve this problem, but it cannot be solved in L1 IMO. In L2 a diff solution may be found which doesn't need the equivalence gate.*

Should use the mt and ct Controlled Vocabularies to discriminate between otherwise identical EPNs?
--------------------------------------------------------------------------------------------------

In SBGN PD a number of controlled vocabularies have been defined, including the material type (mt) which defines the material of an EPN and the conceptual type (ct) which defines the conceptual role of the EPN. These are associated with the EPN inside a Unit of Information (UofI). In SBGN PD L1 V1.3 (the current version) the mt can be used to distinguish between otherwise identical macromolecule EPNs and likewise the ct discriminates between identical nucleic acid feature EPNs. However, the use of the UofI for this is problematic as the UofI was intended to provide annotation for an EPN.

To resolve this situation we wanted to clarify the role of the mt/ct controlled vocabularies in identifying the EPN. Would it be better to ignore the mt/ct assignment when identifying an EPN and rely on different label names instead? The different cases, with mt/ct discrimination and without, are illustrated in the figure below. [|400px](/Image:mtctepnvote.png)

------------------------------------------------------------------------

A vote was completed on 27 Sep 2011.

### "Do you think the mt and ct Controlled Vocabularies should be used to discriminate between otherwise identical EPNs?"

| Choice       | Votes | Fraction |
|--------------|-------|----------|
| yes (case 1) | 10    | 76.9%    |
| no (case 2)  | 3     | 23.1%    |

Change the Simple Chemical glyph to a stadium glyph in L1 Version 2.0
---------------------------------------------------------------------

There has been a proposal and much discussion on sbgn-discuss to change the Simple Chemical Glyph from the current Circle symbol to a Stadium symbol similar to that proposed for the State glyph. For more information and links to diagrams illustrating the issues please refer to the discussions at: <https://utils.its.caltech.edu/pipermail/sbgn-discuss/2011-September/000655.html>.

The diagram below presents the proposed new glyphs. The proposed replacement symbols for the Simple Chemical monomer and multimer glyphs are showed below as well as the cloned forms.

[|400px](/Image:SimpleChemicalStadiumProposal.png)

------------------------------------------------------------------------

### "Do you agree that the Stadium symbol (shown above) should be used to represent the Simple Chemical in SBGN PD Level 1 Version 2.0?"

| Choice | Votes | Fraction |
|--------|-------|----------|
| yes    | 11    | 68.8%    |
| no     | 5     | 31.3%    |

### "If you chose NO please state why"

| Choice                                                      | Votes | Fraction |
|-------------------------------------------------------------|-------|----------|
| I would like to keep the current symbol for Simple Chemical | 1     | 20%      |
| I would like to defer this change until Level 2 of SBGN PD  | 4     | 80%      |

This change will be incorporated into L1V2.0. We will allow the stadium to be drawn in such a way as it can also be a circle. This will preserve compatibility with previous version of SBGN PD.

On reversible arcs
------------------

One of the questions discussed at COMBINE 2010 (as in several past meetings) was the representations of reversible processes. In PD L1V1, the "production" node is overloaded, meaning only production for an irreversible reaction, but meaning production \*and\* consumption for a reversible reaction. Several solutions have been discussed to disentangle the glyphs. The current survey addresses two related issues: 1) the representation of the consumption. 2) the representation of reversible processes. Note that contrary to the questions discussed in previous surveys, there was no consensus reached in COMBINE2010. We therefore do not seek ratification of a solution by the community to be implemented immediately. Rather we would like the opinion of everyone for future developments.

For a detailed presentation of the different solutions, see [here](/sbgn/sbgn/wiki/SBGN-6/SBGN_languages_breakout_topics#Reversible_arc)

For the discussion about different solutions at HARMONY 2011, see [here](/sbgn/sbgn/wiki/SBGN-6.5/SBGN_languages_breakout_topics#Reversible_arc)

------------------------------------------------------------------------

A vote was opened on January 14th 2011 and closed on February 11th. 7 votes have been expressed.

At the question "Are-you satisfied with the current representation of irreversible reactions, where a consumption arc does not carry an arrowhead. Or would-you like to adopt a representation that expresses the direction of consumption?", voters answered:

| Choice                              | Votes | Fraction |
|-------------------------------------|-------|----------|
| keep the current situation          | 3     | 42.9%    |
| depict the direction of consumption | 4     | 57.1%    |

At the question "The solutions for the reversible processes that have been discussed at COMBINE 2010 would be: 0. Current situation. We do not change anythings. Advantage: it is already implemented. There is an overload at the level of the arc, but this is clear at the level of the process. 1. three types of arcs: consumption, production and bidirectional. The bidirectional would carry the same arrowheads. This solution would work for both the current and alternative consumption arc (see question 2). 2. three types of arcs: bidirectional would carry half arrows to remind that they are both consuming and producing. The representation would be a bit different according to the answer to question 2. 3. Two arcs from the entity pool node to the process node, one input and production on either side. The representation would be a bit different according to the answer to question 2. This solution was discussed and rejected at SBGN -2 in Yokohama. A scaling out would transform 3a) into 0) and 3b) into 1). The number of arcs may become esthetically unbearable. 4. Annotation inside the process node ("&gt;"). This solution does not change the arcs themselves, but makes clear that the process is or not reversible. Multiple choices are allowed." voters answered:

| Choice                                              | Votes | Fraction |
|-----------------------------------------------------|-------|----------|
| Keep current situation                              | 2     | 28.6%    |
| Three types of arcs. Full arrowheads for reversible | 4     | 57.1%    |
| Three types of arcs. Half arrowheads for reversible | 6     | 85.7%    |
| Doubled arcs for reversible                         | 0     | 0%       |
| Annotation in the process node                      | 0     | 0%       |

Further discussion on that topic was held at [HARMONY 2011](/sbgn/sbgn/wiki/SBGN-6.5/SBGN_languages_breakout_topics).

Multiplication of source and sink
---------------------------------

In SBGN PD L1 V1, the source and sink, although represented by the same symbol (empty set), are separate SBGN glyphs. They follow different syntactic rules. In addition, an "empty-set" symbol can only be connected to one arc, either consumption (for source) or production (for sink). Although this situation arose from the need to be semantically clear, it is contrary to many usage, results in a sometimes large duplication of glyphs, and does not fully correspond to what is intended (a boundary condition with size null).

The question that was debated at COMBINE 2010 was "Are all "empty-set" glyphs members of a clone?"

The conclusion of the (long and animated) discussion was Yes.

Therefore:

1.  The glyph Sink and Source are to be replaced by a single glyph called Empty Set. The symbol associated to those glyph does not change.
2.  A given "empty-set" symbol can be connected to one or more arcs.
3.  The sources and the sinks symbols are all members of the same clone. They all represent the same underlying object.
4.  The Empty Set glyph does not belong to a compartment.

------------------------------------------------------------------------

A vote was organized to validate the result of the discussion. The question was "Do-you agree with the conclusions of the discussion held at COMBINE 2010, and the corresponding change in SBGN Process Description Level 1 Version 2 ". The vote was opened on December 16th 2010 and closed on December 31st. 11 votes have been filed. The results are:

| Choice                  | Votes | Fraction |
|-------------------------|-------|----------|
| Yes                     | 8     | 72.7%    |
| No                      | 0     | 0%       |
| We need more discussion | 3     | 27.3%    |

Process Identity and Cloning
----------------------------

One of the questions discussed at COMBINE 2010 was the cloning of processes in PD. Because the identity of a process is currently only given by the arcs it connects to, the L1 V1.2 specification allows process to be cloned implicitly. Two processes linked to exactly the same EPNs are de facto graphical representation of the same underlying biological process. Alternative discussed:

1.  Keep the current situation
2.  Each process node is an independent node with its own identity
3.  Allow users to decide and use a clone marker

Option is not sustainable, because one cannot represent two reactions with different intrinsic rates. At the end, it was felt that option 2 was the only non-confusing solution for the time being.

------------------------------------------------------------------------

A vote was organized to validate the result of the discussion. The question was "When it comes to process node cloning, would-you prefer?". The vote was open on December 16th 2010 and closed on December 31st. 8 votes have been filed. The results are:

| Choice                                                              | Votes | Fraction |
|---------------------------------------------------------------------|-------|----------|
| To keep the current situation                                       | 0     | 0%       |
| That each process node is an independent node with its own identity | 6     | 75%      |
| To allow users to decide and use a clone marker                     | 2     | 25%      |
