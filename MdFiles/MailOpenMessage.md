




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



**MailOpenMessage** **- Reads an
outbound message from a message list into memory.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailOpenMessage(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      DHANDLE far \*hMessage**);**



**Description :**



This function
opens an outbound message from a message list and reads it into memory.  This
function is used by gateways to handle messages outbound to a foreign mail
system.  

  

An open message handle is equivalent to an NSF note handle and can be used, if
necessary, for direct calls to NSF.  Use MailCloseMessage to close the message
handle and deallocate the memory associated with it.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

hMessage  -  Open message handle  

  




 **Sample Usage :**


    STATUS      error =
NOERROR;  

    char       \*szServerName;  

    char       \*szMailFile;  

    char        szMailFilePath[MAXPATH+1];  

    DHANDLE      hMessageFile;  

    DHANDLE      hMessageList = NULLHANDLE, hMessage;  

    DARRAY     \*MessageList;  

    WORD        MessageCount, Msg;  

  

    if (error = MailCreateMessageList(hMessageFile,   

                        &hMessageList, &MessageList,
&MessageCount))  

    {  

        printf ("Error: unable to create message list.\n");  

        goto Exit1;  

    }  

  

    /\* Print out each of the outbound messages. \*/  

  

    for (Msg = 0; Msg < MessageCount; Msg++)  

    {  

        printf ("\nMessage #%d: \n", Msg);  

  

        if (error = MailOpenMessage (MessageList, Msg, &hMessage))  

        {  

            printf ("Error: unable to open message number %d.\n",
Msg);  

            goto Exit2;  

        }


 **See Also :**


**[MailCloseMessage](MailCloseMessage.md)**



----------------------------------------------------------------------------------------------------------


 





