
In the 2014 COMBINE, we started the discussion with the SBOLv (Synthetic Biology Ontology Language Visual) community about how to support their visual representations using SBGN diagrams. More extensive and detailed discussions were carried out at the 2015 COMBINE. The details of the discussion can be found in the [COMBINE 2015 report](https://docs.google.com/document/d/1C7PSlKg7NrN9lYVHT2Mmh2x07hXFxlzzR5joNInoI8w/edit?usp=sharing)

The followings are the consensus reached during the discussion:

1.  SBOL visual will use SBGN-AF to represent their diagrams.
2.  Stereotype will be used to draw SBOL specific glyphs to represent their synthetic DNA constructs.
3.  The SBGN-AF arcs will be used to represent the relationships.
4.  SBGN will introduce a glyph for the backbone used in SBOLv (see breakout session SBGN Spatial)

However, there are some concerns from the SBOLv community. Below are three proposals to address their concerns.

### Proposal 1. Logical operator AND can also be represented by a black dot

Rational: AND operator is used very frequently in SBOLv. It was argued that with all the AND glyphs the diagram may appear too crowded.

Proposal:

-   Black dot and AND are equivalent (black dot is a stereotype).
-   Remove the black dot in the association/dissociation arc in PD.

![AND_black_dot](https://raw.githubusercontent.com/sbgn/wiki-files/master/sbolv_support/AND_black_dot.png)

NLN: I think we do not need the black dot at all. Two influences merging would be synonymous with AND. If OR, the influences must be kept separate.

Note: when this proposal is coupled with the “influence on influence”, we enter in a world of pain. Take the example of the inhibition on a stimulation. The stimulation is due to A and B. If an influence terminates after the junction, the influence means “inhibition of the stimulation”. What if the inhibition terminates on the incoming arc to the junction?
  
### Proposal 2. Allow arc to target to another arc

SBOLv sometimes draws arcs regulating arcs, such as the inhibition arc from IPTG in the diagram below.

![arc_to_arc](https://raw.githubusercontent.com/sbgn/wiki-files/master/sbolv_support/SBOL_example_arc_to_arc.png)

Rational:

-   SBOLv argues that if the arc is targeted to the node it implies the inhibition of the production of protein.
-   The issue here is that the node in SBGN-AF is the activity, while SBOLv still treats it as an entity. It is a difficult concept to convince SBOLv.

NLN: But that is not true. In synthetic biology a stimulation terminating on a transcription start site ALWAYS means increase the ACTIVITY of the gene. Same with all the Synth Biol relationships. I believe many SBOLv developers just did not think enough about what we represent. We have 11 years of thinking, plus all the years of discussing SBML before. We just need to explain again and again.

-   In the stereotype proposal, the property of the nodes are defined.

NLN: What is the “stereotype proposal”?

-   In SBGN-ER, arcs are allowed to target to other arcs.

NLN: But ER arcs are different ... So are PD ones. And their nodes.

Proposal: Allow arcs to target to other arcs in AF (maybe PD later). This is currently supported in SBGN-ED

![arc_regulates_arc](https://raw.githubusercontent.com/sbgn/wiki-files/master/sbolv_support/Arc_regulates_arc.png)

NLN: Yes, but we need to be clear on the semantic, and for each “influence on influence”, we need to provide a traduction in “clean AF”. They can all be translated into logical combination. For instance “A stimulates B and C inhibits this stimulation”, is equivalent to “A AND NOT C stimulates B”

### Proposal 3. Allowing branching regulating arcs

When one activity regulates two separate activities, SBOLv allows one arc coming out of the regulator and then branches into two arcs to the targets, while SBGN uses two separate arcs. Two possible solutions.

#### Proposal 3.1

Allow branching arcs visually, but they can be two closely aligned arcs (overlapping?) -&gt; change the layout rule “overlap not allowed” to layout recommendation “should not overlap”.

#### Proposal 3.2

Allow branching of arcs.

![branching_arc](https://raw.githubusercontent.com/sbgn/wiki-files/master/sbolv_support/Branching_arcs.png)


