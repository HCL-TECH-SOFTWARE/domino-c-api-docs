




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



**MailGetMessageItemTimeDate** **- Returns
the value of a time/date header item.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailGetMessageItemTimeDate(**  

      DHANDLE  hMessage,  

      WORD  ItemCode,  

      TIMEDATE far \*retTimeDate**);**



**Description :**



This
function returns the value of a time/date header item.


 


**Parameters :**



Input :  

hMessage  -  Open message handle.  

  

ItemCode  -  Item code:  MAIL\_COMPOSEDDATE\_ITEM\_NUM,
MAIL\_DELIVEREDDATE\_ITEM\_NUM, MAIL\_DELIVERYDATE\_ITEM\_NUM,
MAIL\_POSTEDDATE\_ITEM\_NUM  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

retTimeDate  -  Time/date.  

  




 **Sample Usage :**


        /\* PostedDate
\*/  

        MailGetMessageItemTimeDate(hMessage, MAIL\_POSTEDDATE\_ITEM\_NUM, &Time);  

        ConvertTIMEDATEToText(NULL, NULL, &Time, String,   

                                    sizeof(String), &StringLength);  

        String[StringLength] = '\0';  

        printf("\tDate: %s\n", String);  

  




 **See Also :**


**[MAIL\_xxx\_ITEM\_NUM(1)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255CF1005E1A42)**



----------------------------------------------------------------------------------------------------------


 





