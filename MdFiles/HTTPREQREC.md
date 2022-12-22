




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




**Initial Release 4.6**



**Data Type : Billing**



**HTTPREQREC** **-** Http Request
Record


**----------------------------------------------------------------------------------------------------------**



**#include
<billing.h>**



**Definition :**



typedef struct {  

   DWORD HttpContentLength;     /\* Content Length send/received


                             
     to/from client \*/  

   DWORD HttpReqTimeMs;         /\* Number of milliseconds to


                                  
process request \*/  

   DWORD HttpStatusCode;        /\* Status code returned by the


                                  
server \*/  

   WORD  HttpTimeStampOffset;   /\* Offset to http time stamp in a


                                  
string format \*/  

   WORD  HttpAuthUserOffset;    /\* Offset to Authenticated User


                                  
string \*/  

   WORD  HttpPartnerOffset;     /\* Offset to remote machine name


                                  
string \*/  

   WORD  HttpRefererOffset;     /\* Offset to refering URL string \*/  

   WORD  HttpServerAddrOffset;  /\* Offset to connection IP address \*/  

   WORD  HttpUserAgentOffset;   /\* Offset to user agent string \*/  

   WORD  HttpRequestLineOffset; /\* Offset to Request line string \*/  

   WORD  HttpContentTypeOffset; /\* Offset to content type string \*/  

/\* Time Stamp, AuthUser, Partner and other strings follow \*/  

} HTTPREQREC;


 


**Description :**



To create
Http Request billing records you must include the HttpRequest keyword in the
notes.ini BillingClass variable on the billing server.  This enables the server
to write http request-related information to the billing message queue which
can then be read to the HTTPREQREC structure by the billing server task.


 


For more
information about billing for Domino agents, see *Domino 5 Administration
Help.*



**Structure
Description**



**HttpContentLength** -- Length
of string representing content sent to/received from client


 


**HttpReqTimeMS** -- Number
fo milliseconds to process request


 


**HttpStatusCode** -- Status
code returned by the server


 


**HttpTimeStampOffset** -- Offset
to http timestamp string


 


**HttpAuthUserOffset** -- Offset
to Authenticated user string


 


**HttpPartnerOffset** -- Offset
to remote machine name string


 


**HttpRefererOffset** -- Offset
to refering URL string


 


**HttpServerAddrOffset** -- Offset
to connection IP address string


 


**HttpUserAgentOffset** -- Offset
to user agent string


 


**HttpRequestLineOffset** -- Offset
to Request line string


 


**HttpContentTypeOffset** -- Offset
to content type string


 


Note: All
offset members are relative to the beginning of the record
(&HttpContentLength), if an offset member is set to 0 the member is not
available.


 **See Also :**


**[AGENTREC](AGENTREC.md)**


**[BILLMSG](BILLMSG.md)**


**[BILLREC](BILLREC.md)**


**[DBREC](DBREC.md)**


**[DOCUMENT](DOCUMENT.md)**


**[MAILREC](MAILREC.md)**


**[REPLREC](REPLREC.md)**


**[SESSIONREC](SESSIONREC.md)**



----------------------------------------------------------------------------------------------------------


 





