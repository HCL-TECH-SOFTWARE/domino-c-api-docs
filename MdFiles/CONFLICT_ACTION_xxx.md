




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



**Symbolic Value : Extension Manager**



**CONFLICT\_ACTION\_xxx** **-** Replication
conflict handler return options.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      CONFLICT\_ACTION\_MERGE           -  The two conflicting notes
were resolved by the replication conflict handler and Domino or Notes is to
merge the two notes.  

  

      CONFLICT\_ACTION\_HANDLED       -  The conflict was handled by the
replication conflict handler. Domino or Notes need not perform any further
action.  

  




**Description :**



A
replication conflict handler is written as an extension manager.  The extension
manager can pass one of these values back to Domino or Notes in order to tell
Domino or Notes how to continue.  It can also pass ERR\_EM\_CONTINUE back to
Domino or Notes if Domino or Notes is to handle the replication conflict.  For
example, if an error occurs in your replication conflict handler you may want
to abort handling the conflict yourself and pass ERR\_EM\_CONTINUE back to Domino
or Notes.


 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





