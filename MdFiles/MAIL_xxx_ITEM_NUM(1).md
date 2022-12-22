




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




 


**Symbolic Value : Mail Gateway**



**MAIL\_xxx\_ITEM\_NUM(1)** **-** Mail note
item name codes.


**----------------------------------------------------------------------------------------------------------**



**#include <mail.h>**


 **Symbolic Values :**      MAIL\_SENDTO\_ITEM\_NUM             -  Message recipient name.
Specifies who to send the message to. Use MAIL\_SENDTO\_LIST\_ITEM\_NUM if there is
more than one recipient. This item is of TYPE\_TEXT.  

  

      MAIL\_COPYTO\_ITEM\_NUM             -  List of recipient names to send
copies. This item is of TYPE\_TEXT.  

  

      MAIL\_FROM\_ITEM\_NUM     -  Originator's user name (does not include domain
name). This item is of TYPE\_TEXT.  

  

      MAIL\_SUBJECT\_ITEM\_NUM            -  Subject text. This item is of
TYPE\_TEXT.  

  

      MAIL\_COMPOSEDDATE\_ITEM\_NUM           -  Date/time message was composed.
This item is of TYPE\_TIME.  

  

      MAIL\_POSTEDDATE\_ITEM\_NUM    -  Date/time message was mailed by originator.
This item is of TYPE\_TIME.  

  

      MAIL\_BODY\_ITEM\_NUM      -  Body. This item is of TYPE\_COMPOSITE.  

  

      MAIL\_INTENDEDRECIPIENT\_ITEM\_NUM    -  List of intended recipient
addresses (Reports only). This item is of TYPE\_TEXT.  

  

      MAIL\_FAILUREREASON\_ITEM\_NUM           -  Failure reason text
(Non-Delivery Report only). This item is of TYPE\_TEXT.  

  

      MAIL\_RECIPIENTS\_ITEM\_NUM       -  Message recipient address. Specifies
where a saved message was sent. Use MAIL\_RECIPIENTS\_LIST\_ITEM\_NUM if there is
more than one recipient address. This item is of TYPE\_TEXT.  

  

      MAIL\_ROUTINGSTATE\_ITEM\_NUM            -  Routing state. This item is
reserved for the Domino router and should not be used by the gateway. It is of
TYPE\_TEXT.  

  

      MAIL\_FORM\_ITEM\_NUM     -  Form name. This item is of TYPE\_TEXT.  

  

      MAIL\_SAVED\_FORM\_ITEM\_NUM    -  Original form name (Non-Delivery Report
only). This item is of TYPE\_TEXT.  

  

      MAIL\_BLINDCOPYTO\_ITEM\_NUM   -  List of recipient names to send blind
copies. This item is of TYPE\_TEXT.  

  

      MAIL\_DELIVERYPRIORITY\_ITEM\_NUM       -  Delivery priority ("H",
"N", "L"). This item is of TYPE\_TEXT.  

  

      MAIL\_DELIVERYREPORT\_ITEM\_NUM         -  Delivery report type requested
("N", "B", "C"). This item is of TYPE\_TEXT.  

  

      MAIL\_DELIVEREDDATE\_ITEM\_NUM           -  Date/time message was delivered.
This item is of TYPE\_TIME.  

  

      MAIL\_DELIVERYDATE\_ITEM\_NUM              -  Date/time message was
delivered (Delivery Reports only). This item is of TYPE\_TIME.  

  

      MAIL\_CATEGORIES\_ITEM\_NUM     -  Categories. This item is of TYPE\_TEXT.  

  

      MAIL\_FROMDOMAIN\_ITEM\_NUM    -  Originator's domain name. This item is of
TYPE\_TEXT.  

  

      MAIL\_SENDTO\_LIST\_ITEM\_NUM    -  List of message recipient names.
Specifies who to send the message to. Used to specify more than one recipient.
This item is of TYPE\_TEXT\_LIST.  

  

      MAIL\_RECIPIENTS\_LIST\_ITEM\_NUM          -  List of message recipient
addresses. Specifies where a saved message was sent. Used to specify more than
one recipient address. This item is of TYPE\_TEXT\_LIST.  

  

      MAIL\_RECIP\_GROUPS\_EXP\_ITEM\_NUM    -  List of recipient group names that
have been expanded. This item is of TYPE\_TEXT\_LIST.  

  

      MAIL\_RETURNRECEIPT\_ITEM\_NUM          -  Return receipt requested
("1", "0"). This item is of TYPE\_TEXT. Setting this item to
"1" means "send a return receipt", setting the item to
"0" means "do not send a return receipt."  

  

      MAIL\_ROUTE\_HOPS\_ITEM\_NUM    -  Routing hop count. This item is of
TYPE\_NUMBER.  

  

      MAIL\_CORRELATION\_ITEM\_NUM   -  Arbitrary gateway message
"correlation" text. This item is used by some gateways to correlate
the delivery report with the original message. Any text message may be placed
in this item. This item is of TYPE\_TEXT.  

  

      MAIL\_ORIGINALPATH\_ITEM\_NUM   -  Original routing path (copy of original
message's FromDomain).  

  

      MAIL\_DELIVER\_LOOPS\_ITEM\_NUM            -  Forwarding loop count.  

  

      MAIL\_DEAD\_FAILUREREASON\_ITEM\_NUM            -  Reason for dead mail
failure.  

  




**Description :**



These
symbolic constants define the codes (indexes) associated with mail note item
names.


 **Sample Usage :**


    /\* SendTo \*/  

    MailGetMessageItem (hMessage, MAIL\_SENDTO\_ITEM\_NUM, String,   

                                    MAXSPRINTF, &StringLength);  

  

    String[StringLength] = '\0';  

    printf ("\tTo: %s\n", String);  

  

    /\* CopyTo \*/  

    MailGetMessageItem (hMessage, MAIL\_COPYTO\_ITEM\_NUM, String,   

                                        MAXSPRINTF, &StringLength);  

    String[StringLength] = '\0';  

    printf ("\tCc: %s\n", String);  

  

    /\* From \*/  

    MailGetMessageItem (hMessage, MAIL\_FROM\_ITEM\_NUM, String,   

                                      MAXSPRINTF, &StringLength);  

    String[StringLength] = '\0';  

    printf ("\tFrom: %s\n", String);


 **See Also :**


**[MailAddHeaderItem](MailAddHeaderItem.md)**


**[MailAddHeaderItemByHandle](MailAddHeaderItemByHandle.md)**


**[MailGetMessageItem](MailGetMessageItem.md)**


**[MailGetMessageItemHandle](MailGetMessageItemHandle.md)**


**[MailReplaceHeaderItem](MailReplaceHeaderItem.md)**


**[MAIL\_xxx\_ITEM\_NUM(2)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9AB3CEDDDF02771B8525667A006D464F)**



----------------------------------------------------------------------------------------------------------


 





