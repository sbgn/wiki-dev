AF phenotype glyph survey
-------------------------

In SBGN Activity Flow, *phenotype* and *perturbation* are both activity nodes, and are represented by glyphs identical to those of *perturbing agent* and *phenotype* in PD, respectively. The syntax of both glyphs is identical to that in PD also, i.e., *perturbation* can only be the source of an influence arc, and *phenotype* can only be the target.

There are two issues related to this.

1. In PD, *perturbing agent* is an EPN, while *phenotype* is a process node, while in AF, both *perturbation* and *phenotype* are activity nodes (processes). Using the same glyph for two semantically different concept is confusing.

2. In AF, sometime a *phenotype* can be a source of the different arc, for example, Na channel activity -&gt; membrane depolarization -&gt; K channel activity -&gt; membrane repolarization. The current AF syntax makes it difficult to represent such pathways.

The topic was discussed at the HARMONY in April, and a few solutions have been suggested, which are summarized below.

**A. Solution for the glyph of perturbation**

Remove *perturbation* as an activity node. Instead, use it as a decoration of an activity node like *macromolecule* or *nucleic acid feature*.

Examples: the [glyph](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Perturbation.png), [PPAR pathway](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/PPAR-perturbation.png).

**B. Solutions of *phenotype***

Below is a summary of the suggestions gathered at the HARMONY

1. Remove *phenotype* glyph, and use *activity node* to represent it.
   * [Example](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Phenotype_proposal1.png)
   * Problem: It loses the specificity to represent something that is observed.
2. Remove *phenotype* glyph, use *activity node* with a specific decoration that reflects the fact that it can be observed.
   * [Example](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Phenotype_proposal2.png)
   * Problem: a new glyph has to be designed, and its meaning is similar to that of *phenotype*.
3. Remove *phenotype* glyph, use *activity node* with a *phenotype* glyph as a decoration.
   * [Example](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Phenotype_proposal3.png)
   * Problem: *phenotype* glyph is a process node in PD, and semantically it should not be used as a decoration.
4. Keep *phenotype* glyph, and it can only be the output of an influence arc, but design a new influence arc such as “causation”.
   * [Example](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Phenotype_proposal4.png)
   * Problem: need to create a new arc glyph and its meaning could potentially be the same as existing ones.
5. Allow *phenotype* glyph to be both input and output of influence arcs.
   * [Example](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_phenotype/Phenotype_proposal5.png)
   * Problem: It is not consistent with that of PD. In PD, a *phenotype* can only be the boundary of the pathway, i.e., the target of an arc.
6. Keep the current spec, i.e., *phenotype* glyph can only be the output of an arc.


**Results of the voting**

1 vote - proposal 1

1 vote - proposal 2

0 vote - proposal 3

0 vote - proposal 4

3 votes - proposal 5

2 votes - proposal 6

No decision was made. Need further discussion.