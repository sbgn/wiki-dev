# SBGN-ML (XML Exchange Format)
The XML implementation of SBGN is known as SBGN-ML.

The current version (namespace **http://sbgn.org/libsbgn/0.2**) covers all three languages (PD, ER and AF). Please refer also to the documentation that is auto-generated from the XSD: <http://libsbgn.sourceforge.net/sbgn.doc/>

Namespaces
==========

The XML namespace is used to distinguish versions of SBGN-ML. All element of Milestone 1 SBGN-ML have namespace **http://sbgn.org/libsbgn/pd/0.1** All element of Milestone 2 SBGN-ML have namespace **http://sbgn.org/libsbgn/0.2**. The namespace only goes for elements; attributes are in default (=undefined) namespace.

Common types and elements
=========================

Notes
-----

Version: available from SBGN-ML milestone 2.

The [notes](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/complexType/SBGNBase.notes.html) element can be used to add information about a SBGN map.

Extension
---------

Version: available from SBGN-ML milestone 2.

The [extension](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/complexType/SBGNBase.extension.html) element can be used by tool developers as a generic extension mechanism. See [SBGN-ML Extensions](/LibSBGN/SBGN-ML_Extensions "wikilink") for details

PointAttributes attribute group
-------------------------------

The [PointAttributes](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/attributeGroup/PointAttributes.html) attribute group describes absolute 2D Cartesian coordinates:

-   **x** (float) : horizontal, from left to right
-   **y** (float) : vertical, from top to bottom

The origin is located in the top-left corner of the map.

There is no unit: proportions must be preserved, but the maps can be drawn at any scale. In the test files examples, to obtain a drawing similar to the reference \*.png file, values in the corresponding \*.sbgn file should be read as pixels.

point element
-------------

The [point](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/point.html) element is characterized by **PointAttributes**.

bbox element
------------

The [bbox](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/bbox.html) element describes a rectangle:

-   **PointAttributes** correspond to the 2D coordinates of the top left corner
-   **width** and **height** attributes (both float) refer to the dimensions of the rectangle

The rectangle corresponds to the outer bounding box of a shape. The shape itself can be irregular (for instance in the case of some compartments)

In the case of process nodes, the bounding box only concerns the central glyph (square, or circle), the input/output ports are not included, and neither are the lines connecting them to the central glyph.

A **bbox** is required for all **glyph** elements, and is optional for **label** elements.

label element
-------------

The [label](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/label.html) element describes the text accompanying a glyph:

-   the **text** attribute (string) is mandatory.
-   its position can be specified by a **bbox** (optional)

Tools are free to display the text in any style (font, font-size, etc.)

### bbox of a label

The **bbox** element of a **label** is optional. When no **bbox** is defined, the **bbox** of the parent glyph is inherited. The **label** should be drawn centered horizontally and vertically in the **bbox**.

When the **bbox** is inherited, the **label** may spill outside (just like it can spill outside its parent **glyph**)

An explicit **bbox** provides a stronger hint regarding what surface the **label** should cover. It defines an upper boundary outside of which the **label** should (ideally) not spill. It also represents a preferred size: the surface covered by the **label** can be smaller, but should ideally be as close as possible to the **bbox**.

In most **glyph** classes (EPNs, unit of information, etc.), the **label** is supposed to be centered, so the **bbox** is usually omitted (unless there's a specific hint to be shared concerning the area the **label** should ideally cover)

However, the **label** of a **compartment** or a **complex** can be drawn anywhere inside the **glyph**, so these should preferably have an explicit **bbox**.

### text of a label

The **text** element is a simple string. Multi-line labels are allowed. Line breaks are encoded as `&#xA;` as specified by the XML standard.

High level elements
===================

sbgn element \[root\]
---------------------

The [sbgn](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/sbgn.html) element is the root of any SBGN-ML document. In the current version, it contains one (and only one) **map** element.

map element
-----------

The [map](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/map.html) element describes a single SBGN map.

It contains a list of **glyph** elements, a list of **arc** elements, and a list of **arcgroup** elements. These lists can be of any size (possibly empty).

### bbox element of a map

The **bbox** element on a **map** is not mandatory, it allows the application to define a canvas, and at the same time to define a whitespace margin around the glyphs.

If a bbox is defined on a map, all glyphs, arcs, and arcgroups must be inside this bbox, otherwise they could be clipped off by applications.

### language attribute of a map

The **language** attribute of a **map** is always required.

The attribute can take one of the following values:

-   process description
-   entity relationship
-   activity flow

glyph element
=============

The [glyph](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/glyph.html) element is:

-   either a stand-alone, high-level SBGN node (an EPN, PN, compartment, etc.)
-   or a sub-node (state variable, unit of information, inside of a complex, etc.)

In the first case, it appears directly in the **glyph** list of the map.

In the second case, it is a child of another **glyph** element.

label or state of a glyph
-------------------------

The text inside a **glyph** is described: - either by a [label](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/label.html) element (optional) \[process nodes can't have one\] - or by a [state](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/glyph.state.html) element (optional) \[for state variables only\]

### state of a glyph

The **state** element should only be used for state variables. It replaces the **label** element used for other glyphs. It describes the text to be drawn inside the state variable.

#### value of a state

The **value** attribute (string) represents the state of the variable. It can be:

-   either from a predefined set of string (P, S, etc.) which correspond to specific SBO terms (cf. SBGN specs)
-   or any arbitrary string

#### variable of a state

The **variable** attribute (string) describes the site where the modification described by the value attribute occurs. It is:

-   optional when there is only one state variable on the parent EPN
-   required when there is more than one state variable on the parent EPN

clone element of a glyph
------------------------

The [clone](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/glyph.clone.html) element is optional. It means the glyph carries a clone marker. It can contain an optional **label**.

callout of a glyph
------------------

Callouts are used in the case of glyphs with class annotation. The callout is always optional, it can be used to show which element the callout points to.

bbox element of a glyph
-----------------------

The **bbox** element is mandatory and unique: exactly one per **glyph**.

It defines the outer bounding box of the glyph. The actual shape of the glyph can be irregular (for instance in the case of some compartments)

In the case of process nodes, the bounding box only concerns the central glyph (square, or circle), the input/output ports are not included, and neither are the lines connecting them to the central glyph.

glyph elements inside a glyph
-----------------------------

A **glyph** element can contain any number of children **glyph** elements.

In practice, this should only happen in the following cases:

-   a compartment with unit of information children
-   an EPN with states variables and/or unit of information children
-   a complex, with state variables, unit of info, and/or EPN children

entity of a glyph
-----------------

An **entity** is only used in Activity Flow diagrams. It should be placed on a subglyph of an activity glyph, and is used to indicate the entity that performs the activity.

port elements of a glyph
------------------------

A **glyph** element contain an unbounded, potentially empty list of **port** elements.

A **port** element describes an anchor point, which **arc** elements can refer to as a **source** or **target**. It consists in:

-   absolute 2D cartesian coordinates (**PointAttribute**)
-   a unique **id** attribute

Two **port** elements are required for process nodes. They represent the extremity of the two "arms" which protrude on both sides of the core of the **glyph** (= square or circle shape).

Other glyphs don't need ports (but can use them if desired).

### id of a port

The **id** attribute (xsd:ID) of a **port** can be referred to as a **source** or **target** by **arc** elements.

The xsd:ID type is an alphanumeric identifier, starting with a letter.

Port IDs often contain the ID of their glyph, followed by a local port number (e.g. glyph4.1, glyph4.2, etc.)

However, this style convention is not mandatory, and IDs should never be interpreted as carrying any meaning.

class of a glyph
----------------

The **class** attribute (string) defines the semantic of the **glyph** element, and influences:

-   the way that glyph should be rendered
-   the overall syntactic validity of the map

The various classes encompass the following SBGN elements:

-   Entity Pool Node classes (PD only)
    -   *unspecified entity*
    -   *simple chemical*
    -   *macromolecule*
    -   *nucleic acid feature*
    -   *source and sink*
    -   *complex*
    -   *simple chemical multimer*
    -   *macromolecule multimer*
    -   *nucleic acid feature multimer*
    -   *complex multimer*
-   Process Node classes (PD only)
    -   *process*
    -   *omitted process*
    -   *uncertain process*
    -   *association*
    -   *dissociation*
-   Entity Node classes (ER only)
    -   *entity*
    -   *outcome*
-   Other Node classes (ER only)
    -   *interaction*
    -   *influence target*
    -   *variable value*
    -   *implicit xor*
    -   *annotation*
-   Activity Node classes (AF only)
    -   *biological activity*
    -   *perturbation*
-   Other Node classes (both PD and ER)
    -   *perturbing agent*
-   Other Node classes (both PD and AF)
    -   *compartment*
    -   *submap*
    -   *tag*
    -   *terminal*
-   Logical Operator classes (PD, ER, and AF)
    -   *and*
    -   *or*
    -   *not*
-   Logical Operator classes (both ER and AF)
    -   *delay*
-   Other Node classes (PD, ER, and AF)
    -   ''phenotype
-   Subglyph on glyph classes (both PD and ER)
    -   *state variable*
    -   *unit of information*
-   Subglyph on glyph classes (ER only)
    -   *existence*
    -   *location*

Arc classes are defined in a separate enumeration.

When left empty, the default value of this attribute is "unspecified entity"

orientation of a glyph
----------------------

The **orientation** attribute is used to express how to draw asymmetric glyphs.

The **orientation** of Process Nodes is either "horizontal" or "vertical". It refers to an (imaginary) line connecting the two in/out sides of the PN.

The **orientation** of Tags can be "left", "right", "up" or "down". It refers to the direction the arrow side of the glyph is pointing at.

id of a glyph
-------------

The **id** attribute (xsd:ID) of a **glyph** can be referred to as a **source** or **target** by **arc** elements.

The xsd:ID type is an alphanumeric identifier, starting with a letter.

It is recommended to generate meaningless IDs (e.g. "glyph1234") and avoid IDs with a meaning (e.g. "epn_ethanol")

compartmentRef of a glyph
-------------------------

**compartmentRef** is a reference to the ID of the compartment that this glyph is part of. Only use this if there is at least one explicit compartment present in the diagram. Compartments are only used in PD and AF, and thus this attribute as well. For PD, this should be used only for EPN's.

In case there are no compartments, entities that can have a location, such as EPN's, are implicit member of an invisible compartment that encompasses the whole map. In that case, this attribute must be omitted.

compartmentOrder of a compartment
---------------------------------

The **compartmentOrder** attribute can be used to define a drawing order for compartments. It enables tools to draw compartments in the correct order especially in the case of overlapping compartments. Compartments are only used in PD and AF, and thus this attribute as well.

The attribute is of type float, the attribute value has not to be unique. Compartments with higher **compartmentOrder** are drawn on top. The attribute is optional and should only be used for compartments.

arc element
===========

The [arc](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/arc.html) element describes an SBGN arc between two SBGN nodes. It contains:

-   For **PD**: an optional stoichiometry marker,
-   For **ER**: an optional cardinality marker, zero or more ports (influence targets), and zero or more outcomes,
-   a mandatory **source** and **target** (**glyph** or **port**),
-   a geometric description of its whole path, from **start** to **end**. This path can involve any number of straight lines or quadratic/cubic Bezier curves.

class attribute of an arc
-------------------------

The **class** attribute (string) defines the semantic of the **arc**, and influences:

-   the way that arc should be rendered
-   the overall syntactic validity of the map

The various classes encompass all possible types of SBGN arcs:

-   For **PD** only
    -   *production*
    -   *consumption*
    -   *catalysis*
-   For **ER** only
    -   *assignment*
    -   *interaction*
    -   *absolute stimulation*
    -   *absolute inhibition*
-   For **AF** only
    -   *positive influence*
    -   *negative influence*
    -   *unknown influence*
-   For **PD and ER**
    -   *modulation*
    -   *stimulation*
    -   *inhibition*
-   For **PD and AF**
    -   *equivalence arc*
-   For **PD, ER, and AF**
    -   *necessary stimulation*
    -   *logic arc*

id of an arc
------------

The **id** attribute (xsd:ID) of an **arc** can be used for reference.

The xsd:ID type is an alphanumeric identifier, starting with a letter.

It is recommended to generate meaningless IDs (e.g. "arc1234") and avoid IDs with a meaning.

glyph element of an arc
-----------------------

An arc can contain a single optional child **glyph**. This **glyph** must be of **class** *stoichiometry* (a square with a numeric label)

In PD, an arc can contain a single optional **sub-glyph**. This **glyph** must be of **class** *stoichiometry* (a square with a numeric label).

In ER, an arc can contain several **sub-glyphs**. This can be zero or one **glyph** of class *cardinality* (e.g. *cis* or *trans*), plus zero to many **glyphs** of class *outcome* (black dot).

port elements of an arc
-----------------------

**Port** elements of **arcs** are only allowed in **ER**.

An **arc** element contains an unbounded, potentially empty list of **port** elements.

A **port** element describes an anchor point, which **arc** elements can refer to as a **target**. It consists of:

-   absolute 2D cartesian coordinates (**PointAttribute**),
-   a unique **id** attribute.

### id of a port

The **id** attribute (xsd:ID) of a **port** can be referred to as a **target** by an **arc** element.

The xsd:ID type is an alphanumeric identifier, starting with a letter.

Port IDs often contain the ID of their arc, followed by a local port number (e.g. arc4.1, arc4.2, etc.)

However, this style convention is not mandatory, and IDs should never be interpreted as carrying any meaning.

start element of an arc
-----------------------

The **start** element (characterized by **PointAttributes**) represents the starting point of the **arc**'s path. It is unique and mandatory.

list of next elements of an arc
-------------------------------

A **next** element represents the next point (cf. **PointAttributes**) in the arc's path.

Between the **start** and the **end** of the path, there can be any number (even zero) of **next** elements (intermediate points). They are read consecutively: **start**, **next**, **next**, ..., **next**, **end**.

When the path from the previous point to this point is not straight, this element also contains a list of control points (between 1 and 2) describing a Bezier curve (quadratic if 1 control point, cubic if 2) between the previous point and this point.

### list of point elements of a next element

This list of control points (**point** elements) is only used when the path describes a curve.

The number of **point** elements describes the degree of the Bezier curve:

-   linear (0, empty list)
-   quadratic (1 **point** element)
-   cubic (2 **point** elements)

end element of an arc
---------------------

The **end** element represents the ending point (cf. **PointAttributes**) of the **arc**'s path. It is unique and mandatory.

When the path from the previous point to this point is not straight, this element also contains a list of control points (between 1 and 2) describing a Bezier curve (quadratic if 1 control point, cubic if 2) between the previous point and this point.

### list of point elements of an end element

This list of control points (**point** elements) is only used when the path describes a curve.

The number of **point** elements describes the degree of the Bezier curve:

-   linear (0, empty list)
-   quadratic (1 **point** element)
-   cubic (2 **point** elements)

source attribute of an arc
--------------------------

The **source** attribute (xsd:IDREF) is always required. It can refer:

-   either to the **id** of a **glyph**
-   or to the **id** of a **port** on a **glyph**

target attribute of an arc
--------------------------

The **target** attribute (xsd:IDREF) is always required. It can refer:

-   either to the **id** of a **glyph**
-   or to the **id** of a **port** on a **glyph**

arcgroup element
================

The [arcgroup](http://libsbgn.sourceforge.net/sbgn.doc/http___sbgn.org_libsbgn_0.2/element/arcgroup.html) describes a set of **arcs** and **glyphs** that have a relation together, for example in **ER** **arcs** of class *interaction* around a **glyph** of class *interaction*.

Note that, in spite of the name, an **arcgroup** contains both **arcs** and **glyphs**.

class attribute of an arcgroup
------------------------------

The class attribute defines the semantic of the arcgroup.

Currently, there is only one value defined:

-   For **ER** only
    -   *interaction*

glyph element of an arcgroup
----------------------------

An **arcgroup** can contain **glyphs**. For example, in an **arcgroup** of class *interaction*, there must be one **glyph** of class *interaction*.

arc element of an arcgroup
--------------------------

An **arcgroup** can have multiple **arcs**. They are all assumed to form a single hyperarc-like structure.

(Pre)History
============

For an older version of this page, see [Exchange Format (as discussed around SBGN5.5)](/LibSBGN/Exchange_Format_(as_discussed_around_SBGN5.5) "wikilink")