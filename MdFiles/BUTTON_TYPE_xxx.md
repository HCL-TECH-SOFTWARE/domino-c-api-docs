




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



**BUTTON\_TYPE\_xxx** **-** CDDATAFLAGS
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      BUTTON\_TYPE\_NORMAL   -  button type is normal  

  

      BUTTON\_TYPE\_OK             -  button type is ok  

  

      BUTTON\_TYPE\_CANCEL    -  button type is cancel  

  

      BUTTON\_TYPE\_HELP         -  button type is help  

  

      BUTTON\_TYPE\_MASK        -  BUTTON\_TYPE\_OK | BUTTON\_TYPE\_CANCEL |
BUTTON\_TYPE\_HELP  

  




**Description :**



On-disk
flags for CDDATAFLAGS. For buttons with type information, the CDBUTTON record
is followed by a CDDATAFLAGS structure with its Flags member set to a
BUTTON\_TYPE\_xxx value.


 **See Also :**


**[CDDATAFLAGS](CDDATAFLAGS.md)**



----------------------------------------------------------------------------------------------------------


 





