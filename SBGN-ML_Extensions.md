Extending LibSBGN
=================

The "extension" element can be used by tool developers to attach arbitrary data to any element of SBGN.

XML
---

Here is an example of what an extension looks like in XML:
```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
   <sbgn ns="http://sbgn.org/libsbgn/0.2">
       <map language="process description">
           <extension>
           <renderInformation id="example" programName="SBML Layout" programVersion="3.0"
             ns="http://projects.eml.org/bcb/sbml/render/level2">
               <listOfColorDefinitions>
               <colorDefinition id="yelloComp" value="#ffffccff" />
               ...
               </listOfColorDefinitions>
               ...
           </renderInformation>
           </extension>
           ...
```
-   Complete sample sbgn-ml that uses extensions to store color gradients: http://libsbgn.svn.sourceforge.net/svnroot/libsbgn/trunk/test-files/PD/neuronal_muscle_signalling_color.sbgn
-   For more information about this format see the renderInformation description here: http://sbml.org/Community/Wiki/SBML_Level_3_Proposals/Rendering

Java
----

In order to read the above file it suffices to iterate through the elements like this:
```
            Map map = diagram.getMap();
            Extension ex = map.getExtension();

            // read render info
            if (ex != null && ex.getAny().size() > 0) {
                for (Element element : ex.getAny()) {
                    if (element.getNamespaceURI() == "http://projects.eml.org/bcb/sbml/render/level2") {
                        // found render information

                        // go through color definitions
                        System.out.println("Color definitions:");
                        NodeList colors = element
                                .getElementsByTagName("colorDefinition");
                        for (int i = 0; i < colors.getLength(); i++) {
                            Element current = (Element) colors.item(i);
                            System.out.println("...color: "
                                    + current.getAttribute("id") + " = "
                                    + current.getAttribute("value"));
                        }
                        System.out.println();

                        // go through gradient definitions
                        System.out.println("Gradient definitions:");
                        NodeList gradients = element
                                .getElementsByTagName("linearGradient");
                        for (int i = 0; i < gradients.getLength(); i++) {
                            Element current = (Element) gradients.item(i);
                            System.out.println("...gradient: "
                                    + current.getAttribute("id"));

                            System.out.println("......from: "
                                    + ((Element) current.getChildNodes().item(0))
                                            .getAttribute("stop-color"));
                            System.out.println("......to: "
                                    + ((Element) current.getChildNodes().item(1))
                                            .getAttribute("stop-color"));

                        }
                        System.out.println();

                        // go through styles
                        System.out.println("Styles:");
                        NodeList styles = element.getElementsByTagName("style");
                        for (int i = 0; i < styles.getLength(); i++) {
                            Element current = (Element) styles.item(i);
                            System.out.println("...applies to the following ids: "
                                    + current.getAttribute("idList"));

                            Element group = (Element) current.getChildNodes().item(
                                    0);
                            final String fill = group.getAttribute("fill");
                            if (!fill.isEmpty())
                                System.out.println("......fill: " + fill);
                            System.out.println("......stroke: "
                                    + group.getAttribute("stroke"));
                            System.out.println("......strokeWidth: "
                                    + group.getAttribute("stroke-width"));

                        }
                        System.out.println();
                    }
                }
            }
```

You can attach arbitrary XML to an existing SBGN document, by adding org.w3c.dom.Element's
```
Extension ext = new Extension();
glyph.setExtension(ext);

DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
DocumentBuilder db = dbf.newDocumentBuilder();
Document doc = db.newDocument();

Element elt = doc.createElementNS(NAMESPACE, LOCALNAME);
elt.setPrefix(PREFIX);
elt.setAttribute(name, value);

ext.getAny().add(elt);
```
-   Complete code demo in Java: https://libsbgn.svn.sourceforge.net/svnroot/libsbgn/trunk/org.sbgn/test/org/sbgn/ExtensionDemo.java