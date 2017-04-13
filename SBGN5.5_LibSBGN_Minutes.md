Timeline
========

Disrupted schedule due to Icelandic ash cloud flight restrictions:

-   Hacking on Thursday (morning and afternoon)
-   Discussions on Friday morning

People involved
===============

During Thursday hacking sessions:

-   Tobias Czauderna
-   Stuart Moodie
-   Anatoly Sorokin
-   Martijn van Iersel
-   Alice Villeger

Taking part in Friday discussions:

-   Nicolas Le Novère
-   Falk Schreiber

+ same as Thursday (other people were present but didn't contribute, as far as I remember)

Outputs
=======

Work on the SBGN exchange format

LibSBGN sourceforge project
---------------------------

<https://sourceforge.net/projects/libsbgn/>

Machine readable files
----------------------

a growing number of test cases expressed as

-   PNG = visual examples
-   XML = SBGN-ML draft
-   GML ( <http://www.infosun.fim.uni-passau.de/Graphlet/GML/gml-tr.html> )

+ the corresponding XSD file (work in progress)

cf. SVN repository: <http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/>

Human readable description
--------------------------

a wiki page on how the format works, why some choices where made, what doesn't quite work yet, etc.

cf. [[Exchange_Format]]

Who did what and when
=====================

Everybody took part in live discussions. Nobody took minutes per se...

Martijn wrote and edited in real time(!) the current files (examples + XSD) based on what people would discuss and draw on the board. Martijn also set up an automatic system to check the schema validates against the examples (=&gt; URL?)

In parallel, and after the meeting, Alice wrote the first few versions of the wiki page on the exchange format.

There was a lot of changes between the draft obtained at the end of day 1 and the revision after day 2. Hopefully, all the examples and wiki explanations are now up-to-date again, but there may still be some inconsistencies.

Summary of the issues covered
=============================

cf. Wiki page [[Exchange_Format]]

SECTION 1-4 SCOPE, PURPOSE, BASIC REQUIREMENTS, IMPLEMENTATION
--------------------------------------------------------------

These are mostly reminders of what had been decided in previous meetings and email discussions (from memory, I haven't checked every email or minutes...) IMPLEMENTATION also introduces the method used during SBGN5.5 to develop the current XSD, based on a series of examples which illustrates different aspects of the SBGN specification.

SECTION 5-7
-----------

The following sections describe the various concepts which emerged from that approach. This early draft is no way perfect, but should provide a framework for future discussions.

### SECTION 5: GENERIC NODE CONCEPT

An abstraction introduced to deal with characteristics which are common to many SBGN glyphs: EPN, PN, Logic Operator Nodes, but also Compartments, Units of Information, etc. (Labels? possibly... basically, anything which isn't an Arc?) The exact SBGN nature of a Node is given by its class (string = current SBGN name, or SBO term? Former easier to read, latter more "future-proof") Some key questions include geometry (how to describe glyphs whose shape can vary within the same bounding box) and how to deal with containment (parent/child relationships between glyphs)

### SECTION 6: FIRST EXAMPLE

Deals with simple concrete Node classes, also introduces Arcs. Simple EPNs (no inner components, no decorations) are easy to describe within the Node framework (even though some issues remain, cf. above)

Process Nodes proved more problematic, because their description is tightly linked to that of Arcs. Different approaches where studied to deal with the concept of Port, i.e. the fact a PN has pseudo-arcs pointing out of two distinct sides.

There might be some underlying problems with the current SBGN specifications, e.g.:

-   which class of arcs should be used in reversible processes
-   what geometry is allowed for the pseudo-arcs
-   whether these pseudo-arcs should really be part of the PN glyphs

After a lot of discussions, it was decided to describe Ports explicitly within a Process Node, and have Arcs refer directly to these Ports.

### SECTION 7: SECOND EXAMPLE

Deals with containment. Was only briefly touched during discussions.

There are two ways to represent containment:

-   either through the hierarchy of the XML tree:

<parent>
` `<child/>
` `<child/>
</parent>

-   or in a flat list, via a reference attribute:

<parent id="p1"/>
<child ref="p1"/>
<child ref="p1"/>

The latter approach was preferred to deal with the Compartment/EPN relationship, but the former approach may be more appropriate in some other cases (e.g. the Complex/InnerEPN relationship or the EPN/StateVariable relationship) More discussions are needed on the issue.

### SECTION 8-9

Logic Nodes and Arcs, and some more questions still unresolved, and mostly un-discussed.

Next actions?
=============

Live meeting: remote conference with people who missed SBGN5.5?

-   What should be on the agenda? cf [[MeetingAgenda]]
-   When is a convenient time? (Martijn set up a Doodle to pick a date)
-   What tool should be used to communicate? (Dagmar suggested <http://evo.caltech.edu/evoGate/> )

Bug tracker: to identify and address each issue independently

-   cf. various headers in wiki, and points marked with /!\\
-   use sourceforge tracker?
-   discuss each independent issue via mailing list?

Diagram examples:

-   define more?
-   refine current ones?

=&gt; who will do what? (cf. concrete output tasks: PNG, XML, XSD, wiki, bug tracker, mailing list...)