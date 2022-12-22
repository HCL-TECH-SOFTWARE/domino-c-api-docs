




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




**Initial Release 5.0**



**Function : Rich Text**



**EC\_DIALOGUNITS** **- Evaluates
the Flags member of CDEMBEDDEDCTL against EC\_FLAG\_UNITS**


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



BOOL **EC\_DIALOGUNITS(**  

      WORD  flags**);**



**Description :**



Implemented
as a macro:  

  

#define
EC\_DIALOGUNITS(flags)   ((flags & EC\_FLAG\_UNITS) == EC\_FLAG\_DIALOGUNITS)


 


**Parameters :**



Input :  

flags  -  EC\_FLAG\_xxx  

  




Output :  

(routine)  -  Returns TRUE if width/height of specified flag have been adjusted
to fit contents, FALSE otherwise.  

  

  




 **See Also :**


**[CDEMBEDDEDCTL](CDEMBEDDEDCTL.md)**


**[EC\_FLAG\_xxx](EC_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





