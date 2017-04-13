Agenda for meeting of June 2012
-------------------------------

-   External references proposal
-   Level / version and backwards compatibility of SBGN-ML files proposal
-   Submaps proposal
-   Rendering details
-   Wiki
-   Open Round

Agenda for meeting of February 2012
-----------------------------------

-   Release Evaluation
-   Roadmap review / priorities
-   Linking proposal

Agenda for meeting of January 2012
----------------------------------

-   Paper
-   Documentation
-   Public Webpage on sbgn.org

Agenda for meeting of December 2011 (Tue Dec 6, 8 pm CET)
---------------------------------------------------------

-   Release TODO
    -   C++ bindings
    -   auto-generated xsd documentation -&gt; <http://libsbgn.svn.sourceforge.net/svnroot/libsbgn/trunk/specifications/sbgn.doc/>
    -   wiki documentation
    -   tar/zip OK?
-   Paper
-   Open round

Agenda for meeting of October 2011 (Tue Oct 18, 6 pm CET)
---------------------------------------------------------

-   Pre-release TODO
    -   More AF schematron rules
    -   Review bug tracker: <https://sourceforge.net/tracker/?group_id=318225&atid=1338219>
    -   Annotation call-out link
    -   Xml Schema / API Freeze - When?
    -   Documentation review
    -   Document M1-to-M2 API changes list
    -   Fix end-points of arcs on examples
-   Tool support (CellDesigner, SBGN-ED, ...)
-   Paper
-   Open Round

Agenda for meeting of September 2011 (Mon Sep 5, 1 pm CEST)
-----------------------------------------------------------

-   LibSBGN
    -   Schematron utility function
    -   Enum / constants
-   Validation
    -   AF schematron rules
    -   Negative test-cases?
-   Documentation
    -   What documentation do we need?
-   Milestone 2 Release planning
-   Paper
-   Milestone 3 brainstorm
    -   SBML-layout loss-less round-trip conversion?
    -   MIRIAM support
    -   More tool support (Cytoscape...)

Agenda for meeting of August 2011 (Mon Aug 22, 6 pm CEST)
---------------------------------------------------------

-   Milestone 2 Progress
    -   compartmentOrder
-   Extension documentation & demo: [[SBGN-ML_Extensions]]
-   Software support (Current status: [1](http://libsbgn.sourceforge.net/render_comparison/), [2](http://sysbioapps.dyndns.org/RenderComparison))
-   Paper status
-   COMBINE <http://co.mbine.org/events/COMBINE_2011/Agenda>

Agenda for meeting of July 2011 (Thu 7 Jul, 4 pm CEST)
------------------------------------------------------

-   Milestone 2 progress
    -   Validation
    -   AF test cases
-   Review of previous action items
-   Compartment order
-   Extensions/Notes
-   Misc
    -   Short update on paper (Alice)
-   Bug tracker review: bug-tracker review: <https://sourceforge.net/tracker/?group_id=318225&atid=1338219>
-   Open round

Agenda for meeting of May 2011
------------------------------

-   Milestone 2 progress
    -   Validation
    -   AF test-cases
-   Review of [previous action items](MinutesApr2011#Action_items)
-   Milestone 1 leftovers?
    -   When should we deal with submaps? (anything else missing? check bug tracker?) (Alice)
-   Misc
    -   Short update on paper? (Alice)
        -   Questions on current and short term software support
    -   Timing of votes
    -   Extending SBGN-ML: the current milestone list extensions are planned for Milestone 3. However, this is going to hold the language back needlessly. And it will force us again and again to change the milestone plans (as now with introducing colors first). This is something to be rectified as soon as possible. Taking a couple of minutes at the next telecom for this would be warranted. (Frank)

Agenda for HARMONY 2011
-----------------------

Items in bold have a higher priority on the current roadmap.

### SBGN-ML

-   **ER development**
-   AF development
-   Z Ordering / Containment (see also [here](https://sourceforge.net/tracker/?func=detail&aid=3124644&group_id=318225&atid=1338219))

### LibSBGN

-   **write validation rules in [Schematron](http://www.schematron.com/)**
-   implement some layout algorithms and/or integrate with existing layout libraries?
-   implement import and/or export between LibSBGN and...
    -   graphical formats (e.g. SVG)
    -   Paxtools
    -   LibSBML (+ Layout)

Agenda for meeting of February-March 2011
-----------------------------------------

-   Report from Gatersleben meeting
-   SBGN-ER issues
    -   Proposal 1: target of influence is modeled as a port on an arc
    -   Proposal 2: implicit xor in variable assignment is modeled as invisible glyph and three arcs
    -   Proposal 3: outcome is modeled as a sub-glyph on an arc
    -   Proposal 4: Binary interaction modeled as an arc, ternary interaction modeled as glyph plus three arcs.
        -   Proposal 4a: with utility class
        -   Proposal 4b: with extra interaction element
    -   Proposal 5: Organization of ER, AF and PD inside a single XML Schema

(Full text can be found on the mailinglist, see [Proposals 1-4](https://sourceforge.net/mailarchive/forum.php?forum_name=sbgn-libsbgn&max_rows=25&style=flat&viewmonth=201102&viewday=7) [Proposal 5](https://sourceforge.net/mailarchive/forum.php?forum_name=sbgn-libsbgn&max_rows=25&style=flat&viewmonth=201102&viewday=10))

-   Roadmap planning
-   Validation rules and schematron: [[ValidationRules]]
-   bug-tracker review: <https://sourceforge.net/tracker/?group_id=318225&atid=1338219>
-   Next meeting & Harmony

Agenda for meeting of January 2011
----------------------------------

Expected duration: 1h30

-   SBGN-ML issues
    -   Map element discussion
-   Documentation
    -   ACTION: Tobias will link to an example of a large network at release time.
    -   ACTION: Martijn will write a LibSBGN tutorial using ant
    -   ACTION: Tobias will adapt the same tutorial to eclipse
    -   ACTION: Tobias will post slides with his benchmark results on the wiki
    -   ACTION: Alice will continue to document each element of the schema.
    -   Is documentation good enough?
-   Tool support
    -   ACTION: Tobias will finialize updating SBGN-ED
    -   ACTION: Martijn will work on more examples
    -   ACTION: Alice will create C++ bindings for SBGN-ML
    -   Continuous build server status
    -   License discussion
-   Review of bug tracker: <https://sourceforge.net/tracker/?group_id=318225&atid=1338219>
-   Workplan for Milestone 2
-   Gatersleben meeting status

Agenda for meeting of November 2010
-----------------------------------

Expected duration: 1h30

-   Introduction for newcomers
-   Review of agenda and previous action items follow-up
    -   cf previous meeting notes: <http://sourceforge.net/mailarchive/forum.php?thread_name=39EBB265-A49A-4851-9D46-76CB161E0152%40gmail.com&forum_name=sbgn-libsbgn>
-   SBGN-ML 1.0rc
    -   Containment of glyphs
    -   Z-ordering of glyphs/arcs
    -   Different versions of SBGN specifications
    -   Release plans?
-   User feedback
    -   Lack of documentation? (LibSBGN and SBGN-ML)
-   Bug tracker review
    -   Milestone 1: <https://sourceforge.net/tracker/?group_id=318225&atid=1338219&status=1&artgroup=1113352>
-   Open round

Agenda for meeting of September 2010 (Wed 8 Sep, 11 am CEST)
------------------------------------------------------------

Expected duration: 1h30

-   Introduction for newcomers
-   Review of Agenda and previous action items follow-up
-   COMBINE
    -   Poster planning
    -   Choosing presenter
-   SBGN-ML
-   LibSBGN support
-   bug tracker review
-   open round

Agenda for meeting of August 2010 (Mon 9 Aug, 8pm CEST)
-------------------------------------------------------

-   Events
    -   COMBINE poster / session planning
-   LibSBGN support
    -   PathVisio status
    -   Vanted SBGN-ED status
    -   Other tools?
-   SBGN-ML
    -   Defining the directions of edges in SBGN-ML
    -   Falk, via Tobias: "type of diagram should be encoded"
-   House-keeping
    -   Last meeting's "homework" follow up
        -   If done, debrief if need be
        -   If not, reschedule, assign to someone else, redefine scope, or cancel task
    -   Review bug tracker: <https://sourceforge.net/tracker/?func=browse&group_id=318225&atid=1338219>
    -   Next meeting planning

Agenda for meeting of July 2010 (Thu 8 Jul, 2pm CEST)
-----------------------------------------------------

-   Review roadmap: [[SBGN-ML_Roadmap]]
-   Plans for ICSB 2010
    -   [Combine meeting](http://sbml.org/Events/Forums/COMBINE_2010) (should we have a dedicated LibSBGN session?)
    -   SBGN poster??? (Is there one planned? If yes, should LibSBGN get mentioned on it?)
-   Separation LibSBGN / SBGN-ML
-   Governance discussion
-   Jaxb prototype of LibSBGN
-   Build system, Rendering comparison framework
-   Review bug tracker: <https://sourceforge.net/tracker/?func=browse&group_id=318225&atid=1338219>
-   Next meeting planning

Agenda for meeting of June 2010 (Tue 1 Jun, 8pm CEST)
-----------------------------------------------------

-   Catch-up: review of what was said during SBGN 5.5, review of tools and documents that are already available.
    -   we made these test cases:
        -   Simple reaction: [Image](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/adh.png) [XML](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/adh.xml)
        -   Reversible reaction, vertical: [Image](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/reversible-verticalpn.png) [XML](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/reversible-verticalpn.xml)
        -   With compartments and complex: [Image](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/compartments.png) [XML](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/compartments.xml)
        -   States [Image](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/states.png)
-   Review of current XSD proposal (Are we on the right track? Identify gaps and sources of vagueness)
    -   [SBGN.xsd](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/resources/SBGN.xsd) (validates all above files)
    -   Continous build server automatically validates test cases
    -   Relation to BioPAX style sheets
-   Process
    -   Online meetings (schedule, Evo, time zones?)
    -   Roadmap (timeline -&gt; SBGN 6?)
-   Brainstorm
    -   BioPAX references
    -   Label orientation & bounding box
    -   Arcs and Process Node arms
    -   Using JAXB as XML Library
