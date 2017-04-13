Below are the meeting notes for last week's meeting. Unfortunately, somehow my EVO recording got corrupted halfway through, so I might have missed some things. Please let me know if I missed something important.

Meeting notes, Wednesday November 17, 2010

Present: Alice Vileger, Frank Bergmann, Tobias Czauderna, Martijn van Iersel, Sarah Boyd, Augustin Luna

Review of COMBINE
=================

What was Decided?

-   the latest arc proposal was accepted and implemented.
-   In this proposal, combined curve + straight paths are possible

ACTION: Alice will check in curve + straight arc example (MvI postscript: It isn't there yet) ACTION: Alice will post summary of arc solution on the mailing list

Complex containment issue
=========================

-   We want to store the relation between a macromolecule and the complex

that it is part of.

` -> it was decided to fix this for Milestone 1.`

-   Frank proposes a hierarchical system where protein glyphs are just

child elements of the complex glyph.

` -> This is in fact already possible without modification to the schema.`

-   Martijn proposes an alternative system with a "parent" attribute
-   Alice: A macromolecule inside a complex is really a decoration,

similar to state variables. State variables are also represented in a hierarchical manner. Thus Franks proposal is more consistent.

ACTION: Frank will implement his containment proposal, updating the examples where relevant.

Complex containment is not to be confused with compartment containment.

-   Compartment containment must be stored as well
-   The parent-attribute idea is probably better here
-   This needs to be discussed further
-   We will postpone this for the next milestone, not to delay the release.

ACTION: Martijn will open a ticket on compartment containment, and eventually put this up for discussion.

Benchmarking
============

Sarah asks for large test files, and is concerned about file size

-   Tobias tested and compared large networks in SBGN-ML, GraphML and GML.
-   Currently, SBGN-ML takes less than 50% of the equivalent GML
-   SBGN-ML of course doesn't store style attributes such as font etc.
-   As long as we are smart about storing style attributes in the future,

file sizes shouldn't be a concern.

Multiple pathways in a file
===========================

Sarah would like to be able to store multiple pathways (or multiple versions of the same pathway) in the same file.

-   Currently there is no way to do that
-   We decided to add a top-level element named "map".

ACTION: Martijn will add top-level element named map. ACTION: Tobias will post or link large example network in SBGN format on the wiki (at the time of release)

Z-ordering
==========

Martijn proposes to add zorder attribute to every glyph Frank proposes to make every coordinate three-dimensional Alice: it doesn't make sense to have different depths for corner points or waypoints, this information should be stored on the glyph level

Alice: it's a rendering thing, so we postpone it.

Documentation
=============

Sarah asks for posters and slides from COMBINE to be made available online

Where should it go?

-   Martijn prefers to use the wiki, and not svn, because of concerns of

the repository site. The repository will be replicated on many computers.

What other documentation is required? We should have a tutorial to help developers get started, including code example. ACTION: Martijn will write up a tutorial, using ant ACTION: Tobias will write the same, but using eclipse

ACTION: Martijn will write a readme, explaining the directory structure ACTION: Martijn will link or post the LibSBGN poster on the wiki ACTION: Martijn will add a javadoc rule to the build file, and ensure that it generates useful documentation. ACTION: Tobias will put relevant slides with benchmarks on the wiki ACTION: Alice will link or post her presentation on the wiki ACTION: Alice will create a wiki page explaining each element in the schema.

Augustin comments that xsd:annotation tags could be used to generate documentation from XML Schema automatically, and points to this example: <http://neuroml.org/NeuroMLValidator/Transform.jsp?localFile=NeuroMLFiles/Schemata/v1.8.1/Level1/Metadata_v1.8.1.xsd&xslFile=NeuroMLFiles/Schemata/XSD_Readable.xsl>

Milestone 1 Release process
===========================

We decided on the following process: 1. In the coming month, we'll a) prepare documentation and b) update tools to latest changes. 2. Just after the December meeting, we'll announce a release candidate. 3. If no major issues crop up, we'll announce a final release after the January meeting.

ACTION: Frank will update the Rendering extension converter ACTION: Tobias will update SBGN-ED ACTION: Martijn will update PathVisio

Next Meeting
============

Next meeting will be an online meeting (EU-Australia time) in December. Martijn will send around a doodle.