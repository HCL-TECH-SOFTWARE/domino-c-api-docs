




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



**Data Type : Billing; Replication**



**REPLREC** **-** Replication
Billing Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef struct {  

   SESSIONID SessionID;   

   DWORD     BytesIn;    

   DWORD     BytesOut;    

   TIMEDATE  ReplicaID;  

   char      Source[MAXUSERNAME+1];  

   char      Destination[MAXUSERNAME+1];  

   WORD      Priority;    

} REPLREC;


 


**Description :**



To create
Replication billing records, you must include the Replication keyword in the
notes.ini BillingClass variable on the billing server. This enables the server
to generate billing records for replication activity initiated by that server. 
This information is written to the billing message queue and can be read into
the REPLREC structure by a billing add-in server task.


 


**Structure
Description**



**SessionID -**  Unique
identifier (ID) for the user session. 



**BytesIn -**  Number of
bytes read by the server from the network during replication of a database.
This value is cumulative. Each database replication event updates the value. 


 


**BytesOut -**  Number of
bytes written by the server to the network during replication of a database. 
This value is cumulative. Each database replication event updates the value. 


 


**ReplicaID -**  Replica ID
of the database associated with the replication event.


 


**Source -**  Name of
the server that contains the replicated database.


 


**Destination
-**  Name of the server that contains the destination replica.   



**Priority -**  Priority
of the replication event, obtained from the connection record in the  Domino
Directory. The values are Low, Medium, and High.


 


**Notes:**


Domino does
not generate replication billing records for replications performed by the
Cluster Replicator.  Only standard Domino replication events generate
replication billing records.  For more information, see the *Administering
the Domino System* documentation.


 


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[BILL\_xxx (actions)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6A3C76AFC8056835852563010073FD5F)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[HTTPREQREC](HTTPREQREC.md)**


**[MAILREC](MAILREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





