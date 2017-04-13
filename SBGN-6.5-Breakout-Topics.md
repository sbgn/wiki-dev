On reversible arcs
------------------

There has been a long ongoing discussion about the problem of representing reversible reactions. The problem of the current representation is that the production arc also covers an implicit consumption arc in the case of a reversible reaction. So, the “production” arc is overloaded, meaning only production for an irreversible reaction, but meaning production and consumption for a reversible reaction. Diverse approaches to the problem were envisioned and there was already a vote about possible solutions (for previous discussions see also [SBGN Editors meeting 04 Mar 2009](Editors_meeting_04_Mar_2009) and [SBGN 6 Breakout Topics](SBGN-6-Breakout-Topics)). However, the discussion at HARMONY showed that there is a need to reconsider the possible solutions. A major question is if a user is able by looking on local information (either entity pool node (EPN) or process node (PN)) if the reaction is reversible or not and in which direction the reaction works. Here is an overview of possible solutions which got at least some support in previous discussions. The table below will summarize properties of these solutions.

![arcs-discussion1.jpg]

![arcs-discussion2.png]

1 - current solution (nothing to change, there is an overload at the level of the arc); note that at the EPN it is not clear if a reaction is a production or a production + consumption in case of reversible reaction

2 -

3 - note that there is no rule at the moment which half side of the arrow should be shown

4 - similar to 2, but needs new glyph for PN

5 -

6 - similar to 3, but needs new glyph for PN

7 and 8 - similar to 4

9 - similar to 6 (could also use arrows as in 7)

10 - similar to 5, but needs new glyph for PN

| image | new glyph for arrowhead | new glyph for process | local information at EPN visible | local information at PN visible |
|-------|-------------------------|-----------------------|----------------------------------|---------------------------------|
| 1     | no                      | no                    | no                               | no                              |
| 2     | no                      | no                    | no                               | yes                             |
| 3     | yes                     | no                    | yes                              | yes                             |
| 4     | no                      | yes                   | no                               | yes                             |
| 5     | yes                     | no                    | yes                              | no                              |
| 6     | yes                     | yes                   | yes                              | yes                             |
| 7     | no                      | yes                   | no                               | yes                             |
| 8     | no                      | yes                   | no                               | yes                             |
| 9     | yes                     | yes                   | yes                              | yes                             |
| 10    | yes                     | yes                   | yes                              | yes                             |

No decision has been made.
