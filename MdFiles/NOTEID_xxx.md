




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




 


**Symbolic Value : IDs**



**NOTEID\_xxx** **-** Reserved
note IDs


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      NOTEID\_RESERVED           -  Reserved note ID used for
categories in NIFReadEntries and for deleted notes.  

  

      NOTEID\_ADD          -  Reserved note ID used as input to NoteUpdate, to
add a new note (gets error if UNID assigned to new note already exists).  

  

      NOTEID\_ADD\_OR\_REPLACE          -  Reserved note ID used as input to
NoteUpdate, to update if note UNID already exists, or add note if doesn't
exist.  

  

      NOTEID\_ADD\_UNID            -  Reserved note ID used as input to
NoteUpdate. Try to preserve the specified note UNID, but if it already exists,
assign a new one. (Note that the UNID in the hNote IS updated.)  

  

      NOTEID\_NULL\_FOLDER      -  Reserved note ID used for null folder ids.  

  

      NOTEID\_NO\_PARENT         -  Reserved note ID used to indicate that this
note has no parent in the response hierarchy.  

  




**Description :**



These
symbols indicate special note IDs, such as categories and deleted notes.


 **See Also :**


**[NOTEID](NOTEID.md)**



----------------------------------------------------------------------------------------------------------


 





