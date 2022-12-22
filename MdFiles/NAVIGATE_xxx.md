




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Symbolic Value : Views**



**NAVIGATE\_xxx** **-** How
NIFReadEntries steps through a collection.


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      NAVIGATE\_CURRENT         -  Remain at current position
(reset position & return data).  

  

      NAVIGATE\_PARENT            -  Up 1 level.  

  

      NAVIGATE\_CHILD   -  Down 1 level to first child.  

  

      NAVIGATE\_FIRST\_PEER     -  First node at our level.  

  

      NAVIGATE\_LAST\_PEER      -  Last node at our level.  

  

      NAVIGATE\_CURRENT\_MAIN           -  Highest level non-category entry.  

  

      NAVIGATE\_ALL\_DESCENDANTS    -  NEXT, but only descendants below
NIFReadEntries() - StartPos.  

  

      NAVIGATE\_CURRENT\_HIT             -  Remain at current position in hit's
relevance rank array (in the order of the hit's relevance ranking).  

  

      NAVIGATE\_MASK    -  Navigator code mask.  

  

      NAVIGATE\_MINLEVEL         -  Honor "Minlevel" field in
position. This flag which can be used with any other navigate flag. It causes
the navigation to be limited to entries at a specific level (specified by the
field "MinLevel" in the collection position) or any higher levels but
never a level lower than the "MinLevel" level. Note that level 0
means the top level of the index, so the term "minimum level" really
means the "topmost level" the navigation can move to. This can be
used to find all entries below a specific position in the index, limiting
yourself only to that subindex, and yet be able to use any of the navigators to
move around within that subindex. If this flag is not specified, it defaults to
level 0, meaning that all levels up to and including the topmost level in the collection
will be included in the navigation.  

  

      NAVIGATE\_MAXLEVEL        -  Honor "Maxlevel" field in position.
This flag which can be used with any other navigate flag. It causes the
navigation to be limited to entries at a specific level (specified by the field
"MaxLevel" in the collection position) or any lower levels but never
a level higher than the "MaxLevel" level. In other words, the
MaxLevel field specifies the "bottommost level" that the navigation
can move to. If this flag is not specified, it defaults to (MAXTUMBLERLEVELS
-1), meaning that all levels down to and including the bottommost level in the
collection will be included in the navigation.  

  

      NAVIGATE\_CONTINUE        -  This flag can be combined with any navigation
directive to prevent having a navigation (Skip) failure abort the (ReadEntries)
operation. For example, this is used by the Notes user interface when getting
the entries to display in the view, so that if an attempt is made to skip past
either end of the index (e.g. using PageUp/PageDown), the skip will be left at
the end of the index, and the return will return whatever can be returned using
the separate return navigator.  

  

This flag is also used to get the "last" N entries of a view by
setting the Skip Navigator to NAVIGATE\_NEXT | NAVIGATE\_CONTINUE, setting the
SkipCount to MAXDWORD, setting the ReturnNavigator to NAVIGATE\_PREV\_EXPANDED,
and setting the ReturnCount to N (N must be greater than 0).  

  




**Description :**



These flags
control how NIFReadEntries steps through a collection. The flags are used to
control both the order in which NIFReadEntries skips notes in a collection
before reading any notes, and navigates the collection while it is being read.


 


The minlevel
and/or maxlevel navigation criteria will be used if the NAVIGATE\_MINLEVEL and/or
NAVIGATE\_MAXLEVEL navigation flags are set in **either** the SkipNavigator
or ReturnNavigator parameters to NIFReadEntries.  Regardless of which parameter
these flags are set in, if the flags are set in either one of these parameters
the flags will affect the collection levels that are used in **both** skip
navigation and return navigation of the collection.


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





