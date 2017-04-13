Present:

-   Alice Villéger (AV) not during TC, but comments beforehand
-   Tobias Czauderna (TC)
-   Stuart Moodie (SM)
-   Anatoly Sorokin (AS)
-   Falk Schreiber (FS)

SBGN workshop
-------------

-   SM: organisation is going well
-   SM: 18 to 19 people (people which unfortunately cannot make it: Nicolas, Hiroaki Kitano, Emek; some available via skype)

Co-meeting

-   Editor-Meeting: yes, include Alice via skype

Agenda

-   Times are open to discussion
-   Topics are open to discussion

The agenda is yet to be confirmed, but the likely topics it will cover are:

-   Review the latest SBGN specifications
-   Review tool support for SBGN
-   Discuss how to help developers implementing SBGN supporting tools.
-   New language features.
-   The future of SBGN & lessons learned from SBGN Level 1.
-   Start work on SBGN Level 2.

<!-- -->

-   need session chairs
-   presentations (distributed over the days)

Times Monday

-   29.04. 12:00 lunch
-   29.04. 13:00-13:30 opening/welcome (Igor ?), introduction/overview (Stuart), additions to agenda (all), introduction of participants/ice breaker (all)
-   29.04. 13:30-14:30 Status update/where are we with SBGN - PD (Stuart), ER (Anatoly), AF (Falk), libSBGN (Tobias), Web (Alice)
-   29.04. 14:30-15:30 major issues for SBGN development, discussion (all)
-   29.04. 15:30-16:00 coffee & cake
-   29.04. 16:00-18:30 web, community
-   29.04. 20:00 dinner

Tuesday

-   30.04. 08:30-10:00 ER development - what is missing, what do we need to adress, proposals for changes/extensions (all)
-   30.04. 10:00-10:30 morning tea
-   30.04. 10:30-12:30 AF development - what is missing, what do we need to adress, proposals for changes/extensions (all)
-   30.04. 12:30-13:30 lunch
-   30.04. 13:30-15:30 PD development - what is missing, what do we need to adress, proposals for changes/extensions (all)
-   30.04. 15:30-16:00 coffee & cake
-   30.04. 16:00-18:30 PD L1V2 (all)
-   30.04. 20:00 dinner

Wednesday

-   01.05. 08:30-10:00 The future of SBGN & lessons learned from SBGN Level 1.
-   01.05. 10:00-10:30 morning tea
-   01.05. 10:30-12:30 Proposal - what should SBGN L2 look like
-   01.05. 12:30-13:30 lunch
-   01.05. 13:30-15:30 structured discussion based on ideas of morning sessions
-   01.05. 15:30-16:00 coffee & cake
-   01.05. 16:00-18:00 structured discussion based on ideas of morning session
-   01.05. 19:30 dinner (restaurant)

Thursday

-   02.05. 08:30-10:00 libSBGN, tools for SBGN
-   02.05. 10:00-10:30 morning tea
-   02.05. 10:30-12:00
-   02.05. 12:00-12:30 conclusions from discussions, closing remarks
-   02.05. 12:30 lunch

One day online / skype meeting
------------------------------

last meeting

-   SM: worked well, able to do a lot
-   TC: not so many discussions / interactions
-   SM: partly discussions with two/three editors, useful
-   should be repeated, but if possible it should be a day where everybody can participate
-   see who would be available this weekend

SBGN Web
--------

-   Access rights
-   AV: I've tried to install a version locally on my machine, but have been bumping into some still-unresolved issues. I suspect it's because it's an old version of Mediawiki, resulting in some incompatibilities with the more recent versions of PHP and MySQL running on my machine... I guess I should ask Nicolas Rodriguez what the exact configuration is on the actual server, in order to replicate it as closely as possible at home (maybe on a virtual machine?). Work in progress... When this is fixed, I can start working on the "skin" of the website so that we can alter things like the top menu, the layout, the background, etc (this editing job should be relatively easy once I get the bloody thing actually running). I know it's a bit frustrating to have to wait till then, but in the long run, I think it will be very useful to have a (well-documented, after I've done my homework!) self-contained test version of the website running locally (much safer way to roll out changes than tinkering directly with the live version!)
-   Web server: could the web space on sourceforge be used?

Tool overview
-------------

-   moved to next meeting

T-shirt
-------

-   AV: It's going to be pretty difficult to get an accurate quote without a precise design. Depending on the printing method used, parameters like "number of colours" can increase prices greatly. For instance with the first supplier I looked at, total cost for 30 t-shirts would vary between £200 and £1000 pounds depending on that single factor. Another one would oscillate between £600 and £1000 depending on the \*complexity\* of the design. These are just examples. But it means I can't really shop around until the design of the t-shirt is really established. Regarding the design, I haven't done anything more since my first drafts.Current stumbling blocks:
-   1) the actual pathway needs proof-reading by someone who actually understands systems biology. I did a crude translation job into SBGN PD from KEGG: <http://www.genome.jp/kegg/pathway/map/map00232.html> ... But I have no idea what is a macromolecule, a small chemical, etc. It would be very useful if someone else could look at that pathway, and write it down, say, as an excel file with a tab for EPNs (first column: name, second column: precise type, e.g. "macromolecule") and maybe also a tab for PNs (first column: EC number - or list of participants if no number -, second column: precise type, e.g. "association"...), and if need be a tab for edges as well (if their role is not self-evident)
-   2) finding a free drawing of a coffee cup, on which the pathway could be laid out
-   3) redrawing the actual thing "nicely". One way to streamline the process would be to write a quick script that automatically translates a simple text description of parts of the pathway (e.g. tabulated list of EPNs with type, see above) into SVG (arbitrary layout, just to get a consistent style in term of the nodes rendering). Then the nodes can be laid out by hand over the coffee cup drawing. Then the really difficult bit is going to be drawing all the curvy edges. Again, some ad-hoc script could help... (it's soooo tedious to do it all by hand... And often quite ugly still!) Like some code that takes a few control points and generates the corresponding curve as SVG (again, with consistent styling re: colour, thickness, etc.). This is more difficult than generating the nodes, but I've got some code in Arcadia that may do the trick (I would still need to extract it)

<!-- -->

-   AV: I could work on \#2 and \#3 (still, if someone has other suggestions for these tasks, feel free to help!), but I really need someone else to do \#1. The big question being whether this can still be achieved before the meeting :/ ... At some point (and not at the last minute), we should also try to get at least \*some\* sizing information from the participants. Niceties like custom colours and lady-fit could wait till a future iteration of the t-shirt, but size will really be needed to place an actual order.

<!-- -->

-   Tobias will contact Alice and Anatoly

SBGN contest
------------

-   Diagram test during SBGN meeting? -&gt; to be discussed during TC
-   moved to next meeting

review SBGN@Sourceforge
-----------------------

-   [<http://sourceforge.net/projects/sbgn/>](http://sourceforge.net/projects/sbgn/)
-   [files - seems to be not up-to-date](http://sourceforge.net/projects/sbgn/files/)
-   Problem - used Nature Preceedings, which is not longer working for new versions
-   Stuart will download latest version from Nature Preceedings and upload it to sourceforge
-   SM: we have to discuss how to proceed in the future (COMBINE?)
-   [a Wiki in the new Sourceforge style](http://sourceforge.net/p/sbgn/wiki/Home/)
-   [mailing lists](http://sourceforge.net/p/sbgn/mailman/)
-   [hosted apps](http://sourceforge.net/p/sbgn/_list/hosted_apps)
    -   [Mantis bugtracker](http://sourceforge.net/apps/mantisbt/sbgn/my_view_page.php)
    -   [MediaWiki](http://sourceforge.net/apps/mediawiki/sbgn/index.php?title=Main_Page)
    -   [Piwik web analytics](http://sourceforge.net/apps/piwik/sbgn/)
    -   [url shortener](http://sourceforge.net/apps/sfurl/sbgn/)
-   moved to next meeting

next TC
-------

-   7:00pm UK
-   8:00pm Germany
-   10:00pm Russia

<!-- -->

-   Falk will send email / doodle
