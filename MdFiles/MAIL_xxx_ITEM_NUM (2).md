




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




**Initial Release 5.0**



**Symbolic Value : Mail Gateway**



**MAIL\_xxx\_ITEM\_NUM(2)** **-** Mail note
item name codes.


**----------------------------------------------------------------------------------------------------------**



**#include <mail.h>**


 **Symbolic Values :**      MAIL\_SMTPORIGINATOR\_ITEM\_NUM        -  SMTP Originator  

  

      MAIL\_INETTO\_ITEM\_NUM   -  List of internet recipient names to send the
message to.  

  

      MAIL\_INETCC\_ITEM\_NUM   -  List of internet recipient names to send copies
to.  

  

      MAIL\_INETBCC\_ITEM\_NUM            -  List of internet recipient names to
send blind copies to.  

  

      MAIL\_ALTTO\_ITEM\_NUM    -  List of alternate recipient names to send the
message to.  

  

      MAIL\_ALTCC\_ITEM\_NUM    -  List of alternate recipient names to send
copies to.  

  

      MAIL\_ALTBCC\_ITEM\_NUM              -  List of alternate recipient names to
send blind copies to.  

  

      MAIL\_DONOTHOLD\_ITEM\_NUM      -  Do not hold this message.  

  

      MAIL\_STORAGETO\_ITEM\_NUM      -  Storage type for INETTO.  

  

      MAIL\_STORAGECC\_ITEM\_NUM      -  Storage type for INETCC.  

  

      MAIL\_STORAGEBCC\_ITEM\_NUM    -  Storage type for INETBCC.  

  

      MAIL\_LANGTO\_ITEM\_NUM             -  Language tag for INETTO  

  

      MAIL\_LANGCC\_ITEM\_NUM             -  Language tag for INETCC  

  

      MAIL\_LANGBCC\_ITEM\_NUM           -  Language tag for INETBCC  

  

      MAIL\_INETFROM\_ITEM\_NUM         -  Internet originator.  

  

      MAIL\_SMTP\_DSN\_RCPTS\_ITEM\_NUM        -  SMTP Delivery Status Notification
Receipts.  

  

      MAIL\_JOURNAL\_FLAG\_ITEM\_NUM             -  $JournalResponsibility flag.  

  




**Description :**



These
symbolic constants define additional codes (indexes) associated with mail note
item names.


 **See Also :**


**[MailAddHeaderItem](MailAddHeaderItem.md)**


**[MailAddHeaderItemByHandle](MailAddHeaderItemByHandle.md)**


**[MailGetMessageItem](MailGetMessageItem.md)**


**[MailGetMessageItemHandle](MailGetMessageItemHandle.md)**


**[MailReplaceHeaderItem](MailReplaceHeaderItem.md)**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**



----------------------------------------------------------------------------------------------------------


 





