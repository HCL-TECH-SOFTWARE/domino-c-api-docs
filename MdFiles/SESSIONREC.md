




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.0**



**Data Type : Billing**



**SESSIONREC** **-** Session
Billing Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**





typedef struct {  

   SESSIONID SessionID;            

   WORD Action;                    

   char Username[MAXUSERNAME+1];   

   DWORD BytesIn;                

   DWORD BytesOut;                

   char NetAdr[MAXNETADR];         

} SESSIONREC;


 


**Description :**



To create
Session billing records, you must include the Session keyword in the notes.ini
BillingClass variable on the billing server. This enables the server to
generate billing records related to network activity for each database session
on that server.   The billing server writes this information to the billing
message queue where it can be read into the SESSREC structure by a billing
add-in server task.


For more
information about billing for Domino sessions, see the *Administrating the
Domino System* documentation.


 


**Structure
Description**



**SessionID -**  Unique
identifier (ID) for the user session. 


 


**Action -**  State of
the session.   There are three types of billing records. 


 


BILL\_SESSION\_START
-  Written when a user or server initiates database activity for the first
time.


 


BILL\_SESSION\_STAMP
-  Periodically written for basic session activities, such as opening a
database or editing documents in the database.   The frequency of issuance of
the stamp is controlled by the BillingSuppressTime variable in the notes.ini
file.  The default is 15 minutes.  This record is not written if the session is
idle.  


 


BILL\_SESSION\_END
-  Written when a workstation or server closes the session.  


 


**Username** - 
Authenticated name of the user for this session.  



**BytesIn -**  Snapshot
of the number of bytes received over the network by the server for the session
thus far.  This is a cumulative value that is updated each time a stamp record
occurs during the session.  The value is considered final when the server
generates the  BILL\_SESSION\_END record.  The  value includes any client/server
network overhead in addition to the session data.


 


**BytesOut** -  Snapshot
of the number of bytes sent over the network by the server for the session thus
far.  This is a cumulative value that is updated each time a stamp record
occurs during the session.  The value is considered final when the server
generates the  BILL\_SESSION\_END record.  The  value includes any client/server
network overhead in addition to the session data.


 


**NetAdr -**  Network IP
address of the client that initiated the session. 


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_xxx (actions)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6A3C76AFC8056835852563010073FD5F)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**



----------------------------------------------------------------------------------------------------------


 





