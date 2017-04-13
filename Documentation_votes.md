Creating groups in SBGN maps
----------------------------

In SBGN 2.5, our first "hackathon" in Heidelberg, we discussed the possibility of "group", which would be structures putting together sets of nodes, without changing the semantics of the map. At that time, it was suggested for Process Descriptions, in order to implement "pathways". At the first SBGN competition, Bernard de Bono submitted an impressive [ER map](http://sbgn.org/images/d/dc/SBGN_ER_retinopathy.png) that also used such a feature. The discussion was continued on sbgn-discuss, see the very interesting and complete thread at [1](https://utils.its.caltech.edu/pipermail/sbgn-discuss/2010-November/000328.html). The discussion was resumed at HARMONY 2011, where it was felt to be mature enough to give rise to a vote.

The idea is to have a mechanism to "tag" an SBGN glyph as belonging to one or several groups. Those groups would correspond for instance to "pathways" or "metabolic network", glyphs associated with a disease or biological function. A group is not a compartment, and it is not a submap. It does not affect the syntax of the map, but is merely a multi-glyph annotation.

Groups would be a way for instance to organise nodes together in a certain subpart of the plan, or highligtht them in some way. Software would have to conserve groups, and it could thus be a way to lightly constrain the layout, without going all the way to specify position and size of the nodes. A group would not be "linked" to any node using edges, but would "contain" EPN/PN in PD, EN in ER, AN in AF (i.e. in PD and AF, a group could span several compartment). Groups could be named and could be annotated with "floating" annotations, similarly to the default compartment.

------------------------------------------------------------------------

This vote is now closed. 11 votes have been filed. The results are:

### Question 1. Are-you in favour of introducing a "group" feature in SBGN languages?

| Choice        | Votes | Fraction |
|---------------|-------|----------|
| Yes           | 10    | 90.9%    |
| No            | 1     | 9.1%     |
| I do not know | 0     | 0%       |
||

Decision: The creation of groups will be introduced in the three SBGN languages.

### Question 2: Should-we specify the way a group is displayed?

| Choice        | Votes | Fraction |
|---------------|-------|----------|
| Yes           | 7     | 63.6%    |
| No            | 4     | 36.4%    |
| I do not know | 0     | 0%       |
||

Comments:

-   *In fact, to me, a "submap" in a PD diagram is a grouping as well. If we let submaps to be specified (whatever the way we choose - Q3 of this survey) when they are not collapsed, then submaps could be handled just like the way other types of groups are (so the two concepts could be merged). Compartments, on the other hand, are also groups but they are so special and significant that we prefer to classify and specify them distinctly.*
-   *Maybe with several options. But people and tools need to know what to look for.*
-   *SBGN is all about the graphical representation. Every feature should therefore also represent graphically, and it should be done in a standardized way.*
-   *The representation should be different enough to prevent misinterpretation of the diagram.*

Decision: the way of representing groups will be specified.

### Question 3: If we were to advise a way to represent groups, what should it be (multiple answers possible)?

| Choice             | Votes | Fraction |
|--------------------|-------|----------|
| A spatial grouping | 4     | 36.4%    |
| A contour          | 7     | 63.6%    |
| A background       | 8     | 72.7%    |
| Highlighting glyps | 4     | 36.4%    |
| Unsure             | 2     | 18.2%    |
| None of the above  | 0     | 0%       |
||

Comments:

-   *This needs further discussion but a convex hull that tightly bounds all group members with a transparent background and possibly a contour could be used. Notice however that we should definitely allow overlapping of groups as one might like to show grouping w.r.t. biological function as well as grouping w.r.t. pathway abstractions.*
-   *Representing groups through layout (spatial grouping, and to some extent, contour and background) is likely to become very difficult with large pathways (there's other layout constraints to take into account: compartments, + limiting edge crossing, etc.). Individual glyph highlights (color?) seem preferable (as graphically, the feature is fully "perpendicular" to the other containment idea expressed spatially by compartments)*
-   *layout should not carry any meaning (therefore no spatial grouping), colour should not carry meaning (no background or highlighting)*

Decision: The responses to this question are more nuanced. However, because of the result of Q2, we must take a decision. Since contour and background came clearly first, the editors decided to go for a background for the time being. In the future, explorations will be done to see if we can allow contours as well (Still allowing the backgrounds).

Links to annotation
-------------------

An annotation glyph has been introduced in SBGN ER L1 and SBGN AF L1. It is planned to add it to future versions of SBGN PD. This annotation glyph has to be linked to SBGN objects so as to identify precisely what it refers to.

Entity Relationships Level 1 Version 1 says that the edge linking an annotation to the object it annotates must be significantly different from other edges. The precise type of edge is not specified. Part of the community would like to see that clarified. Four other possibilities have been proposed. One is to define another edge, identified by its connection to an annotation node. Three are based on different symbols: continuous lines, dashed lines, callouts. They are described in [this file.](/media:AnnotationLinks.pdf "wikilink"). You should look at all the slides because the issues are different with PD, AF and ER.

The example of PD used in the Nature Biotechnology paper has been annotated using the three schemes:

-   [using different thickness](/media:Muscle-annotation-thick-color.png "wikilink")
-   [using dashed lines](/media:Muscle-annotation-dashed-color.png "wikilink")
-   [using callouts](/media:Muscle-annotation-callout-color.png "wikilink")

Pitfalls have been pointed out for the four schemes:

-   Using a regular SBGN edge is very misleading and would actually need a complex definition since this edge could connect to all kinds of nodes, but also to other edges.
-   Using thicker continuous lines may also be confusing with other edges. Furthermore, an important recommendation of SBGN is that the thickness of the line should not bear meaning.
-   Using dashed lines would infringe the rule of SBGN to avoid discontinued lines because of the lack of scalability and the risk of having misleading connections within the line.
-   Using callouts may be difficult to implement, in particular for software that allow dynamic reorganization of the graphs.

------------------------------------------------------------------------

This vote is now closed. 20 votes have been filed. The results are:

| Choice                                               | Votes | Fraction |
|------------------------------------------------------|-------|----------|
| A new SBGN edge with different semantics             | 0     | 0%       |
| A thicker continuous line                            | 1     | 5%       |
| A dashed line                                        | 7     | 35%      |
| A callout (Google maps)                              | 13    | 65%      |
| Anything significantly different from the SBGN edges | 6     | 30%      |
| Other                                                | 4     | 20%      |

