




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




**Initial Release 4.0**



**Symbolic Value : Agents**



**ACTIONBYFIELD\_OP\_xxx** **-** Field
operations for form actions.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ACTIONBYFIELD\_OP\_REPLACE      -  Replace value.  

  

      ACTIONBYFIELD\_OP\_APPEND       -  Append value as list element.  

  

      ACTIONBYFIELD\_OP\_REMOVE       -  Remove value from list.  

  




**Description :**



These are
the values that may be stored in the wOperator field of the
ODS\_ASSISTFIELDSTRUCT structure within a CDACTIONBYFORM record.  The operator
value specifies the actual operation on the field.


 **See Also :**


**[CDACTIONBYFORM](CDACTIONBYFORM.md)**


**[ODS\_ASSISTFIELDSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A3E6C6BBE236009C852562610053DF95)**



----------------------------------------------------------------------------------------------------------


 





