




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



**MailGetMessageOriginator** **- Returns
name/address of the originator of a message.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageOriginator(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      char far \*OriginatorName,  

      WORD  OriginatorNameSize,  

      WORD far \*OriginatorNameLength**);**



**Description :**



This
function returns the name/address of the originator of a message.  The
originator of a message is the user name and domain name of the sender of a
message.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  

OriginatorNameSize  -  Originator string buffer size.  (MAXRECIPIENTNAME
recommended).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

OriginatorName  -  Originator name/address string (null-terminated).  

  

OriginatorNameLength  -  Originator string length (not including '\0').  

  




 **Sample Usage :**


    DARRAY    
\*MessageList;  

    WORD        MessageCount, Msg;;  

    char        Originator[MAXRECIPIENTNAME+1];  

    WORD        OriginatorLength;  

  

  

        if (error = MailGetMessageOriginator(MessageList, Msg,   

                Originator, sizeof(Originator), &OriginatorLength))  

        {  

            printf ("Error: unable to get message originator.\n");  

            goto Exit2;  

        }  

  

        Originator[OriginatorLength] = '\0';  

  

        printf ("\tOriginator = '%s'\n", Originator);


 **See Also :**


**[MailGetMessageOriginatorDomain](MailGetMessageOriginatorDomain.md)**



----------------------------------------------------------------------------------------------------------


 





