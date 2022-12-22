




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




**Initial Release 4.6**



**Symbolic Value : Rich Text**



**CDHTMLFORMULA\_FLAG\_xxx** **-** Flags for
CDHTMLFORMULA record.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDHTMLFORMULA\_FLAG\_ATTR     -  Formula is to compute HTML
attributes.  

  

      CDHTMLFORMULA\_FLAG\_ALT       -  Formula is to compute alternate HTML.  

  

      CDHTMLFORMULA\_FLAG\_ACTION\_LABEL             -  Formula is to compute
action label.  

  




**Description :**



These flags
are stored in the dwFlags field of the CDHTMLFORMULA record, and identify the
type of formula stored in this record.


 **See Also :**


**[CDHTMLFORMULA](CDHTMLFORMULA.md)**



----------------------------------------------------------------------------------------------------------


 





