LibSBGN meeting during HARMONY, April 20 2011
=============================================

0) Introductions
----------------

Participants

Martijn, Stuart, Ugur, Huaiyu, Augustin, Gael, Martina, Alice (via Skype), Katja, Tobias

1) SBGN-ML
----------

`   - ER`
`   - AF`
`   - PD: z ordering/containment`

- road map: release milestone 2 covering PD, ER and AF at COMBINE 2011

AF

- development plan for AF: derive test cases from the specification ACTION: drawing test cases during HARMONY 2011 (Thursday or Friday)

ER

- update on the status for ER

`   proposals for ER were presented at HARMONY 2011`
`   all proposal were accepted/discussed before HARMONY 2011`

- discussion about the name for the grouping element for ternary interactions

`   proposed names: hyperarc, superglyph, hyperglyph, arcgroup`
`   decision: arcgroup`
`   proposal: outcomes should not be a child glyph of the circle element`

but a top glyph in the group

PD: z ordering/containment

- clarification of the PD specification regarding compartments

`   There is always an implicit compartment (not visible) containing all`

elements except process nodes and the empty set.

`   If one compartment is drawn all elements have to be within a visible`

compartment.

- Compartment reference will be added as attribute to the glyph element - Canvas size (bounding box) will be added as attribute to the map element - We should have a vote to determine if the implicit compartment should be added as an actual element to the map or if it can be handled implicitly by the library. - Z order will be added as attribute to all elements (integer value 32 bit).

`   proposal: the higher number is on top, numbers should be unique`

2) LibSBGN
----------

Validation

- Schematron might not be able to cover all validation rules which are needed (e.g. overlap). - advantage of schematron: language independent - 3 layers of validation needed?

`   schema validation (implicitly)`
`   schematron validation where possible`
`   language dependent validation for all other rules`

- Some rules will be implemented in schematron as a test.

`   SBGN syntactic rules`
`   SBGN-ML syntactic rules`
`   layout rules (overlap)`
`   semantic rules (clone marker validation, reversible and irreversible`

reaction at the same time) - validation rule numbering (this is a proposal to SBGN editors)

`   We will use similar system as SBML.`
`   Each rule has 5-digit id. First three digits are category, then 2`

sequential digits. - categories numbering

`   Categories 100-899 are for general SBGN use. SBGN-ML syntactic rules`

start from category 900.

`   Categories will be adapted from SBML (errors, recommendations, ...).`
`   `
`   `

3) Paper
--------

- suggestion by Stuart, Katja, and Huaiyu to wait for a bigger paper

4) Round table
--------------

- Stuart: We should vote to increase the priority for defining color for graphics. Stuart wants to get to this before validation - Ugur: There should be interaction between people from Paxtools and LibSBGN regarding conversion. - Tobias: We need clarification about arc coordinates (Where does an arc end?) \[Request by Frank\]

`           Proposal: The coordinates of an arc specify the end`

points of the drawing and not the points where the arc is connected to glyphs (important for catalysis and inhibition).

Action items
============

-   ACTION: Tobias, Martijn, Huaiyu: create AF test-cases covering all aspects of AF. (everybody is welcome to join in)
-   ACTION: Martijn: implement "arcgroup" in ER examples, grouping interactions and making outcomes a child of the arcgroup wherever applicable.
-   ACTION: Tobias: hold a vote on compartmentRef: should it be required or not?
-   ACTION: Tobias: hold a vote on implicit compartments: should there be an explicit implicit compartment?
-   ACTION: Tobias: hold a vote on the zorder field, should it be optional? should they be unique?
-   ACTION: Martijn, Augustin: experiment with schematron rules to get a better idea of suitability (everybody is welcome to join in)
-   ACTION: Alice: Propose 5-digit rule numbering system to SBGN editors (also: unify and renumber existing lists of rules).
-   ACTION: Tobias: hold vote on increasing priority of color attributes
-   ACTION: Tobias: write detailed proposal on the end-points of arcs (make sure this contains really detailed drawings because we tend to speak past each other on this topic).
-   ACTION: Martijn will organize an online meeting in May (US-EU time)
