




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 6**



**Data Type : IDs; Rich Text**



**FRAMEVIEWPOSITION** **-** Contains the
UNID of the currently selected outline entry.


**----------------------------------------------------------------------------------------------------------**



**#include
<fsods.h>**



**Definition :**



typedef struct  

{  

    char    posunid[MAXUNIDSTRING+1];  

} FRAMEVIEWPOSITION;


 


**Description :**



This
structure is used ONLY in the bookmarks database.  It contains one entry per
FRAME/FRAMESET.  At the end of all the frame information is a set of  these
structures which contain the UNID (as a string of maximum length MAXUNIDSTRING)
for the current position in the outline for that frame if there is one.  If
not, the UNID is null.


 **See Also :**


**[CDFRAME](CDFRAME.md)**


**[CDFRAMESET](CDFRAMESET.md)**


**[MAXUNIDSTRING](MAXUNIDSTRING.md)**



----------------------------------------------------------------------------------------------------------


 





