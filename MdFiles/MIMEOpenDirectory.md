




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 7.0.2**



**Function : MIME**



**MIMEOpenDirectory** **- create a
MIMEDIRECTORY for an open Notes MIME format note.**


**----------------------------------------------------------------------------------------------------------**



**#include <mimedir.h>**



STATUS
LNPUBLIC **MIMEOpenDirectory(**  

      NOTEHANDLE  hNote,  

      HMIMEDIRECTORY \*phMIMEDir**);**



**Description :**



This
function MIMEOpenDirectory creates a MIMEDIRECTORY object for an open note. 
You must specify as input a handle to an open note and a pointer to a
MIMEDIRECTORY handle.


 


If the open
note is a Notes MIME format document, MIMEOpenDirectory creates a tree
structure to represent the various parts of the MIME document; RFC2822 headers,
MIME body part Content headers, MIME body parts, etc.


 


If the open
note is a Notes Rich Text format document, MIMEOpenDirectory first converts the
document to MIME format and then creates the MIMEDIRECTORY.


 


Elements and
attributes of the MIMEDIRECTORY may be accessed via the various MIMEEntity
APIs; see below for details.


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully opened the MIMEDIRECTORY.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  

phMIMEDir  -  a pointer to a MIMEDIRECTORY handle.  

  




 **Sample Usage :**



HMIMEDIRECTORY
hMIMEDir;


STATUS error;


 


if (error =
MIMEOpenDirectory(hNote, &hMIMEDir)) {


        goto exit;


}


 


 **See Also :**


**[HMIMEDIRECTORY](HMIMEDIRECTORY.md)**


**[MIMEFreeDirectory](MIMEFreeDirectory.md)**



----------------------------------------------------------------------------------------------------------


 





