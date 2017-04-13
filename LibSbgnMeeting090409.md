Summary of the discussion on SBGN exchange format, Waiheke Island, New Zealand, 09 April 2009
---------------------------------------------------------------------------------------------

Present: Huaiyu Mi, Yukiko Matsuoka, Stuart Moodie, Alice Villeger, Frank Bergman, Emek Demir, Stefan Hoops, Sarah Boyd

------------------------------------------------------------------------

Whiteboard notes from libSBGN meeting Waiheke Island 9 April 2009:

[libSBGNMtngWhiteboard1.pdf](/sbgn/wiki-files/blob/master/LibSbgnMeeting090409/LibSBGNMtngWhiteboard1.pdf)

[libSBGNMtngWhiteboard2.pdf](sbgn/wiki-files/blob/master/LibSbgnMeeting090409/LibSBGNMtngWhiteboard2.pdf)

First task was to establish a features/wishlist, which was written on the whiteboard exactly as follows:

API Scope of libSBML Exchange format Validation Interoperability coversion

`     * SD -> ER (?)`
`     * PD -> AF (?)`
`     * ER -> PD (?)`

Export/Import

`     * SBML`
`     * BioPax (L3(?))`
`     * CellML`

Auto layout

------------------------------------------------------------------------

Stuart then proposed that an immediate need is for the exchange format to be developed, and proposed that the meeting moved to a discussion on how to develop this format.

Huaiyu mentioned that he has developed a diagram with all PD 'features' shown, that he is willing to provide this to help people develop the exchange format.

Stuart invited Alice to present her thoughts on the issues.

Alice suggested that there are several layers:

`     * Rendering/style`
`     * Graph layout`
`     * Biological statements`

Alice also pointed out that cloning and submaps affect the topology of the graphs.

Stuart added that there is also the division between the conceptual model (which is non-redundant), and the underlying visual model.

Stuart then noted that the SBGN diagram has EPNs, Connections, processes etc,. and we would be interested in preserving locations and colours.

Frank raised the issue of validation.

Sarah suggested that SBML is validated by examining the format of the file, similarly the exchange format could be validated by the format of the file.

Stuart talked about the exchange format needing to handle the elements of the graph:

`      * graph topology is straightforward: node location, edge connections`
`      * problem: how are arcs rendered?`

Sarah suggested that this could be determined by the software.

Stuart suggested that it should be in the specification.

The suggestion was made by (?) that bounding boxes and node sizes are preserved.

Sarah made the suggestion that what we really want to preserve is the topology, regardless of the scale.

Huaiyu raised the question of who is going to use it?

Sarah extended this question to how is it going to be used? As an example scenario of what we need to address, Sarah generates a graph in Dunnart, sends it to Alice who edits it in Arcadia, and then sends it back to Sarah, who edits it further in Dunnart, then Sarah and Alice publish it, after which Stuart takes a copy opens it in EPE. Every single time, it looks the same.

Stefan suggested using style sheets. Stuart and Alice agreed this was a good approach.

Stuart suggested that we should be able to preserve colour, line thickness etc, but exchange format should only have to preserve SBGN specifications:

`      * SBGN topology`
`      * Location/size - where it is drawn`
`      * Colour/line thickness/rendering - problematic because not part of the specification`
`      * Edge routing`

Alice said her preference is for preserving topology and location/size and edge routing, and deal with the rest later.

Stuart then raised the issue of file format representations, suggesting that we talk about current solutions, and work out what they offer, whether any work.

Huaiyu said the next step would be to then look at combining or modifying, and Stuart agreed.

With group input, Stuart noted that the current solutions/approaches, include:

`      * SVG`
`      * SBML layout and rendering`
`      * GML`
`      * XML`
`      * XGML`
`      * Fedor => javascript solution (BioUML)`

Stuart mentioned that Falk has been advocating GraphML.

Emek said that SVG is overkill, because don't need to define shape.

Sarah asked if Falk has compared GraphML and GXL, and Stuart said he has.

Emek said that we cannot delegate model representation, we need to extend the language.

Huaiyu suggested that we summarise what is discussed/proposed here, and post it on the list for discussion.

Emek then also noted that the choice is also determined by validation.

The consensus from the group was that XML-based is best format.

Alice suggested that we can start defining object model immediately.

Stuart then moved the discussion on to deliverables, with the explicit understanding that Falk was not at the meeting to contribute, and without knowing what Falk has to say on the subject.

The deliverables were established as:

`   * Develop an XML schema`
`   * Develop a working version that we can play with`
`   * Have a demo/working version by the next meeting (September) that shows exchange between different applications`

The decision was made to have this project hosted in Sourceforge. Stuart would create a package under the SBGN project.

It was noted that BoUML have C++ and Java autogenerators.

Alice was nominated and agreed to take the lead for this project. Emek agreed to provide an initial XML schema. Sarah was nominated to lead this, with Alice's help, Sarah mentioned she was not altogether confident that she would be able to be responsible for this to completion, but agreed to start in this role. Demos for this would be provided by Frank, Stuart, Yukiko, Sarah and Alice, also Falk? Stuart would set up a list on SourceForge.

The goal would be to have this accomplished for the next meeting in September.

Falk's input would be sought.

------------------------------------------------------------------------

Follow-up to the meeting, in email correspondence:

Emek provided an initial xsd.

Stuart (unsuccessfully) tried to subscribe everyone to the libsbgn mail list, will try again.

Sarah raised the issue of not duplicating effort, and asked whether the SBML layout extension provides a solution to the immediate needs of the exchange format. Frank supported these comments and supplied further resources for everyone to look at and then discuss.