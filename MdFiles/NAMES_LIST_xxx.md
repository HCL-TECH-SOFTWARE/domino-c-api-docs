




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




**Initial Release 4.5**



**Symbolic Value : Access Control List**



**NAMES\_LIST\_xxx** **-** NAMES\_LIST -
Authentication flags.


**----------------------------------------------------------------------------------------------------------**



**#include <acl.h>**


 **Symbolic Values :**      NAMES\_LIST\_AUTHENTICATED     -  Set if names list has been
authenticated via Notes.  

  

      NAMES\_LIST\_PASSWORD\_AUTHENTICATED        -  Set if names list has been
authenticated using external password -- Triggers "Maximum Internet name
& password" (set in the database ACL) access level allowed.  

  

      NAMES\_LIST\_FULL\_ADMIN\_ACCESS         -  Set if user requested full admin
access and it was granted.  

  




**Description :**



Possible
values for the Authenticated member of the NAMES\_LIST structure.


 **See Also :**


**[NAMES\_LIST](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/009F0044002000E285255E3F0001744B)**


**[ACLLookupAccess](ACLLookupAccess.md)**



----------------------------------------------------------------------------------------------------------


 





