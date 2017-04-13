## AF nodes

Since the release of SBGN Activity Flow Level 1 specification, we have received some feedback, particularly about the biological activity glyph. Many of the concerns are reasonable (see details below).

In April 2009, we conducted a poll on the topic. The SBGN AF Level 1 specification was drafted based on the outcome of the poll. Unfortunately, due to a glitch in the SBGN discussion list, some of our members did not receive the message and failed to participate in the poll. As a result, we had very few people voted in the poll. Many of the feedback came after the poll was closed and even after the specification was released. We would like to re-open the discussion in order to ensure that the specification will be supported by the community. The [proposals](https://github.com/sbgn/wiki-files/raw/master/AF_node/AF_proposals.pdf) were presented at the COMBINE Workshop in last October.

One consensus we have reached is that AF is about influences among the activities, therefore the nodes in AF diagram should represent activities rather than entities. The problem arises when one wants to decorate the activity node to display the type of entity that the activity comes from.

The goal is to create biological activity nodes that are

-   unambiguous
-   ontologically accurate
-   consistent with representations in all three SBGN languages

### Current specification

-   [The activity node](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Current_AN.png) is represented by a rectangle.
-   [Entity decorationuses](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Current_Dec.png‎) unit of information to indicate the type of entity where the activity comes.
-   Examples: [EGFR](/Media:_Current_egfr.png "wikilink"); [PPAR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Current_PPAR.png); [TGF-beta](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Current_TGFbeta.png)
-   *Advantages*: It is ontologically correct to use a unique glyph to represent biological activity, which is an occurrent.
-   *Disadvantages*: The unit of information decoration can be too small to differentiate, e.g., a macromolecule vs a nucleic acid feature or a complex. It can be useless when the node itself is small in a very large map.

### Proposal 1

-   [The biological activity node](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_1_AN.png) is represented by a rectangle.
-   [The entity decoration](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_1_Dec.png) is drawn the same way as in PD. The AN is placed on the line of the entity glyph to indicate that the activity is derived from the entity.
-   All modulation arcs (positive influence, negative influence) must be connected to the activity nodes, but not the entity decoration.
-   Examples: [EGFR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_1_egfr.png); [PPAR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_1_PPAR.png); [TGF-beta](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_1_TGFbeta.png)
-   One problem with this proposal is that the activity node looks quite similar to the unit of information in the SBGN PD.

### Proposal 2

It is similar to proposal 1, except that the [biological activity nodes](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_AN.png) are placed inside rather than on the edge of the [entity decoration](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_Dec.png).

-   [The biological activity node](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_AN.png)
-   [The entity decoration](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_Dec.png)
-   Examples: [EGFR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_egfr.png); [PPAR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_PPAR.png); [TGF-beta](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_2_TGFbeta.png)

### Proposal 3

-   [The biological activity node](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_3_AN.png) is represented by a rectangle when the entity type of the activity is not illustrated. When the entity type needs to be illustrated, glyphs same to the EPN in PD are used to indicate the type of entity the activity is from. However, here, these nodes represent biological activity but not entity per se.
-   Examples: [EGFR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_3_egfr.png); [PPAR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_3_PPAR.png); [TGF-beta](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_3_TGFbeta.png)
-   The major criticism about this proposal is that it is ontologically ambiguous.

### Proposal 4

This is similar to proposal 2 except that the [entity decoration](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_Dec.png) is placed inside of [biological activity nodes](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_AN.png).

-   [The biological activity node](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_AN.png)
-   [The entity decoration](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_Dec.png)
-   Examples: [EGFR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_egfr.png); [PPAR](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_PPAR.png); [TGF-beta](https://raw.githubusercontent.com/sbgn/wiki-files/master/AF_node/Proposal_4_TGFbeta.png)

[Click here to take survey](http://www.surveymonkey.com/s/73LP2YG)