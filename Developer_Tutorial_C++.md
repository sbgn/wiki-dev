DISCLAIMER: WORK IN PROGRESS
============================

The system was successfully built and tested on MacOSX Snow Leopard.

TODO
----

-   streamline the automatic building process for all supported systems
-   package the resulting files as a standalone library

Where to find LibSBGN C++?
==========================

LibSBGN C++ can be found in the [SVN repository](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/cpp_binding/).

To download the latest version on your machine:

`svn co `[`https://libsbgn.svn.sourceforge.net/svnroot/libsbgn`](https://libsbgn.svn.sourceforge.net/svnroot/libsbgn)` libsbgn`

What's in the LibSBGN C++ folder?
=================================

SBGN C++ binder
---------------

**sbgn.cxx** and **sbgn.hxx** \[FOR REFERENCE ONLY, MAY NOT BE UP-TO-DATE\]

-   automatically generated from the [SBGN-ML schema](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/resources/SBGN.xsd)
-   using the [following tool](http://www.codesynthesis.com/products/xsd)

This library can read and write SBGN-ML files, and validate their syntax against the schema.

Example of code using the binder
--------------------------------

**sbgn2txt.cxx**

-   in = some \*.sbgn files
-   out = a text description (or validation errors, if any)

Tools required to generate the binder
-------------------------------------

**makefile** \[included\], and a local installation of the XSD converter \[NOT INCLUDED\]

-   "make libsbgn" generates **sbgn.cxx** and **sbgn.hxx** from the current XSD
-   "make test" compiles and runs **sbgn2txt** on all \*.sbgn files in the [test-files folder](http://libsbgn.svn.sourceforge.net/viewvc/libsbgn/trunk/test-files/)

How to (re)build the binder?
============================

**sbgn.hxx** and **sbgn.cxx** are generated automatically from **SBGN.xsd**.

To stay up-to-date with the latest specifications, these files should be rebuilt whenever the XSD is modified.

==Download the XSD =&gt; C++ conversion tool==

-   Download the correct version of the [conversion tool](http://www.codesynthesis.com/products/xsd/download.xhtml) for your platform
-   Uncompress the downloaded file in the current directory.

We'll call the resulting directory *XSD2CPP* in the following instructions.

Test the conversion tool
------------------------

Make sure the conversion tool works properly on your system:

`cd `*`XSD2CPP`*`/examples/cxx/tree/hello`
`make`

If not, consult the tool's documentation to fix the problem (cf. *XSD2CPP*/documentation)

Build LibSBGN C++
-----------------

-   Modify the first line of the makefile to link to the correct root directory:

`root := ./`*`XSD2CPP`*`/examples`

-   To update the binder against the latest version of the XSD, and run tests against all the test files:

`make`

How to reuse the binder?
========================

In order to reuse **sbgn.hxx** and **sbgn.cxx** in your own project, you need to be able to link to a copy of **libxsd** (cf. *XSD2CPP*/libxsd)

For building and linking options (dependencies, system specific settings, etc.), have a look at *XSD2CPP*/examples/build

Refer to **sbgn2txt.cxx** for examples of how to invoke the library in your own code, e.g.:

Read an SBGN-ML file
--------------------

`try`
`{`
` xml_schema::properties props; // to store information on the XSD for validation purposes`
` props.schema_location ("`[`http://sbgn.org/libsbgn/pd/0.1`](http://sbgn.org/libsbgn/pd/0.1)`", "../resources/SBGN.xsd");`
` `
` auto_ptr`<libsbgn::pd_0_1::sbgn>` mysbgnobject ( libsbgn::pd_0_1::sbgn_ (`*`sbgnmlfile`*`, 0, props) );`
` // [..] do something with mysbgnobject`
`}`
`// validation errors result in an exception being thrown`
`catch (const xml_schema::exception& e)`
`{`
` cerr `<< "SBGN-ML parsing error: " << e << endl;
 }

==Traverse the SBGN-ML structure==
 // For each map
 for (libsbgn::pd_0_1::sbgn::map_const_iterator m (mysbgnobject->`map ().begin ()); m != s->map ().end (); ++m)`
`{`
` cout `<< "Map" << endl;

  // For each high level glyph
  for (libsbgn::pd_0_1::map::glyph_const_iterator g (m->`glyph ().begin ()); g != m->glyph ().end (); ++g)`
` {`
`  cout `<< "\tGlyph " << g.id() << " (" << g.class_() << ")" << endl;
   // process glyph internal attributes and elements: label, subglyphs, etc.
  }

  // For each arc
  for (libsbgn::pd_0_1::map::arc_const_iterator a (m->`arc ().begin ()); a != m->arc ().end (); ++a)`
` {`
`   cout `<< "\tArc from " << a->`source() `<< " to " << a->`target() `<< " (" << a->`class_() << ")" << endl;`
`   // process arc internal attributes and elements: geometric path, stoichiometry, etc.`
` }`
`}`