**TODO: Outdated, this must be updated to the new github repository**

This tutorial describes in 3 steps how to build the LibSBGN java classes and/or the LibSBGN jar using Eclipse.

Preparation
===========

Add the Java tools to the Ant runtime classpath
-----------------------------------------------

Go to Window -&gt; Preferences -&gt; Ant -&gt; Runtime -&gt; Tab *Classpath*

Add the Java tools to *Global Entries*

-   Click *Add External JARs...*
-   Go to *Path to JDK*/lib/tools.jar

[thumb|c|center|346px|Set the Ant runtime classpath in the Eclipse preferences](/Image:LibSBGN_Ant_Classpath.png "wikilink")

Add the JDK to the system PATH variable (necessary for JavaDoc)
---------------------------------------------------------------

Add

*`Path` `to` `JDK`*`/bin`

to the system PATH variable as described [here](http://www.java.com/en/download/help/path.xml) and [here](http://download.oracle.com/javase/tutorial/essential/environment/paths.html)

Install an Eclipse Subversion plugin
------------------------------------

Install the Subversion plugin [Subversive](http://www.eclipse.org/subversive/) ([installation documentation](http://www.eclipse.org/subversive/documentation/gettingStarted/aboutSubversive/install.php)) **or** [Subclipse](http://subclipse.tigris.org/) ([installation documentation](http://subclipse.tigris.org/servlets/ProjectProcess?pageID=p4wYuA))

Check out LibSBGN from SourceForge
==================================

Open the *SVN Repository Exploring* Perspective

-   Go to Window -&gt; Open Perspective -&gt; SVN Repository Exploring **or**
-   Go to Window -&gt; Open Perspective -&gt; Other ... and choose *SVN Repository Exploring*

Add a new repository location (right click in *SVN Repositories*)

[thumb|c|center|494px|Add a new repository location](/Image:LibSBGN_SVN_Repository_1.png "wikilink")

Enter

[`https://libsbgn.svn.sourceforge.net/svnroot/libsbgn`](https://libsbgn.svn.sourceforge.net/svnroot/libsbgn)

in *URL*

Optionally choose *Use a custom label* and enter a name, e.g. *LibSBGN*

Click *Finish*

[thumb|c|center|494px|Enter the repository location information](/Image:LibSBGN_SVN_Repository_2.png "wikilink")

Right click on *LibSBGN/trunk*

Choose *Check Out*

[thumb|c|center|494px|Check out the trunk from the LibSBGN SVN repository](/Image:LibSBGN_SVN_Repository_3.png "wikilink")

Build the LibSBGN source files, class files, jar file and JavaDoc files
=======================================================================

Switch to the *Java Perspective*

To build the source files, class files and jar file

-   Right click on *build.xml* in project *libsbgn*
-   Choose *Run As* -&gt; *Ant Build*

[thumb|c|center|494px|Build the LibSBGN source files, class files and jar file](/Image:LibSBGN_Build_1.png "wikilink")

To build the source files, class files, jar file and JavaDoc files

-   Right click on *build.xml* in project *libsbgn*
-   Choose *Run As* -&gt; *Ant Build...*

[thumb|c|center|494px|Build the LibSBGN source files, class files, jar file and JavaDoc files](/Image:LibSBGN_Build_2.png "wikilink")

-   Select *doc*
-   Click *Apply* and/or *Run*

[thumb|c|center|494px|Build the LibSBGN source files, class files, jar file and JavaDoc files](/Image:LibSBGN_Build_3.png "wikilink")

In case the build process doesn't start make sure that Ant is using the same JRE as the workspace (see figure above, tab *JRE*).