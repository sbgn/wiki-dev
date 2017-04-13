Present: Katja Wegner, Gael Jalowicki, Frank Bergmann, Tobias Czauderna, Martijn van Iersel, Augustin Luna, Falk Schreiber, Huaiyu Mi, Stuart Moodie, Anatoly Sorokin, Akira Funahasi, Yukiko Matsuoka

Java constants
--------------

-   We'd like constants for the possible values of the class attributes in LibSBGN.
-   Martijn proposed to add meta-data to each constant (such as the corresponding SBO term, corresponding SBGN language, etc.). After some discussion it was decided to keep things simple. ACTION - Martijn will write the code for the constants.
-   In the future, we could store meta-data in a way that is independent of the programming language
-   For the future, Frank requested derived classes to be defined that automatically set the correct clazz value - e.g. \`map.addGlyph (new MacroMolecule())\`

Extensions
----------

-   Naming: why are they named <extensions> and not <annotations>, as in SBML? Reason: the term annotations is overloaded, it is also a glyph type.
-   Can code for extensions be added to the repository? We could add them to a new "util" or "contrib" directory (that doesn't exist yet).

End-points of lines
-------------------

-   Falk demonstrated that it is sometimes advantageous to let a line end at the center of a target node instead of at the edge, because otherwise you may see a wedge-shaped gap if the line is very thick and not perpendicular to the glyph. However, this does not address the issue of defining the width of the whitespace gap.
-   Katja proposed an alternative solution where there is a bounding box around the arrowhead and the whitespace gap together.
-   Frank and Martijn re-iterated the current definition of end-points of lines (see red dots in attached diagram)
-   Frank requested a list of which arrowheads should go on the start or the end of each arc to be added to the documentation.

MIRIAM support
--------------

-   MIRIAM can already be supported by putting an RDF block inside <extension> tags.
-   As in SBML, MIRIAM RDF blocks can not / do not have to be on the glyph that they relate to. Therefore, an optional id is necessary, especially on <map>
-   ACTION: Martijn will add an optional meta-ID.

Validation
----------

-   At a different COMBINE session, standardization of validator output will be discussed (NB, this has resulted in the CombineVRL project).
-   Augustin proposed a method for referencing rules, e.g. "sbgn-pd-L1V1.3-3.4\#1". Another solution is to put this in human-readable description.
-   Severity levels: Augustin proposed "error", "warning", "not-implemented" and "untestable". The latter two have a place-holder function, and will not normally be shown by software.
-   Unit-testing validation: Augustin suggested to name test-cases as SBML does: pdXXXXX-pass-N.sbgn and pdXXXXX-fail-N.sbgn. You need both a positive and a negative case, because of dependencies between some rules.

Documentation
-------------

-   Falk offered to help review documentation. Please send around a request for review before the release.
-   When M2 is released, documentation should be more clearly linked from sbgn.org

Bbox on map
-----------

-   It has been requested before to store the drawing canvas. This can be used to define a whitespace margin around the elements on the page. Stuart and Martijn requested this to be a bbox instead of a simple width, height pair. ACTION martijn will implement this.

Release
-------

-   Do in two steps: announce API/XSD freeze before final release, In the intervening period, documentation can be reviewed.
-   Aiming for a release end of October / Halloween.
