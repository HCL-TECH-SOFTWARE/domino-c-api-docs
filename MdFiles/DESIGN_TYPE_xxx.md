




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




**Initial Release 4.0**



**Symbolic Value : Folders**



**DESIGN\_TYPE\_xxx** **-** Type of
folder - shared or private.


**----------------------------------------------------------------------------------------------------------**



**#include <design.h>**


 **Symbolic Values :**      DESIGN\_TYPE\_SHARED     -  Note is shared. Shared notes are
always stored in the database. They are never stored in the desktop file.  

  

      DESIGN\_TYPE\_PRIVATE\_DATABASE         -  Note is private and is stored in
the database rather than in the desktop file.  

  




**Description :**



These
symbolic constants describe the type of folder being created.


 **Sample Usage :**


if (error = FolderCreate
(hDB2, NULLHANDLE, FormatNoteID, hDB1, 


                         
"API Folder", MAXWORD,  

                          DESIGN\_TYPE\_PRIVATE\_DATABASE,  

                          0L, &FNoteID))


 **See Also :**


**[FolderCreate](FolderCreate.md)**



----------------------------------------------------------------------------------------------------------


 





