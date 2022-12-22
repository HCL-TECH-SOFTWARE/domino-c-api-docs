




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



**ACTIONSENDMAIL\_xxx** **-** CDACTIONSENDMAIL
record field array indexes


**----------------------------------------------------------------------------------------------------------**



**#include <queryods.h>**


 **Symbolic Values :**      ACTIONSENDMAIL\_FIELDCOUNT   -  Number of elements in the
SendMail action field size array.  

  

      ACTIONSENDMAIL\_TOFIELD          -  Index of the "To" field
length.  

  

      ACTIONSENDMAIL\_CCFIELD          -  Index of the "Cc" field
length.  

  

      ACTIONSENDMAIL\_BCCFIELD        -  Index of the "Bcc" field
length.  

  

      ACTIONSENDMAIL\_SUBJECTFIELD            -  Index of the
"Subject" field length.  

  

      ACTIONSENDMAIL\_BODYFIELD      -  Index of the "Body" field
length.  

  




**Description :**



The
CDACTIONSENDMAIL record contains an array of length values for the SendMail
action fields.  These values are used to index into the array.


 **See Also :**


**[CDACTIONNEWSLETTER](CDACTIONNEWSLETTER.md)**


**[CDACTIONSENDMAIL](CDACTIONSENDMAIL.md)**



----------------------------------------------------------------------------------------------------------


 





