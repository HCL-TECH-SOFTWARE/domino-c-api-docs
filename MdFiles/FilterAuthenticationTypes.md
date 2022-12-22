




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



**FilterAuthenticationTypes** **-** DSAPI
FilterAuthenticate authType


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


  
kNotAuthentic         = 0,


  
kAuthenticBasic       = 1,


  
kAuthenticClientCert  = 2


}
FilterAuthenticationTypes;


 


**Description :**



The type of
authorization.  If the filter handles this event, the filter must set authType
within the FilterAuthenticate structure to one of these values.


 


kNotAuthentic                     -
User's credentials failed authentication. The http stack must terminate the
processing of the request. 


kAuthenticBasic                  -
User's name and password has passed authentication. The authentication phase
should be terminated, and the next phase in the processing of the request
started.


kAuthenticClientCert           -
The SSL authentication using an SSL client certificate has succeeded. The
authentication phase should be terminated, and the next phase in the processing
of the request started.


 **See Also :**


**[FilterAuthenticate](FilterAuthenticate.md)**



----------------------------------------------------------------------------------------------------------


 





