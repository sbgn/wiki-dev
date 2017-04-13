LibSBGN Meeting notes, March 10 2011

Present: Alice, Anatoly, Augustin, Falk, Martijn, Tobias

Report from Gatersleben
=======================

-   Alice, Tobias, Martijn and Falk met in Gatersleben. We worked on ER implementation, which resulted in several test cases and proposals.
-   We also started writing up a manuscript.
    -   Anatoly asks if the library is mature enough for publication? - It is definitely mature enough for somebody who wants to add SBGN-ML support to a tool. Our main goal now is to draw new developers.
    -   Augustin is in favor, he remarks that validation will be important for the reviewers.
    -   Which journal to choose?

ACTION: Falk will send a presubmission enquiry.

Discussion of proposals
=======================

Proposals 1 and 3
-----------------

-   Anatoly remarks that proposal 1 and 3 have the issue that the position of the port could be outside the parent arc, this must be validated. Alice: yes, and we've seen this problem in PD with arcs pointing to process nodes, the coordinates of the arc don't have to match the coordinates of the port.
-   Anatoly asks who is responsible for validation, the reader or the writer? - Both must do validation. You have to validate upon reading because external files could be corrupted. You have to validate upon writing to guard against bugs in your own code.
-   Anatoly asks if SBGN-ML can be used to store a graph without coordinates? - Alice: no it was decided a long time ago that this is outside the scope of LibSBGN.

Proposals 1 and 3 are passed without further discussion.

Proposals 2 and 4
-----------------

-   Regarding proposal 2, the part before the implicit xor in an assignment arc doesn't really have a name, although it has its own look (i.e. no arrow head)
-   For proposal 4, there are two options to group elements belonging to an interaction. 4a proposes a utility function, 4b proposes a grouping element
    -   Solution 4b has the advantage of being platform-independent
    -   4b looks a bit like a hyperedge
    -   If we go for 4b, we might also want to revisit the solution for proposal 2, which has a similar hyperedge-like quality

ACTION: Alice will raise naming of assignment arcs to the SBGN editors.

ACTION: Martijn will adjust proposal 2, and put 4a and 4b up for a vote.

Proposal 5
----------

-   Proposal 5: there isn't much opposition to this proposal anymore. Anatoly recognizes the extra effort that maintaining multiple namespaces bring.
-   GraphML was brought up. Why don't we use GraphML?
    -   GraphML must be heavily extended for our purposes, these extensions will be proprietary (from a non-LibSBGN standpoint).
    -   Tobias: exchange of GraphML between tools doesn't work in practice.
    -   GraphML doesn't have tool support that is as good as XML proper.

ACTION: Martijn will put up proposal 5 for a vote for confirmation

Validation
==========

-   We want to build a validation layer with schematron. For each validation rule, we'll need
    -   an identifier
    -   textual description
    -   A schematron rule
    -   SBGN-ML negative test-case
    -   SBGN-ML positive test-case
-   We'll start gathering rules on this wiki page: [[ValidationRules]]
    -   For Alice, this can go hand in hand with her SBGN editorial duties.
    -   According to Augustin, textual description can be stored in schematron xml.
    -   Augustin also suggests to also include "warning rules" for usage that is not wrong but goes against recommendation.
-   A schematron rule and ant target to run is already checked into subversion by Augustin

ACTION: everybody can start adding rules to the [[ValidationRules]] wiki page

ACTION: Martijn and Augustin will create a [[SchematronHowto]] wiki page

ACTION: everybody: read up on schematron before Harmony, start playing with a couple of rules.

Roadmap
=======

-   After the release, we have to update our Roadmap. After some discussion, we came up with this:
    -   Milestone 2: Support for ER and AF. Addition of schematron validation rules. Release targeted around COMBINE 2011.
    -   Milestone 3: Detailed graphical specification, and extensibility
    -   Milestone 4: Annotations, linking with external models (e.g. BioPAX), and MIRIAM compliance.
-   Extensibility support, i.e. opening SBGN-ML to third-party extensions, was briefly discussed.
    -   Advantage: allows to support more use cases, which can draw in more users
    -   Disadvantage: if an extension becomes too popular, this might cause the same issues as any non-standard format.
    -   Falk: let's put exensibility support in M3, after finalizing ER and AF support.

Bug tracker update
==================

-   The bug tracker was quickly updated to reflect the new roadmap.

Harmony
=======

-   During the Harmony meeting in NY we'll try to set aside a session just for creating rules. This could be any day but Friday, as Falk has to leave early.
-   We'll also set up an informal dinner on Sunday evening, for those who are there.

Final items
===========

-   There won't be another online meeting before Harmony.
-   A recording of this meeting is available from Martijn upon request.
