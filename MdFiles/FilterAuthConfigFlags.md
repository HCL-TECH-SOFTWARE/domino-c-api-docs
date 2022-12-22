




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



**FilterAuthConfigFlags** **-** DSAPI
FilterAuthenticate authFlags


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


  
kAuthAllowBasic         = 1,


  
kAuthAllowAnonymous     = 2,


  
kAuthAllowSSLCert       = 4,


  
kAuthAllowSSLBasic      = 8,


  
kAuthAllowSSLAnonymous  = 16,


  
kAuthRedirectToSSL      = 32


}
FilterAuthConfigFlags;


 


**Description :**



The
authentication options enabled for the server.  The values for a server can be
found under the Internet Ports section within the server document.  The values
can be added together.


 


kAuthAllowBasic                 -
The server allows basic authentication by providing a user name and password.


kAuthAllowAnonymous        -
The server allows anonymous access to public (non protected) documents.


kAuthAllowSSLCert             -
The server allows SSL authentication using an SSL client certificate.


kAuthAllowSSLBasic           -
The server allows SSL authentication by providing a user name and password.


kAuthAllowSSLAnonymous  -
The server allows anonymous SSL authentication to public (non protected)
documents.


kAuthRedirectToSSL           -
The server allows redirections to SSL authentication for documents that are SSL
protected.


 **See Also :**


**[FilterAuthenticate](FilterAuthenticate.md)**



----------------------------------------------------------------------------------------------------------


 





