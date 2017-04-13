This page serves as a portal to the discussions towards the development of SBGN Process Description Level 2.

-   [Process viewed as Petri-Nets](#process-viewed-as-petri-nets)
-   [Stylesheets](#stylesheets)
-   [Using logical gates](#using-logical-gates)
-   [Mixed maps](#mixed-maps)
-   [Simplification and clarity](#simplification-and-clarity)
-   [Moving compartments](#moving-compartments)
-   [Multi-compartment entities](#multi-compartment-entities)

## Process viewed as Petri-Nets
----------------------------

1) Overload of production and reversible arcs is a long standing issue in PD Level 1. This has led to numerous discussions and a vote. [various solutions](/sbgn/sbgn/wiki/SBGN-6/SBGN_languages_breakout_topics#Reversible_arc) were explored, then the [spectrum of possibilities](/sbgn/sbgn/wiki/SBGN-6.5/SBGN_languages_breakout_topics#Reversible_arc) expanded further. We had a [PD_development\#On_reversible_arcs](/sbgn/sbgn/wiki/PD_development#On_reversible_arcs) that only excluded the use of doubled arcs, and annotation of the node.

2) SBGN PD started from the CellDesigner notation, that only contained one type of nodes. The process node was added on top of the transition arc, to avoid misunderstanding regarding left and right in case of reversible arcs and to provide anchors for the modulatory arcs. It resulted in a bipartite graph.

Several groups called for a Petri-Net type of representation, which is an accepted standard way of representing bipartite graphs describing processes. This correspond to [solutions 2 and 6 proposed in HARMONY 2011](/sbgn/sbgn/wiki/SBGN-6.5/SBGN_languages_breakout_topics#Reversible_arc)

-   That solves the problem of production/reversible overload

<!-- -->

-   That solves the problem of knowing which arc it is when looking at the EPN or the PN

<!-- -->

-   That solves the overload between consumption and equivalence arc

## Using logical gates
-------------------

In the initial phase of SBGN development, the logical combination of EPN influences on processes was represented using logical gates. There were a series of discussions based on the exact semantic of those combinations, that led to abandon the standard logical gates and use circles instead. Since the shape was the same for all, that led to another complicated discussion on which symbols to use, that resulted in using words rather than symbols.

The use of circles does not work well:

-   In order to quickly see was comes in and out, people are required to put all the inputs terminating on a point connector located 180 deg from the output connector. Most people do not do that, but rather distribute the inputs on the circles. This looks nicer, and correspond with what CellDesigner was doing. But we loose the ability to know instantly what gets in and what gets out. When people draw the connections correctly, the circle is sometimes drawn away from the connector. This is ugly and gets back the problem of tracing. Note that with the "not" operator, there is still a problem of orientation.

<!-- -->

-   The logical operators have the same shape than simple molecules. This will be solved in many cases by the stadium in L1V2, but a specific case of the stadium is still a circle.

<!-- -->

-   The use of English words in operators is very much against the spirit of a graphical language. We should use symbols. But of course there is the problem of choosing the symbol set etc.

There is an existing standard for graphically representing logical operators. Using them would solve the problem of directionality, of labelling, would increase instant recognition, and would make the maps nicer.

## Stylesheets
-----------

1) The representation of an entity is often contextual. For instance, EGFR can be iewed as a receptor (for EGF) or an enzyme (tyrosine kinase). RXR can be viewed as a receptor (for retinoic acid) or as a transcription factor.

2) Some symbols have been widely used in molecular and cellular biology for decades, and are expected to be used by standard graphical notations. Examples are the broken arrow for gene/transcription initiation site, the arrows crossing an oval for transporters etc. However, they are not used by SBGN, and sometimes conflict with them.

3) Some communities standardized their own symbols, and will not adopt SBGN until it is compatible. A prominent example is Synthetic Biology.

One solution proposed as early as 2007 was the use of stylesheets. The stylesheet do not redefine the SBGN symbols but "enrich them". The same SBGN map can be rendered differently according to the stylesheet used. A longer discussion with examples was held on sbgn-discuss: <https://lists.caltech.edu/pipermail/sbgn-discuss/2010-November/000346.html>

The issue was discussed further in HARMONY 2012.

## Mixed maps
----------

Many maps found in the scientific literature or in textbooks are mixed maps. For instance a signalling pathway would be described largely using AF, but the phosphorylation events would be described using PD. Often events involving simple chemicals are described using PD while events involving proteins are described using AF.

Most signalling maps would completely explode if using proper PD. However, the combinatorial complexity is often coming from a limited amount of entities.

It would therefore be desirable to be able to link different maps using different languages, within a larger ensemble. Different solutions have been discussed at [HARMONY 2011](/sbgn/sbgn/wiki/SBGN-7.5).

## Simplification and clarity
--------------------------

The initial design of SBGN PD started from the symbols, and the syntax evolved later on. The structure of the language became more and more clear and simple, and some of the symbols are either no longer necessary or completely getting in the way. Examples are association/dissociation (are processes, could be represented as process (square, with open / filled circle inside if necessary), catalysis etc. In addition, the set of three languages is now really clear: AF is all about square angle occurrents. ER is all about round angle continuants. And PD would be a perfect bi-partite graph is the EPN did not have so many shapes, some confusing (a simple chemical may look like a logical get), some hard to draw (nucleic acid feature).

A proposal was made to simplify the language by deprecating a few symbols and using stylesheets instead.

## Moving compartments
-------------------

While SBGN languages are good to represent biochemical networks, they are currently difficult to use to depict cell biology. One of the biggest hurdles is to represent moving or transforming compartments. If '"a" compartment is represented twice on the graph, the resulting map contains two compartments, which is fine (similar to translocation of EPNs). However, all the EPNs contained by the compartment have to be duplicated and transport processes created for all of them. Although this has been discussed a few times, no progress has been made. Should-we use submaps? unit of info on compartments? New rules?

## Multi-compartment entities
--------------------------

The existence of multi-compartment entities is arguably the most debated issue of SBGN PD, and the most enquired for evolution of the language. At the moment an EPN belongs to a compartment. Therefore a transmembrane receptor must belong to one compartment. One solution is that it belongs to the membrane. That forces the existence of the membrane as a compartment. The only elegant solution is to put the membrane compartment "underneath" the cytosol, so as to have a nice one-membrane separation (see [this example](https://sbgn.github.io/sbgn/docs/faq/pd#how-can-i-represent-multi-compartment-reactions-without-multiplying-the-ugly-compartment-boundaries) of the PD FAQ), and to draw all the compartments first and then the EPNs (so that transmembrane proteins are not partially hidden by the compartment above.
