




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



**DBREC** **-** Database
Billing Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef struct {  

   SESSIONID SessionID;            

   WORD Action;                    

   char Username[MAXUSERNAME+1];   

   DWORD DBOpenTime;               

   TIMEDATE ReplicaID;             

} DBREC;


 


**Description :**



To create
Database billing records, you must include the Database keyword in the
notes.ini BillingClass variable on the billing server. This enables the server
to write database-related information to the billing message queue which can
then be read into the DBREC structure by a Billing add-in server task.


 


For more
information about billing for database activity, see the *Domino 5
Administration Help* database*.*




**Structure
Description**



**SessionID** --
Identifier (ID) of the Domino or Notes session established  by the Notes
workstation or Domino server that initiated the billing activity, such as
opening a database.


 


**Action** --  Type of
session activity at the time the billing record occurs.  Database billing
records are written for each of the following activity states:


 


BILL\_DB\_STAMP
-- Indicates that the database is active with such activities as document
editing and saving, and access control list updates.  The frequency of issuance
of this record depends on the BillingSuppressTime notes.ini variable.  A
billing database stamp occurs if the timer specified by BillingSuppresTime
expires and there is database activity only. The default is 15 minutes. 


 


BILL\_DB\_OPEN
-- Indicates that the database is open.  Billing records are not generated for
opening data directories.


 


BILL\_DB\_CLOSE
- Indicates a user or server request to close the database.  The database is
not actually closed until the session terminates and a  BILL\_DB\_CLOSE\_END is
issued.  A Lotus Domino Server may not permanently close the database until the
user session has ended. This can happen when the server anticipates heavy usage
of a database.  In this way, if a database is opened and closed multiple times
within a single session, the open time between each open/close action can be
easily calculated.


 


BILL\_DB\_CLOSE\_END
- Indicates a database is closed at session end.


 


**Username** --
Authenticated name of the user who initiated the session.


 


**DBOpenTime** -- Elapsed
time that a database is open during the session. When a database is opened
multiple times within a session, a cumulative value is recorded for the
session.


 


**ReplicaID** -- Unique
replica ID of the open database.


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_xxx (actions)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6A3C76AFC8056835852563010073FD5F)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





