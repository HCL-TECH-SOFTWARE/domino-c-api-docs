




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



**MailTransferMessageLocal** **- Transfers
a message to the local Mail Router.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailTransferMessageLocal(**  

      DHANDLE  hMessage**);**



**Description :**



This
function transfers a message to the local Mail Router by transferring it to a
mail.box file on the local machine. This function is normally used by mail
gateway programs running on the Lotus Domino Server.  If there are multiple
mail.box files on the local machine, this function will transfer the message
properly.  This function will not succeed on a Notes workstations where there
is no local mail.box file.  

  

Once a message is transferred to the Router, responsibility for the message is
also transferred; a gateway does not need to retain any further state regarding
the message as the Router will either deliver the message or return a
Non-Delivery Report back to the originator.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **Sample Usage :**


    /\*  Deliver the
message. \*/  

    /\*  If local, transfer message to the local mail.box \*/  

    if (fLocal)  

    {  

        if (status = MailTransferMessageLocal(hMsg))  

        {  

            /\* Unable to transfer message to local mail box \*/  

            error = ERR\_SENDMAIL\_CANTTRANSFER;  

            goto CloseMsg;  

        }  

        /\* else we successfully transferred msg to local mail box \*/  

        /\* Save msg to user's mail file and clean up.\*/  

        if (status = NSFNoteUpdate(hMsg, UPDATE\_NOCOMMIT))  

        {   /\* Unable to update message in local mail file \*/  

            error = ERR\_SENDMAIL\_CANTUPDATEFILE;  

        }  

        goto CloseMsg;  

    }  

  




 




----------------------------------------------------------------------------------------------------------


 





