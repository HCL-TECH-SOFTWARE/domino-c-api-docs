




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




**Initial Release 6**



**Symbolic Value : Composite Data;
Rich Text**



**BUTTON\_SPEC\_xxx** **-** CDDATAFLAGS
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BUTTON\_SPEC\_NORMAL   -  Button with this attribute is
normal.  

  

      BUTTON\_SPEC\_DEFAULT   -  Button with this attribute is the default push
button in a dialog box.  

  

      BUTTON\_SPEC\_MASK        -  BUTTON\_SPEC\_DEFAULT  

  




**Description :**



On-disk
flags for CDDATAFLAGS. For buttons with type information, the CDBUTTON record
is followed by a CDDATAFLAGS structure with its Flags member set to a
BUTTON\_TYPE\_xxx value. If the button type is the default type, the Flags member
is set to the BUTTON\_SPEC\_DEFAULT value.


 




----------------------------------------------------------------------------------------------------------


 





