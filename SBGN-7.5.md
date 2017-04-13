SBGN-7.5 was held from May 21st to 25rd, 2012, in Maastricht, Netherlands, at the School of management.

Tuesday 22 afternoon: Mixed maps
--------------------------------

Rational: In the literature and some pathway databases, one find hybrid maps, in particular with parts in PD and parts in AF. We have currently not possibility to implement that in SBGN.

Everyone agree that full hybrid maps are not desirable. They would be impossible to validate.

Several solutions are envisioned:

Using Submaps: e.g. Within a map in AF, an activity X is linked to a submap. This submap contains a map in PD, in which X is a macromolecule. This is fine but not sufficient since we use equivalenceArc. This should be different from a PD submap in a PD map, both containing a macromolecule Y. Furthermore, the relation between X macromolecule and X activity is not specified.

Using groups: an activity A stimulate X that is consumed by a process producing Y. Y inhibits B. Same issues than above. But worse since the glyphs in a group belong to the same map. X could be duplicated and the activity and macromolecule linked by an equivalence node (proposed by Alexander Mazein).

It is felt that it is maybe too early to settle on a given solution. People are encouraged to think about the issue and to test possible solutions.