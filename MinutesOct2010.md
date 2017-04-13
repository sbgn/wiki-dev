Meeting Notes, October 7, 2010, During COMBINE in Edinburgh

Present: Emek Demir, Stuart Moodie, Anatoly , Gary Bader, Martijn van Iersel, Alice Vileger, Tobias Czauderna, Falk Schreiber, Huaiyu Mi, Augustin Luna

Curved Arcs
===========

-   Several proposals have been discussed on the mailing list, and the

feeling is that we're getting close to a final resolution.

-   With regards to specifying segment type (straight, quadratic or

cubic), alice proposes to leave it out altogether, because this information can be derived from the number of control points (0, 1 or 2)

-   "controlPoint" will be renamed to "point" for brevity.

Clone marker labels / State val@var
===================================

-   Currently, clone marker labels are implemented with a second label

element, whereas state labels are done using a specialized "state" tag with attributes variable and value. This is inconsistent because the former is "graphical", the latter is "semantical".

-   Resolution: we go for semantical. The "label" for clone marker labels

is replaced with a "clone" element, with an optional text attribute

-   The "clone" attribute on glyphs is then redundant and will be removed.
-   The "role" attribute on labels will be removed.
-   The current implementation for state is left untouched.

Label bounds proposal
=====================

-   The latest proposal made by Frank was accepted by everybody, the

corresponding bug will be closed.

Stoichiometry
=============

-   Currently there is no way to create stoichiometry labels.
-   It was decided to allow subglyphs on arcs for stoichiometry (just like

we allow subglyphs on glyphs for "state" and "unit of information")

-   Position of stoichiometry markers is specified using absolute

coordinates (and not e.g. relative positions on the arc)

-   There was a whole discussion on what a stoichiometry marker on a

curved line should look like, but a decision on this will have to be taken by the SBGN editors.

Missing
=======

-   We did not have time to discuss the issue of Compartments & Complex

containment unfortunately.

-   We also did not have time to talk about a release plan

Next Meeting
============

Next meeting will be an online meeting (EU-USA time) in November.