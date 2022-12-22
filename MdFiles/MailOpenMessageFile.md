




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**MailOpenMessageFile** **- Opens a
gateway's outbound message file.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailOpenMessageFile(**  

      char far \*FileName,  

      DBHANDLE far \*rethFile**);**



**Description :**



This
functions opens a gateway's outbound message file.   

  

A handle to a message file is equivalent to an NSF database handle and can be
used, if needed, in direct NSF calls.  Use MailCloseMessageFile to close the
message file handle and deallocate the memory associated with it.


 


**Parameters :**



Input :  

FileName  -  Message file pathname string pointer (null-terminated).  May be
NULL which will default to the mail.box file on the Lotus Domino Server.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

rethFile  -  Message file handle.  

  




 **Sample Usage :**


 STATUS      error =
NOERROR;  

    char       \*szServerName;  

    char       \*szMailFile;  

    char        szMailFilePath[MAXPATH+1];  

    HANDLE      hMessageFile;  

   

    szServerName = argv[1];  

    szMailFile = argv[2];  

  

    OSPathNetConstruct( NULL,               /\* port name  \*/  

                        szServerName,     

                        szMailFile,  

                        szMailFilePath);  

  

    /\* Open the message file. \*/  

  

    if (error = MailOpenMessageFile(szMailFilePath, &hMessageFile))  

    {  

        printf ("Error: unable to open '%s'.\n", szMailFilePath);  

        goto Exit0;  

    }


 **See Also :**


**[MailCloseMessageFile](MailCloseMessageFile.md)**



----------------------------------------------------------------------------------------------------------


 





