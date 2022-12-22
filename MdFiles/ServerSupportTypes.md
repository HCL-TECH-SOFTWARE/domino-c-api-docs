




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



**ServerSupportTypes** **-** DSAPI Server
support function types.


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


        kWriteResponseHeaders         =
1,


        kOwnsRequest                  =
2,


        kGetParsedRequest                     =
3,


        kWrite102Processing           =
4,


        kGetAuthenticatedUserInfo     =
5


}
ServerSupportTypes;


 


**Description :**



Server
support function types can be specified within the ServerSupport functionality
defined within a FilterContext for a DSAPI filter. 


 


funcType
indicates the service to be performed. Possible values are:


kWriteResponseHeaders     -
Write response status code, reason text, and headers to the client.


kOwnsRequest                   -
Claims ownership of the http request. Only the filter that claims ownership of
the request will get notified of events from then on forward, and only the
filter (no default processing of the request) is to process the request, i.e,
the filter better be prepared to handle the event kFilterProcessRequest and
generate the response data for the client.


kGetParsedRequest            -
Retreives the components of the parsed request.


kWrite102Processing          -



kGetAuthenticatedUserInfo  -
Get the authenticated user information including his/her web user name,
password, group list, cannonical user name... Note that this service is only
valid after the authentication phase has taken place for web user name,
password, and cannonical name (the web user name and password will not be available
before authentication has taken place in the case of session authentication.)
The user's group list will not be available until the user's group list
generation phase has taken place.


 **See Also :**


**[FilterAuthenticatedUser](FilterAuthenticatedUser.md)**


**[FilterContext](FilterContext.md)**


**[FilterParsedRequestLine](FilterParsedRequestLine.md)**


**[FilterResponseHeaders](FilterResponseHeaders.md)**



----------------------------------------------------------------------------------------------------------


 





