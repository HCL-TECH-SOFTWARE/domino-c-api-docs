




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



**Symbolic Value : Composite Data;
Rich Text**



**EMBEDDEDCTL\_xxx** **-** CDEMBEDDEDCTL
- CtlType


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      EMBEDDEDCTL\_EDIT         -  Control type is edit.  

  

      EMBEDDEDCTL\_COMBO    -  Control type is a combobox.  

  

      EMBEDDEDCTL\_LIST          -  Control type is a listbox.  

  

      EMBEDDEDCTL\_TIME         -  Control type describes calendar/scheduling.  

  

      EMBEDDEDCTL\_KEYGEN   -  Control type also a combobox.  

  

      EMBEDDEDCTL\_FILE          -  Control type also edit.  

  

      EMBEDDEDCTL\_TIMEZONE            -  Control type is timezone.  

  

      EMBEDDEDCTL\_COLOR     -  Control type is a color picker.  

  




**Description :**



Implemented
as an enumerated type:


 


enum {


   EMBEDDEDCTL\_EDIT =
0,


   EMBEDDEDCTL\_COMBO =
1,


   EMBEDDEDCTL\_LIST =
2,


   EMBEDDEDCTL\_TIME =
3,


   EMBEDDEDCTL\_KEYGEN =
4,


   EMBEDDEDCTL\_FILE =
5,


  
EMBEDDEDCTL\_TIMEZONE = 6,


      EMBEDDEDCTL\_COLOR
= 7


};


 **See Also :**


**[CDEMBEDDEDCTL](CDEMBEDDEDCTL.md)**



----------------------------------------------------------------------------------------------------------


 





