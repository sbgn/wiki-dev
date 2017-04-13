LibSBGN Meeting notes, 14 December 2010

Present: Frank Bergmann Alice Vileger Sarah Boyd Tobias Czauderna Martijn van Iersel

SBGN-ML
=======

Arcs
----

Alice checked in example of mixed arcs, and posted summary on the mailinglist. There are no further action items on this issue.

Containment
-----------

Frank updated the examples, and Martijn entered a ticket for compartment containment. There are no further action items on this issue.

"Map" element
-------------

-   "Map" will allow grouping of multiple maps in a file.
-   "Map" could also be used to model submaps in the future.
-   Martijn did not implement this yet, because there are still unresolved issues. There could be a namespace problem if we want to support different language maps in the same file.
-   After some discussion, it was decided that it would be best to go ahead anyway.
-   Martijn will finalize implementation (DONE at this time of writing).

Documentation
=============

Various documentation actions were completed. The following action items still need work and are therefore repeated here:

ACTION: Tobias will link to an example of a large network at release time. ACTION: Martijn will write a LibSBGN tutorial using ant ACTION: Tobias will adapt the same tutorial to eclipse ACTION: Tobias will post slides with his benchmark results on the wiki ACTION: Alice will continue to document each element of the schema.

-   Martijn created an ant target for javadoc generation.
-   Augustin has turned XML comments into XSD annotations
-   Alice encountered a few comments in the schema that appear out of date, she is reviewing those before finishing the documentation.

Tool support
============

PathVisio and the SBML Layout rendering extension are up-to-date. Tobias is still working on updating SBGN-ED.

ACTION: Tobias will finialize updating SBGN-ED

Frank asks for more example documents, some SBGN features are not yet covered in the examples. For example, not all line endings are covered. The submap example can be quickly fixed by making use of tag nodes. Not all four tag orientations are covered by the examples.

ACTION: Martijn will work on more examples (everybody, feel free to review the specs for missing coverage)

Alice intends to look into C++ bindings.

ACTION: Alice will create C++ bindings for SBGN-ML

Release schedule
================

After some discussion, it was decided to move ahead with the plan and announce a release candidate in December, and if all goes well, do a release in January.

Alice will do the announcement (DONE at this time of writing).

Martijn asks everybody to think about what can be done before HARMONY in NY.

Next Meeting
============

ACTION: Martijn will schedule next meeting in January, in US / EU time zone.

An audio recording of this meeting is available from Martijn upon request.