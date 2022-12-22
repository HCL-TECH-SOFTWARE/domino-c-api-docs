




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




 


**Symbolic Value : Item (Field)
Information**



**TYPE\_xxx [USERID]** **-** Item Data
Type - V1/V2 Author


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**



**Description :**



Notes V1/V2
Author fields contain a text user name followed by an 8 byte license ID. Notes
2.1 and earlier created items of TYPE\_USERID when saving data from a field
designed as data type "Document Author".  Notes 3.0 and later no
longer uses the "Document Author" data type, or the item type
TYPE\_USERID.  

  

In an item of TYPE\_USERID, all but the last 8 bytes of the structure contains
the user name, which may be printed as text.  The last 8 bytes contain the
license ID, as follows:  

  




typedef
struct {  

   char      Author[sizeof(user\_name)];  

   LICENSEID License;  

} V1V2\_Author;


  

You may obtain the user name and license ID from SECKFMUserInfo.  The user name
text may optionally contain the name of the user plus a list of server names in
parentheses.  

  

Notes 3.0 or later recognizes items of TYPE\_USERID as a Notes V1/V2 Author,
field but does not save items with this type.


 **Sample Usage :**


   STATUS      error;  

    char        szDocAuthor[MAX\_USERNAME\_LEN];  

    LICENSEID   License;  

    char        achUSERID[MAX\_USERNAME\_LEN + sizeof(LICENSEID)];  

  

    /\* Get Current UserID and store it \*/  

    if (error = SECKFMUserInfo(KFM\_ui\_GetUserInfo,  

                           szDocAuthor,&License))  

    {  

        printf ("Error: unable to get info about current user.\n");  

        return (error);  

    }  

                  

    memcpy(achUSERID, szDocAuthor, strlen(szDocAuthor));  

    memcpy(&achUSERID[strlen(szDocAuthor)],&License,  

                       sizeof(LICENSEID));  

  

    if (error = NSFItemAppend(hNote,ITEM\_SUMMARY,  

                        "From", strlen("From"),  

                        TYPE\_USERID, achUSERID,  

                        (DWORD) (strlen(szDocAuthor) +  

                        sizeof(LICENSEID))))  

    {  

        printf ("Error: unable to set From item in note.\n");  

        return (error);  

    } 


 **See Also :**


**[ITEM\_xxx [NAMES]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/557B87BE33862F688525623800493995)**


**[ITEM\_xxx [READERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0134426255B7EE1885256238004A727D)**


**[ITEM\_xxx [READWRITERS]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C2175B1F1F4585C4852562380049DF01)**


**[NAMES\_LIST](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/009F0044002000E285255E3F0001744B)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





