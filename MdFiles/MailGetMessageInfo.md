




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



**MailGetMessageInfo** **- Returns
information about a message in a message list.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageInfo(**  

      DARRAY far \*MessageList,  

      WORD  Message,  

      WORD far \*RecipientCount,  

      WORD far \*Priority,  

      WORD far \*Report**);**



**Description :**



This
function returns information about a message in a message list.


 


**Parameters :**



Input :  

MessageList  -  Message list pointer.  

  

Message  -  Message number (0-n).  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

RecipientCount  -  (Optional) - If not NULL, number of recipients in the
message.  In Release 4.0 and later, only messages which have been sent have a recipients
list.  

  

Priority  -  (Optional) - If not NULL, priority of the message, which can be
one of DELIVERY\_PRIORITY\_xxx.  

  

Report  -  (Optional) - If not NULL, type of delivery reporting requested,
which can be one of DELIVERY\_REPORT\_xxx.  

  




 **Sample Usage :**


    STATUS      error =
NOERROR;  

    HANDLE      hMessageList;  

    WORD        MessageCount, Msg, RecipientCount, Rec;  

    char        RecipientName[MAXRECIPIENTNAME+1];  

    WORD        RecipientNameLength;  

    char        UserName[MAXUSERNAME + 1];  

    WORD        UserNameLength;  

    char        DomainName[MAXDOMAINNAME+1];  

    WORD        DomainNameLength;  

  

  

        if (error = MailGetMessageInfo(MessageList, Msg,   

                            &RecipientCount, NULL, NULL))  

        {  

            printf ("Error: unable to get number of recipients in
message.\n");  

            MailCloseMessage (hMessage);  

            goto Exit2;  

        }  

        printf ("\tNumber of Recipients = %d.\n", RecipientCount);  

  

        for (Rec = 0; Rec < RecipientCount; Rec++)  

        {  

            MailGetMessageRecipient(MessageList, Msg, Rec, RecipientName,  

                    sizeof(RecipientName), &RecipientNameLength);  

            MailParseMailAddress(RecipientName, RecipientNameLength,   

                    UserName, sizeof(UserName), &UserNameLength,  

                    DomainName, sizeof(DomainName), &DomainNameLength);  

  

            UserName[UserNameLength] = '\0';  

            DomainName[DomainNameLength] = '\0';  

            printf ("\t\tRecipient %d = '%s'\t Domain = '%s'\n", Rec,  

                                UserName, DomainName);  

        }   /\* end of loop over recipients \*/


 **See Also :**


**[DELIVERY\_PRIORITY\_xxx](DELIVERY_PRIORITY_xxx.md)**


**[DELIVERY\_REPORT\_xxx](DELIVERY_REPORT_xxx.md)**


**[MailGetMessageRecipient](MailGetMessageRecipient.md)**


**[MailParseMailAddress](MailParseMailAddress.md)**



----------------------------------------------------------------------------------------------------------


 





