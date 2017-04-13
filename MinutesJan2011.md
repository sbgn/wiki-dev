LibSBGN Meeting notes, 24 January 2011

Present: Alex Pico Akira Funahashi Augustin Luna Alice Vileger Frank Bergmann Huaiyu Mi Martijn van Iersel Tobias Czauderna

Documentation
=============

Most documentation tasks have been completed. Alice has created documentation on all elements of SBGN-ML, but hasn't yet managed to format this documentation automatically from the XSD. There was a lot of feedback on documentation. Augustin suggests adding a code example on validation. Frank suggests adding a utility class to hide some of the verbous JAXB bits.

ACTION: Alice will continue work on automated documentation formatting ACTION: Martijn will update the tutorial with a validation example and a Utility class

SBGN-ML
=======

"Map" element
-------------

There was a discussion on whether the "map" element was a good idea or not. Storing multiple diagrams in a single file makes tools more complex, and it's not clear what the advantage is. Frank proposes to keep the map element in, but set the maximum to just a single one. Then we can always decide to allow more maps later in a backwards compatible manner.

ACTION: cardinality of map will be set to one

Terminals
---------

A new glyph class "terminal" is proposed to be used by the tag-like shapes in submaps.

ACTION: terminal will be added to the class enumeration.

Coordinates
-----------

The documentation is vague about the unit used for coordinates. It was resolved that the scale is essentially arbitrary, but the rule of thumb is: 1 unit == 1 pixel.

Font attributes
---------------

The schema still contains font and fontsize attribute, even though it's not used by any of the examples, and graphical properties were assigned to milestone 2. This is still a vestige from the Wittenberg meeting. They haven't been properly thought through.

ACTION fontsize and font will be removed from the spec before the release.

Tool support
============

Martijn has re-installed a new development server, so that the comparison gallery is online again. Frank has managed to get the comparison script running as well. The three tools supporting SBGN-ML are up-to-date, or very nearly so.

C++ bindings: Alice has managed to create C++ bindings. It's a bit tricky to set up because there are all kinds of dependencies. This needs to be documented, and tested on multiple operating systems.

ACTION: Alice will further document the procedure for generating C++ binding.

License
-------

After some discussion on the list, we're getting close to deciding on a software license for LibSBGN. A quick round amongst meeting attendees shows that there is consensus support for LGPL v 2.1 (or higher). To finalize the decision, we need a poll to get community feedback.

ACTION: Martijn will start a poll to get feedback from the community. ACTION: Martijn will check if JAXB puts any restrictions on the license we can use.

Roadmap
=======

There is no reason to postpone the release. We will finish up some loose ends and release on Friday 26th.

After that work will start on ER and AF support. Alice, Tobias and Martijn will work on some of the Milestone 2 items during a face-to-face meeting in Gatersleben from February 7 to 11. Ideally this will lead to proposals that can be finalized at HARMONY in New York.

Next Meeting
============

ACTION: Martijn will schedule next meeting in February, for EU / Australia timezones.

An audio recording of this meeting is available from Martijn upon request.