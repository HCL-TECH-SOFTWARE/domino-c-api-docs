




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




**Initial Release 6**



**Data Type : DSAPI**



**FilterParsedRequestLine** **-** Data1 for
DSAPI server support function kGetParsedRequest


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef struct{  

    char    \*pRawUri;  

    char    \*pPathUri;  

    char    \*pQueryUri;  

    char    \*pFragmentUri;


    char    \*pSchemeUri;  

    char    \*pHostInfoUri;  

    char    \*pHostName;  

    int     hostPort;


    char    \*pUserUri;  

    char    \*pUserPasswordUri;


    int     majorProtocolVersion;  

    int     minorProtocolVersion;  

}FilterParsedRequestLine;


 


**Description :**



The
FilterParsedRequestLine structure is used by the ServerSupport callback
functionality of the FilterContext.  see FilterContext for more information


 


pRawUri                             -
(Input)  Pointer to the raw uri from the input request line.


pPathUri                             -
(Input)  Pointer to the path uri in the input request line.


pQueryUri                           -
(Input)  Pointer to the query string from the input request line.


pFragmentUri                     -



pSchemeUri                        -



pHostInfoUri                       -
(Input)  Pointer to the part with the host name in the url.


pHostName                        -
(Input)  Pointer to the host name after we have parsed the request line.


hostPort                             -
(Input)  The host port number the request came in.


pUserUri                             -
(Input)  Pointer to the user name from the input request line. It is set to
NULL is none is provided.


pUserPasswordUri              -
(Input)  Pointer to the user's password from the request input line. it is set
to NULL if none was provided.


majorProtocolVersion          -
(Input)  The major version number of the http protocol used for the request.


minorProtocolVersion          -
(Input)  The minor version number of the http protocol used for the request.


 


 **See Also :**


**[FilterContext](FilterContext.md)**


**[ServerSupportTypes](ServerSupportTypes.md)**



----------------------------------------------------------------------------------------------------------


 





