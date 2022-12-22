




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



**Symbolic Value : Billing**



**BILL\_xxx (actions)** **-** Session
Billing Actions


**----------------------------------------------------------------------------------------------------------**



**#include <billing.h>**


 **Symbolic Values :**      BILL\_SESSION\_START        -  Indicates the first session
record for this session  

  

      BILL\_DB\_OPEN        -  Indicates the database is open  

  

      BILL\_DB\_CLOSE      -  Indicates a request to close the database. This
action enables Domino billing to track how often a database opens and closes
during a session  

  

      BILL\_SESSION\_STAMP       -  Indicates the session is active. This stamp
occurs if the timer specified by the notes.ini BillingSuppressTime variable
expires and there is database activity only  

  

      BILL\_DB\_STAMP     -  Indicates the database activity during an open
session  

  

      BILL\_DB\_CLOSE\_END         -  Indicates the server closed the database
when the session ended  

  

      BILL\_SESSION\_END            -  Indicates the session has ended  

  




**Description :**



The above
constants define the state of a Domino database or session at the time the
billing record occurs. The values are assigned to the Action field of the
SESSIONREC and DBREC billing records, as appropriate.  


 


 **See Also :**


**[DBREC](DBREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





