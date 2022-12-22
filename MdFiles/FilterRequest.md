




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



**FilterRequest** **-** DSAPI
Request information within a FilterContext


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef struct {


   unsigned int  
method;


   char\*          URL;


   char\*         
version;


   char\*         
userName;


   char\*         
password;


   unsigned char\*
clientCert;


   unsigned int  
clientCertLen;


   char\*         
contentRead;


   unsigned int  
contentReadLen;


} FilterRequest;


 


**Description :**



A GetRequest
within a FilterContext can be called to retrieve request line (first line of
request) information and reports on other information as the request is
processed. The first line of an HTTP request has this syntax: <method>
<url> <version>. For example, "GET /sales.nsf?OpenDatabase HTTP/1.0".


 


method                   -
The type of HTTP request, see RequestMethod


URL                       -
The <url> part of the request line.


version                   -
The <version> part of the http protocol.


userName               -
The user's web name or NULL if not present.


password                -
The user's web password or NULL, if not present.


clientCert                -
The user's SSL client certificate or NULL if not present.


clientCertLen          -
The number of bytes in the user's SSL client certificate, or 0 if not present.


contentRead           -
The buffer containing the post data already read, NULL is no post data has been
read.


contentReadLen      -
The number of bytes of post data available, 0 if none is present.


 


 


 **See Also :**


**[FilterContext](FilterContext.md)**


**[RequestMethod](RequestMethod.md)**



----------------------------------------------------------------------------------------------------------


 





