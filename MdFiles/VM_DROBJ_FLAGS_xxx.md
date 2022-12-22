




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.5**



**Symbolic Value : Navigators**



**VM\_DROBJ\_FLAGS\_xxx** **-** Navigator
display flags


**----------------------------------------------------------------------------------------------------------**



**#include <vmods.h>**


 **Symbolic Values :**      VM\_DROBJ\_FLAGS\_VISIBLE           -  The object is visible  

  

      VM\_DROBJ\_FLAGS\_SELECTABLE              -  The object can be select (i.e.
is not background)  

  

      VM\_DROBJ\_FLAGS\_LOCKED          -  The object can't be edited  

  

      VM\_DROBJ\_FLAGS\_IMAGEMAP\_BITMAP   -  Stored only for objects of type
SIG\_CD\_VMBITMAP. The bitmap was generated for display in Web browsers via a
Domino server, and is not displayed when opened in Notes.  

  




**Description :**



These flags
control how a graphic object in a Navigator is displayed.  These flags are
stored in the flags field of the common record headers (VMODSdrobj and
VMODSbigobj) in the Navigator records (VIEWMAP\_xxx\_RECORD).


 **See Also :**


**[VMODSbigobj](VMODSbigobj.md)**


**[VMODSdrobj](VMODSdrobj.md)**



----------------------------------------------------------------------------------------------------------


 





