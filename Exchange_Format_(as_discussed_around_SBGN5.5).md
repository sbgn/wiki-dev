a.k.a. "SBGN-ML"

Purpose
-------

Exchanging diagrams between the various tools supporting SBGN

Scope
-----

In the first instance, SBGN PD, with a focus on semantic (conceptual model) and layout (dimension and position of glyphs in the visual model)

Rendering (color, font, precise shape of the glyphs...) is less important and will be dealt with in a later version.

Basic requirements
------------------

### Rule \#0 : exhaustivity and unambiguity

The exchange format should allow to represent unambiguously (in term of conceptual model) the full spectrum of the SBGN PD specifications.

However, in the first instance, there is no need to provide mechanisms to represent things which are not part of the specification (e.g. rendering style such as color)

Future versions may attempt to provide such mechanisms, but support for these by SBGN-ML compliant tools is optional.

### Rule \#1 : easy to draw

In the first instance, the exchange format should describe the position and dimension of visual element via explicit, absolute coordinates.

This ensures that no complex geometric computations are required to render the diagram with commonplace programming tool-kits (e.g. Swing, Qt, etc.)

SBGN-ML compliant tools should not be assumed to support advanced drawing functionalities such as edge routing.

**/!\\** There is no full consensus on what is "advanced" and what is "common-place": e.g. can we assume all tools can draw centered labels, or should absolute coordinates be provided? In case of doubt, err on the side of caution and provide absolute values?

In a future version, mechanisms to describe relative position and advanced layout rules (alignment, distribution, etc.) are likely to be proposed. However, these will be tightly linked to the implementation in LibSBGN of a tool translating these relative parameters into absolute values.

### Rule \#2 : easy to interpret

The exchange format should make all semantically-relevant relationships explicit.

This ensures no complex image analysis operations are required to infer the conceptual model from the exchanged diagram.

For instance, the fact that an edge points at a given glyph should be stated explicitly: tools should not need to infer that relationship from the relative coordinates of these graphical objects.

Similarly, the relationship between an EPN and its compartment should be explicit (not inferred from geometric containment)

**/!\\** Some relationship can be inferred without relying on complex image analysis. For instance, cloned EPNs bearing the same labels in the visual model allow (by simple string comparison, since labels are unique within a compartment) to infer the existence of corresponding EPNs in the the conceptual model. The consensus so far has been that the exchange format should only describe the visual model, and keep the conceptual model implicit (as long as its inference remains simple, as in the clone identity example)

Implementation
--------------

Custom-made XML format, inspired from existing formats, e.g.:

-   SBML Layout + Rendering extension?
-   SBML CellDesigner extension?
-   GraphML?
-   GPML?
-   SVG? (for advanced rendering?)
-   etc.

In its final form, SBGN-ML will be represented by an XSD, complemented by a human readable description (currently, this wiki page)

During the drafting stage, the format will be expressed through a number of examples: for each test-case, an XML representation will be attached to a given SBGN diagram.

A new XSD will be extrapolated from each new example (before and after discussions and subsequent modifications), and compatibility with previous examples will be tested systematically.

At the end of the process, the final XSD should satisfy all the basic requirements described above (exhaustivity, easy to draw, easy to interpret, ...?)

For a fully up-to-date version, please check the SVN repository: <http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/>

Generic Node concept
--------------------

A number of SBGN objects (which may or may not be grouped together under the same banner in the current SBGN nomenclature) happen to share similar visual properties. The description of these properties is regrouped in SBGN-ML under the generic "Node" abstraction. The purpose of this generic abstraction is to avoid repeating the same basic descriptions and discussions for each specific SBGN class.

A Node is a graphical object...

-   drawn as a visible shape (usually predefined, depending on the node's precise type)
-   bound by an invisible rectangular box
-   often (depending on its type) containing a text label
-   sometimes (depending on its type) containing a number of optional sub-nodes
-   usually/always? identified with a unique id (which other objects can refer to when expressing a relationship with the Node)
-   ALWAYS assigned a specific, concrete SBGN class (e.g. "macromolecule", "and operator", etc.)

This means nodes can be Entity Pool Nodes, Logical Operator Nodes or Process Nodes, but also Compartments, Units of Information or State Variables... In fact, any glyph that is not an Arc.

### Proposed XML representations of a Node

<node class="specific_node_type" id="node1">
` `<bbox x="0" y="0" w="10" h="10" />
` `<label text="Multiple lines\nseparated\nby optional line breaks" />
` `<node class="..." id="node2">
`  [...]`
` `</node>
` `<node class="..." id="node3">
`  [...]`
` `</node>
</node>

### Problem 1 : class

**/!\\** In the draft version of the XSD, a *class* is expressed as a human-readable string (e.g. "compartment", "complex", etc.). In the final version, these are likely to be substituted with the corresponding SBO terms?

### Problem 2 : geometry

**/!\\** The bounding box is enough to describe fairly accurately a number of glyphs. However, some glyphs will be over-defined (e.g. fundamentally symmetrical glyphs like "simple chemical" or "source/sink" only need a radius, not a width and height) and some under-defined (e.g. different "macromolecule" shapes can fit in the same rectangular bounding box: an angle and radius parameter need to be defined for its corners to fully constrain the shape). Over-defined shapes can be ambiguous (is the actual radius the width or the height?) and may require additional validation steps (does width equals height?) to accept the file as a valid SBGN diagram description. Under-defined shapes may lead to a valid diagram in one tool being redrawn as a invalid diagram in another tool (as nodes and edges which initially don't overlap may end up overlapping). At the moment, in the current draft, these issues are UNRESOLVED (and may remain so in the first version of the exchange format, as their actual consequences seem relatively minor: the conceptual model is -probably?- not affected, and the overall layout is preserved)

### Problem 3 : label

The label element would be skipped in unlabeled Nodes such as Process Nodes or Source/Sink.

**/!\\** The label described above is not given any geometric information and can only be assumed to be centered. This may contradict the "Easy to draw" rule (although it seems possible to infer a label bounding-box relatively easily from its node's bounding box). Also, some Nodes' labels are not centered by default: e.g. in a Compartment, they can be placed anywhere. These "free-floating" labels do need their own bounding box. Question: should ALL labels have a bounding box? Should they then be regarded as Nodes in their own right? (and be described as a child of the Node they label... just like Unit of Information and State Variable nodes?). This "Labels as independent Glyphs" approach is successfully used by the SBML Layout Extension.

Label as Node example proposal? (text could be either an attribute or a child element... Any preference?)

<node class="label" id="optional or mandatory?">
` `<bbox x="0" y="0" w="10" h="10" />
` `<text>`Multiline\n still works`</text>
</node>

### Problem 4 : containment

**/!\\** The concept of container nodes holding children nodes is a contentious issues. In some cases, it seems to make sense to express the parent/child relationships via a XML hierarchy. In other cases, it seems more appropriate to express the relationship via a reference from the child to its parent's id.

For instance, the identity of a Macromolecule node is expressed via its Label and State Variables. Similarly, the identity of a Complex is expressed via its inner elements. Bundling these identifying children nodes inside of their parent node seems sensible.

<node class="complex" id="c1">
` `<node class="some_epn_class" id="epn1" />` // not a "real" EPN (can't directly take part in a process), but looks exactly the same as a real one`
` `<node class="some_epn_class" id="epn2" />
</node>

However, should the XML description of EPNs be nested inside the description of their Compartments? Or should this relationship be expressed via a "compartment" attribute on EPNs? Recent discussions seemed to favor the second option, but the reason why have not been clearly expressed.

<node class="compartment" id="c1"/>
<node class="some_epn_class" id="epn1" container="c1" />
<node class="some_epn_class" id="epn2" container="c1" />

In any case, the containment relationship (not just visual, but conceptual) needs to be expressed explicitly (cf. rule \#2)

Example 1 : simple network
--------------------------

One process (PN1), where EPN1 is consumed, EPN2 is produced, and EPN3 modulates PN1

\[insert diagram\]

Proposed notation:

### Entity Pool Nodes

<node class="unspecified_entity" id="epn1">
` `<label text="EPN 1\nanother line\njust for fun" [font-size="..." font-family="..."] />
` `<bbox x="0" y="0" w="100" h="200" />
</node>

#### Geometry

cf. [\#Problem 2 : geometry](/#Problem_2_:_geometry "wikilink")

The bounding box is relevant layout-wise. However, it does NOT fully constraint the exact shape of some glyphs. For instance, the macromolecule glyph:

\[insert illustration showing two different macromolecule shapes fitting in the same bounding box\]

In the first version of the exchange format, we don't care (the diagram may look a bit different when rendered by different tools, but it does not change its meaning, and the layout is likely to remain valid = it's a rendering issue)

#### Label

cf. [\#Problem 3 : label](/#Problem_3_:_label "wikilink")

-   Multiline labels are described by introducing line breaks (\\n or anything else appropriate) in the text attribute.
-   Shouldn't the label be given a bounding box, or at least a position? (cf rule \#1)
-   The SBML layout extension allows free floating labels, not attached to any glyph. Labels are graphical objects like any others, with an **optional** parent node. Is this valid in SBGN? Should SBGN-ML allow to define such independent labels?
-   Optional style attributes may be attached to labels in a future version (but not in the first draft)

### Process Nodes

Work in progress: there are a number of issues with these nodes, which are also linked to the Arc definition question.

#### Early proposal

<node class="process_node" id="pn1" orientation="???">
` `<bbox x="500" y="0" w="100" h="50" />
` [...] // Unclear if the node should have children or not, cf. the Arc issue below`
</node>

#### Glyph components

Proposed terminology to facilitate discussions on process node (I don't think it's defined in the SBGN specs? or is it?)

-   Core = the central fixed shape of a process node (can be a square or a circle, depending on its precise type)
-   Arm = one of the two lines which connects the core of a process node to it production or consumption arcs. Can be right-hand side or left-hand side.
-   Port = the "external" end-point of an arm, where the production or consumption arcs connects with the process node glyph. Again, can be right-hand side or left-hand side (cf. arm side)
-   Right/Left-Hand side = these are conceptual (e.g. the sides of a chemical reaction = input and output if irreversible), not visual (independent of any rotation of the glyph)

#### Geometry

Does a bounding box make sense? Aren't w and h the same? The core of a process node is either a square or a circle...

A bounding box only makes sense if we consider it also surrounds the arms of the process node.

\[insert diagram?\]

But the precise shape of the glyph is then under-defined: e.g. what is the respective length of each arm? The box does not need to be centered...

The problem is similar to the under-constrained macromolecules described above. Can this be considered as a mere rendering problem?

#### Ports and Arms

The problem here goes deeper: there is a disagreement on how to interpret the SBGN PD specifications on process ports.

-   on the one hand, the process node glyphs in the specs always represent arms as short straight lines of equal length, either horizontal or vertical (depending on the overall node orientation)
-   on the other hand, the text description of process nodes does not imply such constraints: the port points can be located anywhere (possibly very far, or very close from the square), and the arm which links each port points to the middle of one side of the core can be of any shape (they don't have to be straight lines)

\[diagram to describe second possibility?\]

Most tools prefer to implement the first, more constrained approach, but there is nothing in the current specification explicitly forbidding the second approach. This is a SBGN problem:

-   should the current process node remain a single multi-component glyph with a very variable overall shape? (Or should that shape be more constrained?)
-   should the process node glyph be reduced to its core, and the process node "arms" be defined as proper arcs? (and an invisible "port" node be defined for the connection point between these new "left/right arm" arcs and the classic consumption/production arcs?)

Visually, both definitions are equivalent, but they imply different validation rules (as nodes and arcs overlap rules are different)

Until this SBGN question is resolved, how should the exchange format deal with the issue?

The bounding box approach makes strong assumptions on the arms shape and the ports location relatively to the core. It can be made slightly more flexible by (in increasing order of flexibility):

-   allowing arms to have a length (but still consider them to always be horizontal/vertical)
-   giving ports coordinates (and just assume the arm is a straight line) = this is the approach taken in the current XSD, cf example below
-   describing arms as arcs (with a possibly complex route: polyline, spline, etc.), and ports as nodes with no dimension, just a position?

#### Orientation

Regardless of the approach taken to deal with ports and arms, process nodes have an orientation: conceptually, they have a right-hand side and a left-hand side (be the process reversible or not), and visually, these sides can be pointing East/West, North/South, West/East or South/North.

If the node is simply described as a bounding box, orientation can be considered implicit (w&gt;h = horizontal, h&gt;w = vertical), but this makes the file more difficult to interpret both visually and conceptually (cf. rule \#1 and \#2). Also, this system probably breaks down if we allow "free-form" arms, cf. discussion on ports and arms above?

If orientation is stated explicitly, are two states enough (vertical or horizontal, cf. current XSD) or should we define four:

-   vertical with the conceptual left side
    -   either on the top (North)
    -   or at the bottom (South)
-   horizontal with the conceptual left side
    -   either on the left (West)
    -   or on the right (East)

The need for four states may emerge when we deal with reversible processes, as arcs on both sides are of the same class (production), but we still need to discriminate between these two sides, at the conceptual level.

Although there may be a way to describe these arcs and their precise source/target unambiguously, without having to define 4 rotation states? Cf. discussion on Arcs below...

#### Current proposal

Based on all the above discussions (and designed to work along with the current Arc proposal)

<node class="process" orientation="horizontal" id="pn1">
` `<bbox x="150" y="100" w="20" h="10"/>
` `<port x="0" y="0" id="pn1.1"/>
` `<port x="0" y="0" id="pn1.2"/>
</node>

### Arcs

Work in progress... Contentious issues ahead!

#### Basic properties

Arcs are SBGN glyphs which:

-   visually connect two nodes together = represent a conceptual relationship between these two nodes (the type of nodes allowed syntax-wise depends on the arc type, cf. SBGN specs)
-   in PD, currently appear to have two conceptually distinct ends? "Multipartite" graph, with one type of node at one end, another type of node at the other end (asymmetric relationship = this can be interpreted as the "direction" of an arc?):
    -   e.g. consumption and production arcs have a process node on one end, and an EPN on the other end
    -   modulation arcs have a process node on one end, and an EPN or a logic operator on the other end
    -   logic arcs have a logic operator on one end, and an EPN or a logic operator on the other end...
    -   but this may not always be possible to generalize (e.g. different rules in ER, with arcs pointing at other arcs! and may also not always be true in future versions of PD?)
-   have no precise shape, apart from being a continuous curve (but the route they follow must abide by a number of layout rules, e.g. no overlapping)
-   have specific decorations on some ends (depending on their precise type) (the decoration may become part of the Node glyph instead, in future versions of the specs?)

#### Visual arcs, conceptual arcs

The description of arcs involves a certain amount of redundancy, as in order to satisfy both rule \#1 (easy to draw) and rule \#2 (easy to interpret), two sets of information that could theoretically be inferred from one another (visual appearance, e.g. coordinate of the end of an arc <=> conceptual relationship, e.g. this arcs is connected to this node) are both written explicitly. This may mean more work for validation tools (check that both sets of information are consistent??)

#### Conceptual relationship: Hierarchy or Flat List?

A previous draft proposed consumption, production and modulation arcs to be described as children of process nodes (this is the approach taken, for instance, by the SBML layout extension). Similarly, logic arcs could be children of logic operator nodes.

Here is how it could have more or less looked like on example 1: (check XSD in SVN repository for exact example?)

<node class="process_node" id="pn1">
` `<bbox [...] />` // Geometric description of the process node itself, including arms and ports? (cf. Process Node section)`
` `<arc class="consumption" ref="epn1">
`  [...] // Geometric description of the arc path`
` `</arc>
` `<arc class="production" ref="epn2">
`  [...] // Geometric description of the arc path`
` `</arc>
` `<arc class="modulation" ref="epn3">
`  [...] // Geometric description of the arc path`
` `</arc>
</node>

The arcs bundled inside a given node describe a relationship between that node, and the node linked to by their *ref* (reference) attribute. Their conceptual role and visual appearance is expressed by their *class* (a human readable string in the draft version, but could be a SBO term in the final version). Their precise shape can be described in a number of ways (cf. the Arc Geometry section)

Another, similar (but more "clustered") proposal involved creating arc groups for each side of the process node (left and right), in order to disambiguate reversible processes (cf. section on the Reversible Process Problem):

<node class="process_node" id="pn1">
` `<bbox [...] />
` `<left>
`  `<arc class="production" ref="epn1">` [...] `</arc>
`  `<arc class="production" ref="epn2">` [...] `</arc>
` `</left>
` `<right>
`  `<arc class="production" ref="epn3">` [...] `</arc>
`  `<arc class="production" ref="epn4">` [...] `</arc>
` `</right>
</node>

In this version, the left and right objects could contain information on the process node's port geometry: (x,y) location of the port itself, possibly (x,y) location of the other end of the arm (on the side of the process core) or even description of the full path of the arm.

Both hierarchical proposals were later rejected after further discussions. One of the reasons invoked was that this approach could not be transferred to other SBGN diagrams (e.g. ER) and may become invalid in the future if the PD specifications were to change.

The approach eventually advocated is that of a flat list of arcs, referring, for each of their ends, to the id of a node (listed in another, separate part of the file), e.g.:

<arc class="consumption" ref1="epn1" ref2="pn1">` // conceptual relationship on both ends + conceptual type (= visual appearance hint)`
` [...] // precise geometric description`
</arc>

This flat list approach was actually the very first approach discussed at SBGN5.5. But it had to be refined further to address a number of other problems.

#### The Reversible Process Problem, and the role of Ports

Arcs don't just point at a process node, they point at a side of that process node. The problem can be somewhat ignored when dealing with an irreversible process, as the class of the arc hints at which side of the process the arc should be pointing at:

<arc class="consumption" epn="epn1" pn="pn1">` [...] `</arc>` // left hand side`
<arc class="production" epn="epn2" pn="pn1">` [...] `</arc>` // right hand side`

However, in the current SBGN specification, in the case of a reversible process, we have production arcs pointing at either side of the process node. The arc class does not suffice anymore to disambiguate the conceptual description of the process:

<arc class="production" epn="epn1" pn="pn1">` [...] `</arc>` // left or right hand side?`
<arc class="production" epn="epn2" pn="pn1">` [...] `</arc>` // left or right hand side?`

Arguably, it is theoretically possible to infer this conceptual information from the visual description of the arcs (their end-points are located at different coordinates, depending on the side they belong to), but this would go against rule \#2 (easy to interpret)

A number of proposals have been made to address the reversible process problem. One solution was described in the previous section (second hierarchical approach). A flat-list approach offers other solutions, e.g.:

-   Keep the class - side equivalence, but add a "reversible" attribute which modifies the visual style of the arc? (can also be used with the first hierarchical approach: the reversible attribute would then be on the parent process node instead of the arc)

<arc class="consumption" reversible="true" epn="epn1" pn="pn1">` [...] `</arc>`  // left`
<arc class="production" reversible="true" epn="epn2" pn="pn1">` [...] `</arc>`  // right`

(This solution has been rejected, in particular because it diverges too much from the current SBGN specification)

-   Keep the appropriate SBGN class, but add an attribute indicating the side the arc is pointing at?

<arc class="production" epn="epn1" pn="pn1" side="left">` [...] `</arc>`  // left`
<arc class="production" epn="epn2" pn="pn1" side="right">` [...] `</arc>`  // right`

A benefit of this approach is that it works regardless of the class chosen in SBGN to describe reversible arcs (it is very possible that in a future version, *reversible* becomes a separate Arc class, similar in appearance to a production arc, but conceptually distinct. And these arcs may even change in appearance in later versions)

A limitation of the second approach is that it relies on predefined ports (left and right). It may be difficult to extend if the SBGN PD specification evolves to define other types of ports (and what about ER?)

Also, independently from SBGN, a more generic concept of port may be useful in SBGN-ML to describe the connection between arcs and visually complex nodes? (e.g. an EPN with a large number of state variables, with a limited number of spatial "slots" on its sides, through which to route arcs???)

Discussions on that topic had to be cut short towards the end of SBGN5.5, but a consensus emerged towards using generic ports, defined on process nodes, and referred to by arcs (cf. Current Proposal below. The "epn/pn" attributes have become "source/target" children, and the "pn+side" concept has been merged into a more generic "port ref" concept, but the core idea remains similar)

#### Current Proposal

The current proposal describes arcs in a flat list. Each arc belongs to a class which describes its conceptual role and provides a hint regarding the way it should be decorated (arrow, diamond, etc.). Each end of the arc (source, target) is described both in term of geometry (x,y coordinates) and conceptual relationship (reference to a node id, or to a node's port id). Using references to ports instead of process nodes allows to solve the reversible process problem (regardless of whether we create a reversible arc class or not)

<arc class="consumption">
` `

` `<target x="0" y="0" ref="pn1.1" />
</arc>
<arc class="catalysis">
` `

` `<target x="0" y="0" ref="pn1" />
</arc>
<arc class="production" >
` `

` `<target x="0" y="0" ref="pn1.2" />
</arc>

/!\\ There is no information on the exact geometry of the arc (path taken, e.g. multiline, spline curve with control points, etc.). The SBML layout extensions proposes a way to describe this.

/!\\ The port coordinates are described twice: once on the definition of the port on the process node, and a second time when giving the coordinates of the arc target. I seem to remember we agreed no coordinates should be given at the arc level when referring to a port (as opposed to a node). Should this be discussed again and/or the XSD be corrected?

/?\\ Is the source of a consumption/production/modulation arc always an EPN, and the target always a PN or a PN port? Or can it be the other way around? (this matters, as tools need to know at which end of the arc to draw the decoration: can we assume a modulation arc decoration is always located at the target coordinates, or do we need to check the class of the source and target *ref* to decide where to draw the decoration?). If source or target can be of any type, maybe they should just both be called "end"?

/!\\ The decoration's geometry is not described at all. Is this only a rendering problem (something to deal with in version 2?) or should the decoration be given a bounding box, etc.? (and be treated as yet another SBGN-ML Node?)

Example 2 : containment
-----------------------

These questions have not been discussed thoroughly during SBGN5.5 due to lack of time.

### Compartment

A rectangular compartment can be described by a bounding box and a floating label. From a graphical perspective, they are not too different from EPNs, especially complexes... (they can even have units of information on them)

From an SBGN-ML perspective, this means Compartments are Nodes.

There is a parent/child relationship between Compartments and the EPNs they contain.

Should these EPNs be nested inside the compartment they belong to? (like complex elements can be nested inside their complex?)

<node class="compartment">
` `<node class="some_epn_class">
` ...`
` `</node>
` ...`
</node>

or should they just refer to the compartment via an attribute?

<node class="compartment" id="...">
`...`
</node>
`...`
<node class="some_epn_class" compartment="...">
`...`
</node>

The issue wasn't discussed thoroughly, but a preference was expressed for the second method.

The question of how to describe the geometry of non-rectangular compartments has not been tackled! (have a look at SBML layout/rendering extension?)

### Complex

A complex is an EPN. It contains glyphs which look exactly like EPNs (same graphical characteristics). Functionally, these internal glyphs are not real EPNs. They can't be produced or consumed directly. SBGN currently allows them to modulate process nodes (just like perturbations), but this property may be dropped in future SBGN versions.

From an SBGN-ML perspective, real EPN and "inner EPNs" (= pseudo EPNs) are both Nodes.

Question 1: should real EPNs and inner EPNs be described by the same set of *class* values? (e.g. "macromolecule", "simple chemical", etc... or their SBO equivalent in the final version):

-   from a visual style perspective, this makes sense, as real EPNs and inner EPNs have the exact same graphical characteristics
-   but from a validation perspective, a macromolecule inside of a complex is not the same thing as a standalone macromolecule (the latter can be produced or consumed by a process, the former cannot)

Solution 1: define a new set of classes for inner EPNs (e.g. "inner-" or "pseudo-" + normal name... But what about corresponding SBO terms?)

Solution 2: use the same set of classes, but find another way to disambiguate the situation for validation purposes (e.g. use the fact that "inner EPNs" will always be attached to a container EPN, while "real EPNs" don't)

Question 2: We've got a parent/child relationship between inner EPNs and their complex. Should we express that containment via the XML tree, or list inner EPNs in a flat list? (either along real EPNs, or in a separate part of the file)

Solution 2.1: Flat list. Inner EPNs have an extra attribute (e.g. complex="id of the complex") which expresses the containment relationship and differentiates them from real EPNs for validation purposes.

Solution 2.2: XML tree. Inner EPNs are children of their complex. It should be easy enough to differentiate them from real EPNs for validation purpose? (as they are not listed at the same level in the XML tree). Also, all the elements identifying a complex are grouped together instead of being scattered in different places.

<node class="complex" id="...">
` `<bbox x="..." y="..." w="..." h="...">
` `<label text="...">
`  `<bbox x="..." y="..." w="..." h="...">
` `</label>
` `<node class="macromolecule" id="?">` // do they need an id if no arc ever refers to them?`
`  `<label ... />
`  `<bbox ... />
` `</node>` `
` [...]`
</node>

/!\\ The (optional) label of a complex definitely needs a bounding box! (it can't be just centered)

### Unit of information and state variables

They are graphical elements with a label, a shape in a bounding box, etc. They belong to an EPN (or a compartment)

They could/should? probably be nested in the EPN/Compartment they belong to:

<node class="some_epn_class" ...>
` `<label ... />
` `<bbox ... />
` `<node class="uoi">
`  `<label ... />
`  `<bbox ... />
` `</node>
</node>

Again, there is the flat list + reference to parent alternative. Discussion needed?

What about controlled vocabulary? (the label is actually a prefix + a suffix, they hold conceptual information that may be worth expressing in a more explicit manner? cf. rule \#2)

### Misc

... What about other node decorations? E.g. clone marker? (with its own optional label) Should they be treated in the same way? (= node within a node)

And what about tags?

Example 3 : not just a bipartite graph
--------------------------------------

### Logic Arcs and Nodes

These are not fundamentally different from PN and their arcs.

Hierarchical approach? (rejected)

<node class="and">
` `<arc ref= ... />
` `<arc ref= ... />
</node>

Flat list approach...

<node class="and">` [...] `</node>` // include port description?`
`[...]`
<arc>` [...] `</arc>` // ref to both ends: operator port, and (epn or another operator port)`
<arc>` [...] `</arc>` // ref to both ends: operator port, and (epn or another operator port)`

To be continued
---------------

Open question: a diagram may well contain a number of real EPNs which (apart from their position) will be visually identical to some inner EPNs (inside of a complex). Are we happy with repeating the same visual descriptions in different places? (even when that description is pretty long, e.g. involves a number of state variables, etc.) \[the same question arises when describing, for instance, the same complex in two different compartments... Or a number of clones of the same complex. So far the answer has been: OK to be redundant, No to "factorizing" the description\]