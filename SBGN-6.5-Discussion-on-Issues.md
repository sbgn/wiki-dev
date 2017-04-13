PD Issues Discussed at HARMONY 2011
===================================

Reversible Arcs
---------------

Falk Schreiber has outlined the discussion [here](/Events/SBGN-6.5/SBGN_languages_breakout_topics "wikilink").

State Glyph
-----------

The state glyph originally had an external number designation outside the state variable. This was designed for compatability with some existing implementations which used a sphere with the value held in the circle and the variable name outside it. This has been largely superceded by the 'value@variable' notation and the adoption of th stadium glyph. The question is should still permit this? This has a number of limitations including ambiguity in some layouts about which variable name belongs to which state. The suggestion is to have a vote on this with the recommendation that this is no longer permitted.

Empty Set
---------

Source and Sink have been deprecated in a vote [here](/PD_Development "wikilink"). However, the vote was unclear about that the nature of the Empty Set was. After much discussion the conclusion was that this was a special type of EPN that could act as both a sink and source of unspecified EPNs, it did not have a quantity nor did it belong to any compartment. Likewise it could be replicated on a map and could be connects to any number of arcs.

Subunits of a complex
---------------------

It was agreed that Subunits are decorators of a complex not EPNs. The main issues of discussion was whether Subunits must be unique within a complex. It was concluded that they did not need to be unique. In cases where subunits of the same name have different states then the subunit composition of the complex is what defines its identity. For example a complex with subunits drawn A(P)A() is identical to one with subunits drawn A()A(P) and should therefore be cloned.

Cardinality of an EPN
---------------------

In the current spec cardinality is defined as a unit of information, but it is also an attribute of an EPN being critical for the definition of its identity as EPNs with different cardinalities are regarded as different. Since the Unit of Information is intended for annotation the proposal is that a new glyph be chosen to show the unit of information.

Material Type and Conceptual Type
---------------------------------

In a similar way to cardinality these controlled vocabularies are attributes defining part of the identity of the macromolecule and nucleic acid feature respectively. Since this is specified by a unit of information there are not restriction on having more than one mt or ct type, and this also breaks the designed usage of UofI, which is annotation. Consequently there was much discussion about whether to follow cardinality and propose a new glyph (or the same glyph as cardinality) to specify that this is an attribute of the respective EPNs or whether to remove this requirement and make such features purely annotation.

It is proposed that we vote to ask the question should mt and ct designations be part of the identity of a MM and NAF EPN (keep the current situation). If the answer is yes then we will vote on the decorator to adopt.