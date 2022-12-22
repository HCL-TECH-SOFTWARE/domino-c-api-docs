




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



**Function : Form**



**StoredFormAppendSubformToken** **- Add a
token to the end of a subform name so that the subform won't be found in a pre
6 Client/Server**


**----------------------------------------------------------------------------------------------------------**



**#include <dbmisc.h>**



STATUS
LNPUBLIC **StoredFormAppendSubformToken(**  

      char\*pszSubName,  

      WORD  wSubNameBufferLen**);**



**Description :**



This
function adds a token to the end of a subform name so that the subform won't be
found in a pre 6 Client/Server.  (The 6 client and server will remove this
token before looking up the subform name.)


 


 


**Parameters :**



Input :  

pszSubName  -  a pointer to a buffer which contains the subform name  

  

wSubNameBufferLen  -  a WORD containing the length of the text buffer  

  




Output :  

(routine)  -  Return STATUS from call.  NOERROR if successful.  

  

  




 **See Also :**


**[StoredFormAddItems](StoredFormAddItems.md)**


**[StoredFormRemoveItems](StoredFormRemoveItems.md)**



----------------------------------------------------------------------------------------------------------


 





