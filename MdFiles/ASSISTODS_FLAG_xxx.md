




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



**ASSISTODS\_FLAG\_xxx** **-** Agent
control flags.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ASSISTODS\_FLAG\_HIDDEN            -  TRUE if manual assistant
is hidden.  

  

      ASSISTODS\_FLAG\_NOWEEKENDS             -  Do not run on weekends.  

  

      ASSISTODS\_FLAG\_STOREHIGHLIGHTS    -  TRUE if storing highlights.  

  

      ASSISTODS\_FLAG\_MAILANDPASTE           -  TRUE if this is the V3-style
mail and paste macro.  

  

      ASSISTODS\_FLAG\_CHOOSEWHENENABLED         -  TRUE if server to run on
should be chosed when enabled.  

  




**Description :**



These flags
are set in the dwFlags field of the ODS\_ASSISTSTRUCT record.


 **See Also :**


**[ODS\_ASSISTSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/540A215A94BACC0385256261006222BC)**



----------------------------------------------------------------------------------------------------------


 





