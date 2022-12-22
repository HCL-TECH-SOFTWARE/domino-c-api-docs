




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




**Initial Release 5.0.7**



**Symbolic Value : Constants; Rich
Text**



**ACTION\_SYS\_CMD\_xxx** **-** Action
system commands.


**----------------------------------------------------------------------------------------------------------**



**#include <actprop.h>**


 **Symbolic Values :**      ACTION\_SYS\_CMD\_CATEGORIZE              -  Put a document in
a category.  

  

      ACTION\_SYS\_CMD\_EDIT    -  Open a document in edit mode.  

  

      ACTION\_SYS\_CMD\_SEND   -  Send a document to the address specified in the
document's "SendTo" field. if there is no "SendTo" field in
the document, use ACTION\_SYS\_CMD\_FORWARD.  

  

      ACTION\_SYS\_CMD\_FORWARD      -  Forward a document. Use this option if
there is no "SendTo" field in the document.  

  

      ACTION\_SYS\_CMD\_MOVE\_TO\_FOLDER    -  Put a document in a folder.  

  

      ACTION\_SYS\_CMD\_REMOVE\_FROM\_FOLDER      -  Remove a document from a
folder.  

  




**Description :**



Action
system commands.  If you set ACTION\_SYS\_COMMAND as the value for the Type
member of CDACTION, set the second word of  the variable action data to one of
these values. Please see the Tech Note "[System Action Command Codes](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/76189A185BACF654852563B1006A7E8C)" for more
details.


 **See Also :**


**[CDACTION](CDACTION.md)**



----------------------------------------------------------------------------------------------------------


 





