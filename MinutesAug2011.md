Present: Augustin, Tobias, Alice, Frank, Martijn

SBGN-ML Varia
-------------

-   The compartmentOrder feature is implemented by Tobias and tested by Martijn. Martijn will check in some test files to demonstrate the feature (ACTION).

<!-- -->

-   Frank notes that some curved arcs of AF examples are not yet described in XML, most notably the two_edges_between_two_activities test-case. This will have to be updated.

<!-- -->

-   Documentation should be updated when Milestone 2 comes out. We agree to keep one version of the documentation, highlighting differences between versions where necessary (e.g.: "this feature is available since M2"). We will not copy the documentation for each Milestone.

End-points of arcs
------------------

-   End-points of arcs: Tobias asked for input from the SBGN editors. However, we decided that this is a tool issue (even if the specs could be clarified). So we'll move ahead with implementation without the SBGN editors.

<!-- -->

-   Frank made a proposal for implementation (Martijn will send around a diagram for clarification)

Extensions
----------

-   What is the difference between Notes and Extensions? Notes contain documentation in XHTML format, all tools are supposed to know more or less how to display notes. Extensions can be tool-specific, and a tool is not necessarily expected to understand every Extension.

<!-- -->

-   We started an extension documentation page. There is currently documentation on reading, writing extensions in Java, as well as some XML examples. Alice will add information about when extensions are appropriate (ACTION)

Tool support
------------

-   Frank and Martijn have updated their tools recently.
-   Tobias will not have time to update before COMBINE
-   Alice added M1 support in Arcadia. This will be officially released (ACTION).
-   Martijn created and checked in an M1 to M2 converter to ease the support of old documents.

Validation
----------

-   Augustin has worked with a summer student on a plug-in for PathVisio that makes use of the schematron rules for validation.
-   Martijn will add a utility function for schematron validation to LibSBGN (ACTION). This utility function will be independent of PathVisio.

Paper
-----

-   The paper should be written as though M2 has been released, otherwise the paper will be out of date by the time of publication.
-   There is a reasonable expectation that most tools will be updated to M2 soon, there is no reason to hold out for that.
-   Alice will send around an updated version by Friday (ACTION)

COMBINE
-------

-   Augustin will present schematron validation in PathVisio at COMBINE.
-   Martijn and Tobias will present LibSBGN (both format and lib) together at COMBINE.
-   Martijn will update poster based on feedback from Falk and Tobias, and send it around for review (ACTION)

Next meeting
------------

We'll try to organize a meeting during a break-out session at COMBINE. The next online meeting will be most likely in October.