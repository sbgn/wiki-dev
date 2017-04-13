Concept and Features
--------------------

The way that Schematron is used is that first the rule set is converted into a XML stylesheet (XSL), and then the dataset to be validated is transformed against the stylesheet to produce the validation report (see Basic Usage). A strength of Schematron is its ability to use XPath expressions to select XML instances, therefore a good understanding of XPath is essential (see XPath Links).

### Features

-   Schematron uses assertions (used to detects errors) and reports

(used to report affirmative instances).

-   Schematron supports workflows in which distinct groups of rules are

active; these are known as phases.

-   Schematron supports the reporting of diagnostic information.

Basic Usage
-----------

Here is an example using the Xalan XSLT processor:

`# Xalan SCHEMATRON_SOURCE.sch ./schematron/iso_svrl_for_xslt1.xsl >`
`SCHEMATRON_AS_XSL.xsl`
`# Xalan FILE_TO_BE_VALIDATED.xml SCHEMATRON_AS_XSL.xsl > VALIDATION_REPORT.svrl`

Schematron Tutorials and Tips
-----------------------------

-   [ISO Schematron Tutorial](http://www.dpawson.co.uk/schematron/index.html)
-   [Schematron: validating XML using XSLT](http://www.ldodds.com/papers/schematron_xsltuk.html)
-   [Introduction to Schematron](http://www.mulberrytech.com/papers/schematron-Philly.pdf)
-   [The top three mistakes in Schematron](http://broadcast.oreilly.com/2009/06/the-top-three-mistakes-in-sche.html)

Schematron Documentation
------------------------

-   [Schematron specification](http://www.schematron.com/spec.html)
-   [Schematron Quick Reference](http://www.mulberrytech.com/quickref/schematron1.pdf)

Main Schematron Pages
---------------------

-   [Schematron on Google Code (for downloads)](http://code.google.com/p/schematron/)
-   [Schematron Homepage](http://www.schematron.com/)

Extending Schematron
--------------------

-   [API for ISO Schematron Skeleton](http://www.schematron.com/schematron-skeleton-api.htm)
-   [Probatron4j - Java Schematron implementation uses custom XPath functions coded in Java](http://code.google.com/p/probatron4j/)

XPath Links
-----------

-   [XPath Abbreviated Syntax](http://www.w3.org/TR/xpath/#path-abbrev)
-   [XPath, XQuery, and XSLT Functions](http://www.w3schools.com/Xpath/xpath_functions.asp)
-   [XPath Examples](http://msdn.microsoft.com/en-us/library/ms256086.aspx)
-   [XPath Developer Eclipse Plugin](http://www.bastian-bergerhoff.com/eclipse/features/web/XPathDeveloper/toc.html) An environment to test XPath expressions

Java XSLT Processors
--------------------

-   [Xalan](http://xalan.apache.org)
-   [Saxon](http://saxon.sourceforge.net/)

Navigating Objects using XPath
------------------------------

-   [JXPath: Applies XPath expressions to graphs of objects of all kinds: JavaBeans, Maps, Servlet contexts, DOM, etc.](http://commons.apache.org/jxpath/)
