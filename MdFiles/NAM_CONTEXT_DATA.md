




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Menu Add-In**



**NAM\_CONTEXT\_DATA** **-** Contains
import/export information.


**----------------------------------------------------------------------------------------------------------**



**#include
<addinmen.h>**



**Definition :**



typedef struct  

   {  

   FLAG Context:3;    /\* Desk, View, Editor R/W, Editor R/O \*/  

   FLAG fCanExport:1; /\* TRUE if the add-in can perform an export.\*/  

   FLAG fCanImport:1; /\* TRUE if the add-in can request an import.\*/  

   union  

      {  

      EDITIXDATA Edit;  

      VIEWIXDATA View;  

      } IXData;  

   } NAM\_CONTEXT\_DATA;


 


**Description :**



This
structure provides import/export data to a menu add-in program.  The Context
field of indicates the Notes context when the menu item was selected.  It can
take one of the following values:  

     NAM\_IN\_DESK                        In the desktop.  

     NAM\_IN\_VIEW                         In a view.  

     NAM\_IN\_VIEW\_DESIGN     Designing a view.  

     NAM\_IN\_EDIT\_RO                In a read only document.  

     NAM\_IN\_EDIT\_RW               In a document - edit mode.  

     NAM\_IN\_EDIT\_DESIGN      Designing a document.  

  

The a menu add-in receives this information when processing the NAMM\_COMMAND
message from Notes.  

  




 **See Also :**


**[NAM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0D8215A59837A258852561E0006FD604)**


**[NAM\_IN\_xxx](NAM_IN_xxx.md)**


**[EDITIXDATA](EDITIXDATA.md)**


**[EDITIMPORTDATA](EDITIMPORTDATA.md)**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**


**[VIEWIXDATA](VIEWIXDATA.md)**


**[NAM\_COMMAND\_INFO](NAM_COMMAND_INFO.md)**



----------------------------------------------------------------------------------------------------------


 





