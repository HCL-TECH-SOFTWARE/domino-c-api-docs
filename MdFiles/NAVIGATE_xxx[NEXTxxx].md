




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



**NAVIGATE\_xxx [NEXTxxx]** **-** How
NIFReadEntries steps through a collection.


**----------------------------------------------------------------------------------------------------------**



**#include <nif.h>**


 **Symbolic Values :**      NAVIGATE\_NEXT    -  Next entry over entire tree (parent
first, then children,...).  

  

      NAVIGATE\_NEXT\_PEER     -  Next node at our level.  

  

      NAVIGATE\_NEXT\_MAIN      -  CURRENT\_MAIN, then NEXT\_PEER.  

  

      NAVIGATE\_NEXT\_PARENT             -  PARENT, then NEXT\_PEER.  

  

      NAVIGATE\_NEXT\_UNREAD            -  NEXT, but only "unread"
entries.  

  

      NAVIGATE\_NEXT\_UNREAD\_MAIN   -  NEXT\_UNREAD, but stop at main note also.  

  

      NAVIGATE\_NEXT\_SELECTED         -  NEXT, but only "selected"
entries.  

  

      NAVIGATE\_NEXT\_SELECTED\_MAIN           -  Next selected main.  

  

      NAVIGATE\_NEXT\_EXPANDED        -  NEXT, but only "expanded"
entries.  

  

      NAVIGATE\_NEXT\_EXPANDED\_UNREAD    -  NEXT, but only "expanded"
AND "unread" entries.  

  

      NAVIGATE\_NEXT\_EXPANDED\_SELECTED             -  NEXT, but only
"expanded" AND "selected" entries.  

  

      NAVIGATE\_NEXT\_EXPANDED\_CATEGORY            -  NEXT, but only
"expanded" AND "category" entries.  

  

      NAVIGATE\_NEXT\_EXP\_NONCATEGORY    -  NEXT, but only "expanded"
"non-category" entries.  

  

      NAVIGATE\_NEXT\_HIT         -  NEXT, but only FTSearch "hit"
entries (in the SAME ORDER as the hit's relevance ranking).  

  

      NAVIGATE\_NEXT\_SELECTED\_HIT             -  NEXT, but only
"selected" and FTSearch "hit" entries (in the SAME ORDER as
the hit's relevance ranking).  

  

      NAVIGATE\_NEXT\_UNREAD\_HIT     -  NEXT, but only "unread" and
FTSearch "hit" entries (in the SAME ORDER as the hit's relevance
ranking).  

  

      NAVIGATE\_NEXT\_CATEGORY        -  NEXT, but only "category"
entries.  

  

      NAVIGATE\_NEXT\_NONCATEGORY            -  NEXT, but only
"non-category" entries.  

  




**Description :**



These flags
control how NIFReadEntries steps through a collection. The flags are used to
control both the order in which NIFReadEntries: skips notes in a collection
before reading any notes, and navigates the collection while it is being read.


 **See Also :**


**[NIFReadEntries](NIFReadEntries.md)**



----------------------------------------------------------------------------------------------------------


 





