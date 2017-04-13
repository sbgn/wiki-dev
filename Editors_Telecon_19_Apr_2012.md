Present:

-   Emek Demir (ED)
-   Nicolas Le Novère (NLN)
-   Huaiyu Mi (HM)
-   Stuart Moodie (SM)
-   Falk Schreiber (FS)
-   Anatoly Sorokin (AS)

News from the SBGN world
------------------------

People have been in contact with NLN to convert PD and ER into AF. He redirected them to HM. FS has progressed in generating multiple AF from PD in SBGN-ED. He will present a demo in HARMONY.

ED mentions the existence of 2 SBGN google summer of code projects.

1.  Short description: The main aim of the project is to create SBGN compliant views for the networks used to visualize cancer maps at “cBio Cancer Genomics Portal” . Two stages: First, create a Cytoscape Web based viewer for biological networks using SBGN Process Description notation. Then, customize this component for cBio Cancer Genomics portal so as to overlay genomics data onto such network views.

Funding
-------

A grant application has been submitted to the EU Commission (Virtual Physiological Human). OpenMod will support the development, support and implementation of the COMBINE standards. 2 people will work full time for 5 years on SBGN in the group of FS and NLN.

Specifications
--------------

-   PD L1 V2 (AS) postponed to HARMONY. See user-manual below.
-   ER documentation review (ED)
-   changes done in AF (Huaiyu)

HM presents his plan to have a "process glyph" in AF. A long discussion ensues. NLN asks if we should not have hybrid maps with AF, PD and ER "modules", rather than mixes of nodes. ED takes the same position, saying no to process nodes in AF, but asking to consider Hybrid Maps via the Submaps or some other mechanism. NLN suggests that Huaiyu presents his proposal in HARMONY, and a counter-proposal is tried based on hybrid maps with modules. ED thinks an hybrid map is conceivable if a) we carefully delineate and define the interface b) very explicitly define the semantics. He suggests that we probably need a PD/AR semantic document as well similar to the one he wrote re PD/ER. NLN mentions thatt the situations are very different: 1) having different modules, such as well identifiable (by the user) "submaps" (not the "submaps" of PD) 2) Having nodes from AF and PD together, in the same graph. We will have to have edges linking AF nodes to PD nodes. Both ED and NLN points to the validation problems. HM re-states that mixed / hybrid maps would be good. We will have to work on the naming for the different parts of the maps (frames, layers, …). NLN notes that this does not solve the problem of linking phenotype and input, wich still seems to be one of the problems faced by HM went describing electrophysiology.

PD User manual
--------------

NLN started a draft. The idea is to remove the technical parts from the spec, and focus on the biology. This should be a user manual, and explain how to use SBGN PD, writing and interpreting maps. The user manual to be written for HARMONY is for L2 V1.3. Once it is done, we can focus on the spec for L1 V2, which is free to be very technical, unencumbered by the part targeted to end-users. Note that the user-manual is not a list of examples. People are welcomed to put those examples on the Wiki. AS will help with the user manual.

We will discuss it at HARMONY, gathering input from attendees. Only then will we circulate it to general SBGN mailing list.

Relationship between languages (ED)
-----------------------------------

To be discussed in HARMONY.

HARMONY
-------

NLN precises that the first day (tutorials) is different than the others, with a different audience. NLN would rather have sessions on specific issues rather than dedicated to a language in general. More time should be allowed for developers to work on libSBGN, during which, in parallel, we can discuss issues or work on spec and example. A Google doc will be created to organise the schedule.