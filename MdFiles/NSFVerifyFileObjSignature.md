




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Note**



**NSFVerifyFileObjSignature** **- Verifies
a signature on an object.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFVerifyFileObjSignature(**  

      DBHANDLE  hDB,  

      BLOCKID  bhItem**);**



**Description :**



This
function verifies a signature on an object such as a file attachment.  It
returns an error if the signature did not verify.


 


**Parameters :**



Input :  

hDB  -  Handle to the opened database.  

  

bhItem  -  BLOCKID of the object.  

  




Output :  

(routine)  -   Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - The object signature was successfully verified or the object was not
signed.  

ERR\_xxx - STATUS returned from a lower level Notes function.  This value can be
passed to OSLoadString to obtain a text string that can be presented in a
dialog box or log entry.  

  

  




 **See Also :**


**[NSFNoteVerifySignature](NSFNoteVerifySignature.md)**



----------------------------------------------------------------------------------------------------------


 





