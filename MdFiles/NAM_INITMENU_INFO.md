




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



**NAM\_INITMENU\_INFO** **-** Contains
information that can be used by a menu add-in program to determine whether to
enable, disable, gray, check, etc. its menu item(s).


**----------------------------------------------------------------------------------------------------------**



**#include
<addinmen.h>**



**Definition :**



typedef struct  

   {  

   HMENU hMenu;         /\* Handle of the Add-In PopUp menu. \*/  

   NAM\_CONTEXT\_DATA Data;  /\* Context specific data. \*/  

   } NAM\_INITMENU\_INFO;


 


**Description :**



This
structure contains information that can be used by a menu add-in program to
determine whether to enable, disable, gray, check, etc. its menu item(s).  

  

The menu add-in receives this information when processing the NAMM\_INITMENU
message from Notes.


 **See Also :**


**[NAM\_CONTEXT\_DATA](NAM_CONTEXT_DATA.md)**



----------------------------------------------------------------------------------------------------------


 





