




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



**NAVIGATE\_xxx [PREVxxx]** **-** How
NIFReadEntries steps through a collection.


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      NAVIGATE\_PREV    -  Previous entry over entire tree
(opposite order of PREORDER).  

  

      NAVIGATE\_PREV\_PEER     -  Previous node at our level.  

  

      NAVIGATE\_PREV\_MAIN      -  CURRENT\_MAIN, then PREV\_PEER only if already
there.  

  

      NAVIGATE\_PREV\_PARENT             -  PARENT, then PREV\_PEER.  

  

      NAVIGATE\_PREV\_UNREAD            -  PREV, but only "unread"
entries.  

  

      NAVIGATE\_PREV\_UNREAD\_MAIN   -  Previous unread main.  

  

      NAVIGATE\_PREV\_SELECTED         -  PREV, but only "selected"
entries.  

  

      NAVIGATE\_PREV\_SELECTED\_MAIN           -  Previous selected main.  

  

      NAVIGATE\_PREV\_EXPANDED        -  PREV, but only "expanded"
entries.  

  

      NAVIGATE\_PREV\_EXPANDED\_UNREAD    -  PREV, but only "expanded"
AND "unread" entries.  

  

      NAVIGATE\_PREV\_EXPANDED\_SELECTED             -  PREV, but only
"expanded" AND "selected" entries.  

  

      NAVIGATE\_PREV\_EXPANDED\_CATEGORY            -  PREV, but only
"expanded" AND "category" entries.  

  

      NAVIGATE\_PREV\_EXP\_NONCATEGORY    -  PREV, but only "expanded"
"non-category" entries.  

  

      NAVIGATE\_PREV\_HIT         -  PREV, but only FTSearch "hit"
entries (in the SAME ORDER as the hit's relevance ranking).  

  

      NAVIGATE\_PREV\_SELECTED\_HIT             -  PREV, but only
"selected" and FTSearch "hit" entries (in the SAME ORDER as
the hit's relevance ranking).  

  

      NAVIGATE\_PREV\_UNREAD\_HIT     -  PREV, but only "unread" and
FTSearch "hit" entries (in the SAME ORDER as the hit's relevance
ranking).  

  

      NAVIGATE\_PREV\_CATEGORY        -  PREV, but only "category"
entries.  

  

      NAVIGATE\_PREV\_NONCATEGORY            -  PREV, but only
"non-category" entries.  

  




**Description :**



These flags
control how NIFReadEntries steps through a collection. The flags are used to
control both the order in which NIFReadEntries: skips notes in a collection
before reading any notes, and navigates the collection while it is being read.


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





