




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



**ACTIONSENDMAIL\_FLAG\_xxx** **-** Option flags
for CDACTIONSENDMAIL record.


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ACTIONSENDMAIL\_FLAG\_INCLUDEDOC    -  Include original
document in message.  

  

      ACTIONSENDMAIL\_FLAG\_INCLUDELINK    -  Include doclink to document.  

  

      ACTIONSENDMAIL\_FLAG\_SAVEMAIL         -  Save a copy of the message.  

  

      ACTIONSENDMAIL\_FLAG\_TOFORMULA     -  "To" field is a formula.  

  

      ACTIONSENDMAIL\_FLAG\_CCFORMULA     -  "cc" field is a formula.  

  

      ACTIONSENDMAIL\_FLAG\_BCCFORMULA   -  "bcc" field is a formula.  

  

      ACTIONSENDMAIL\_FLAG\_SUBJECTFORMULA      -  "Subject" field is a
formula.  

  




**Description :**



These flags
specify options for the Send Mail action for a Agent.  These flags are stored
in the dwFlags field of the CDACTIONSENDMAIL structure.


 **See Also :**


**[CDACTIONNEWSLETTER](CDACTIONNEWSLETTER.md)**


**[CDACTIONSENDMAIL](CDACTIONSENDMAIL.md)**



----------------------------------------------------------------------------------------------------------


 





