PD Stoichiometry labels
-----------------------

How do-we align stoichiometry labels on curved edges.

Answer: Decorations are nodes. Nodes must be above the arcs they are connected to. Stoichiometries are attached by ports on adjacent corner. This is a clarification of the specification, and does not require community vote.

{{\#icon:stoichiometryOnCurve.png‎ | Decorated nodes |300 || corner iradius11}}

Logical operators linking EN to statements in ER
------------------------------------------------

Case of the variable values assignments:

When there are several alternative values, what is the semantic of the combination? Answer: There is an implicit xor at the node joining multiple variable values to the assignment. This implicit xor is not a true logical operator, and the edges linking the connexion point to variable values are not logic arcs but variable assignments. We keep the specification as it is, and do not add explicit operators.

The case of operators on interactions was not discussed.

Outcome on influences
---------------------

As of ER Level 1 Version 1.1, we can only put outcomes on statements (interaction or variable assignment), but not influences (stimulation, inhibition etc.). This means we can use the actualization of a statement in an interaction or an influence, but not the actualization of an influence itself.

In COMBINE 2010, we discussed why we would need such outcomes, and what would be their meaning. The figure below shows why we need, and what it would look like to put outcomes on influences.

{{\#icon:outcome-influences.png‎ | Decorated nodes | || corner iradius11}}

Outcome (1) is the one we can use at the moment. It means:

-   if T is assigned to VAR, then X inhibits the interaction between A and B

(or can it also means “if T is assigned to VAR, then the interaction between A and B is inhibited”? See next section.)

Outcome (2) cannot be used at the moment: It would mean:

-   If Y stimulate the assignment of T to VAR, the interaction between A and B is inhibited. For instance, while busy assigning T to VAR, Y would disrupt the A/B complex (think enzymatic or channel activity from Y affecting its conformation).

Crucially, (1) and (2) are different because the stimulation by W does not inhibit the interaction between A and B.

Differentiating continuant and occurrent entities
-------------------------------------------------

Contrarily to what we initially believed, an Entity in ER is a not a continuant and relationships are not occurrents. Entity and outcomes are existing things (existants?), while relationships (influences and statements) are potentialities (dispositions?). Until recently Entities have always been used to represent continuants, but Bernard de Bono used them also for occurrents (e.g. “glycolysis”), see [his entry in the 2010 competition](http://sbgn.org/images/d/dc/SBGN_ER_retinopathy.png).

Recently some of us became aware that contrarily to what we initially believed, an Entity in ER is a not a continuant and relationships are not occurrents. Entity and outcomes are things, both continuants and occurrents that exist (existants?) \[note that this is actually the definition of “entity”\]. Relationships on the contrary (influences and statements) are potentialities (dispositions?). Until recently Entities have mostly been used to represent continuants, but Bernard de Bono used them also for occurrents (e.g. “glycolysis”), see [his entry in the 2010 competition](http://sbgn.org/images/d/dc/SBGN_ER_retinopathy.png).

It is proposed by Augustin Luna and Nicolas Le Novère to have two types of outcomes, disc for “truthified” continuants (only on statements), and square for “truthified” occurrents (possibly on influences or statements see the discussion above). For instance, a disc on an interaction would represent the complex, while a square would represent the interaction itself. This interaction could have an effect (the outcome could initiate an influence) that is not mediated by the physical complex.

Similarly, it is proposed to use two different glyphs for entities representing continuants (round corner rectangle) and occurrents (rectangle) that remind the continuants and occurrents of PD. This would bring a consistency accross all SBGN languages.

Below is an example of map with continuant entities (insulin, glucose) and occurrent entity (glucose transport), as well as continuant outcome (Insulin receptor complex) and occurrent outcome (The interaction between IRS1 and insulin receptor complex).

![OccurrentsContinuants.png]

Reversible arc
--------------

In PD L1V1, the “production” node is overloaded, meaning only production for an irreversible reaction, but meaning production **and** consumption for a reversible reaction. Several solutions have been discussed to disentangle the glyphs.

{{\#icon:ReversibleProcess.png | Decorated nodes |500 || corner iradius11}}

The upper right drawings represents irreversible reactions in the current spec a) and a possible alternative b). In the latter situation, the consumption would be different from the production since the arrowhead would end on the PN and not the EPN. This would correspond to the representation used in Petri-Net. Another advantage would be the visual difference between consumption and logic/equivalence arcs.

The solutions for the reversible reactions would be:

0. Current situation. We do not change anythings. Advantage: it is already implemented. There is an overload at the level of the arc, but this is clear at the level of the process.

1. three types of arcs: consumption, production and bidirectional. The bidirectional would carry the same arrowheads. This solution would work for both the current and alternative consumption.

2. three types of arcs: bidirectional would carry half arrows to remind that they are both consuming and producing.

3. Two arcs to the same process node, one input and production on either side. Representations are provided corresponding to the current irreversible situation and the alternative. This solution was discussed and rejected at SBGN-2 in Yokohama. A scaling out would transform 3a) into 0) and 3b) into 1). The number of arc may become esthetically unbearable.

4. Annotation inside the process node ("&gt;"). This solution does not change the arcs themselves, but makes clear that the process is or not reversible.

Multiplication of source and sink
---------------------------------

In SBGN PD L1 V1, source and sink are separate glyphs. In addition, an “empty-set” can only be connected to one arc, either consumption or production. Although this situation arose from the need to be semantically clear, it is contrary to many usage, results in a sometimes large duplication of glyphs, and does not fully correspond to what is intended (a boundary condition with size null).

The question that was debated was "Are all “empty-set” glyphs members of a clone?"

The conclusion of the (long and animated) discussion was **Yes**.

Therefore:

1.  source = sink;
2.  A given “empty-set” can be connected to any number of arcs.
3.  Since all empty-set glyphs of a map represent the same “thing”, this thing cannot belong to any compartment. It is therefore not an EPN but a different type of continuant.

Process duplication
-------------------

The main question is the cloning of processes in PD. Because the identity of a process is currently only given by the arcs it connects to, the L1 V1.2 specification allows process to be cloned implicitly. Two processes linked to exactly the same EPNs are *de facto* graphical representation of the same underlying biological process. Alternative discussed:

1.  Keep the current situation
2.  Each process node is an independent node with its own identity
3.  Allow users to decide and use a clone marker

1) is not sustainable, because one cannot represent two reactions with different intrinsic rates. At the end, it was felt that option 2 was the only non-confusing solution for the time being.

can Phenotype be cloned?
------------------------

In the L1 V1.2 specification, the situation of the phenotype is confusing, and the specification is inconsistent. The clone markers are meant for EPNs only, but have been used on phenotypes. As described above, in addition phenotype being a PN, it could be implicitly cloned in the current situation. Can phenotype be cloned?

Pros: a diagram may become cluttered if they cannot be cloned.

Cons: The declutter mentioned above only happens if we can modulate different members of the clone by differnent EPNs. That would violate the identity of a process defined by its input. If we select 2 above, phenotype is a process, and therfore cannot be cloned. If we have two phenotype nodes with the same label but different modulations, readers may be induced in thinking they are different.

Proposal: phenotype can not be cloned.

Others
------

-   Generics and Negative State Variables in PD

<!-- -->

-   Binding State Variables in PD

<!-- -->

-   Complex subunits are not EPNs

<!-- -->

-   Submap functions

<!-- -->

-   Function “ontology”

<!-- -->

-   Deprecate simple chemical

<!-- -->

-   Enumeration of rules

<!-- -->

-   Balanced equations: tracker item ([http://sourceforge.net/tracker/?func=detail&aid=3051033&group_id=178553&atid=1082245](http://sourceforge.net/tracker/?func=detail&aid=3051033&group_id=178553&atid=1082245))

<!-- -->

-   Clone markers inside complexes: tracker item [http://sourceforge.net/tracker/?func=detail&aid=3069108&group_id=178553&atid=1082245](http://sourceforge.net/tracker/?func=detail&aid=3069108&group_id=178553&atid=1082245)

<!-- -->

-   Labels on complexes: tracker item [http://sourceforge.net/tracker/?func=detail&aid=2849275&group_id=178553&atid=1082245](http://sourceforge.net/tracker/?func=detail&aid=2849275&group_id=178553&atid=1082245)

<!-- -->

-   Activity node decoration in AF [http://sbgn.org/AF_development](http://sbgn.org/AF_development)

Submit to vote again.

-   Compartment in ER

Solved. No compartment in ER. But we will propose “group” to visually organise the maps.

-   Spatial relationships
