




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




 


**Function : Mail Gateway**



**MailCreateMessageFile** **- Creates
and opens a new gateway message file.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailCreateMessageFile(**  

      char far \*FileName,  

      char far \*TemplateFileName,  

      char far \*Title,  

      DBHANDLE far \*rethFile**);**



**Description :**



This
function creates and opens a new gateway message file.  This function should be
called by the gateway to create a new message file when it begins execution for
the first time.  Use MailCloseMessageFile to close the message file handle and
deallocate the memory associated with it.  

  

The access control list of the new message file is created with Default set to
Depositor access and the local server and the value of the Admin notes.ini
variable set to Manager access.


 


**Parameters :**



Input :  

FileName  -  Message file pathname string pointer (null-terminated).  

  

TemplateFileName  -  Message file template pathname string pointer
(null-terminated).  

  

Title  -  Title string pointer (null-terminated).  NULL if template title is to
be used.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

rethFile  -  Message file handle.  

  




 **See Also :**


**[MailCloseMessageFile](MailCloseMessageFile.md)**



----------------------------------------------------------------------------------------------------------


 





