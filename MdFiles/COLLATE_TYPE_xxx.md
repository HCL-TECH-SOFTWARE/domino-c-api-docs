




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



**COLLATE\_TYPE\_xxx** **-** COLLATE\_DESCRIPTOR
- keytype (Specifies how columns in a view are sorted.)


**----------------------------------------------------------------------------------------------------------**



**#include <nifcoll.h>**


 **Symbolic Values :**      COLLATE\_TYPE\_KEY          -  Collate by key in summary
buffer  

  

      COLLATE\_TYPE\_NOTEID    -  Collate by note ID  

  

      COLLATE\_TYPE\_TUMBLER            -  Collate by "tumbler" summary
key  

  

      COLLATE\_TYPE\_CATEGORY          -  Collate by "category" summary
key  

  




**Description :**



These are
the possible values for the  keytype member of the COLLATE\_DESCRIPTOR data
structure.  The keytype structure member specifies the type of sorting that is
done in the specified column in a view.


 **See Also :**


**[COLLATE\_DESCRIPTOR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00BE00740029007F85255E37006051E3)**



----------------------------------------------------------------------------------------------------------


 





