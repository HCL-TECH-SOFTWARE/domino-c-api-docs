




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




**Initial Release 5.0.3**



**Data Type : DSAPI**



**RequestMethod** **-** DSAPI 
Incoming HTTP request


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


    kRequestNone              =
0,  

    kRequestHEAD           = 1,  

    kRequestGET            = 2,  

    kRequestPOST           = 3,  

    kRequestPUT            = 4,  

    kRequestDELETE         = 5,  

    kRequestTRACE          = 6,  

    kRequestCONNECT        = 7,  

    kRequestOPTIONS        = 8,  

    kRequestUNKNOWN        = 9,  

    kRequestBAD            = 10


} RequestMethod;


 


 


**Description :**



This structure
defines the supported HTTP Request Methods within a FilterRequest.  


 


kRequestNone                    -
No HTTP request method is provided.


kRequestHEAD                  -
method is often used for testing hypertext links for validity, accessibility,
and recent modification


kRequestGET                     -
GET method - used to retrieve whatever information (in the form of an entity)
is identified by the Request-URL


kRequestPOST                  -
POST method - requests that the origin server accept the entity enclosed in the
request as a new subordinate of the resource identified by the Request-URL in
the Request-Line


kRequestPUT                     -
PUT method - requests that the enclosed entity be stored under the supplied
Request-URL


kRequestDELETE               -
DELETE method - requests that the origin server delete the resource identified
by the Request-URL


kRequestTRACE                -
TRACE method


kRequestCONNECT           -
CONNECT method


kRequestOPTIONS            -
OPTIONS method


kRequestUNKNOWN          -
Unknown request method.


kRequestBAD                     -
Bad request method. Error.


 **See Also :**


**[FilterRequest](FilterRequest.md)**



----------------------------------------------------------------------------------------------------------


 





