Minutes of Editors' Meeting 4-5 March 09
========================================

Location
--------

Hinxton

Attendees
---------

Nicolas Le Novère (NL) Stuart Moodie (SM) Anatoly Sorokin (AS) Falk Schreiber (FS)

Huaiyu Mi attended part of the second day through videocon.

Report
------

On March 4th morning, the editors discussed in details the problems and errata of the PD L1 R1.0 specification, and what to put in PD L1 R1.1 versus PD L1 R2.

A long discussion ensued about the problem of reversible reactions (see picture below). Currently while the semantics of consumption arc is clear, this is not the problem of production arc, that also cover an implicit consumption arc in the case of reversible reactions. Diverse approaches to the problem were envisioned: Changing the semantics of production arc, creating another arc, identical to production, but representing reversibility, and changing completely the syntax of processes.

![Reversibility.JPG]

March 4th afternoon was devoted to discussions around ER L1.

The arrowheads use for assignment and interaction are identical (harpoon). This is confusing. Furthermore, while the assignment convey an idea of information transfer from the state variable value to the state variable, this is not the case of the interaction. On the contrary, the arrowhead are “pointers” t the interactors, but they could also suggest a transfer of information from the outcome to the interactors. Various possibilities were envisioned.

![Interaction.JPG]

Only a few viable possibilities were retained (see below). However, it was felt that the issue should be postponed after L1 R1.

![Interaction2.JPG]

We discussed in detail the representation of n\_ary interactions. It was finally decided to propose a system were an interaction is represented by a circle attached to the arrow pointing to the interactors. The outcomes should all be on the circle. In the case of binary interaction without cardinality, the circle can be omitted.

\[\[Image:nary\_interactions.JPG|nary\_interactions

The representation of existence and location state variables were (re)discussed. The decision for existence was to use a variable represented by black and white semi-circles. The values would be T(rue) or F(alse). For the location variable, we will propose the use of a “pin”.

![Existence.JPG]

The editors then discussed the concepts and structure of Level 1 of the Activity Flow diagrams. This was done with Huaiyu Mi through videoconf. The concept of activity was in particular refined.

The editors discussed the situation of the SBGN website. The website is great, nice and functional, largely thanks to the hard work of Mike Hucka and colleagues. But it is felt that the current situation is a bit dangerous since we are at the mercy of one machine on which we have no control at all. In the long run we should move it to Sourceforge. The question is to know who would take care of the content.

Finally, the editors discussed the situation of SBGN meetings. In particular, the absence of any relevant information on ICSB 2010 called for back-up solutions. Falk will investigate possible SBGN meetings in Wittenberg in late October or Spring 2010.
