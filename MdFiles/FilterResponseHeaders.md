




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



**FilterResponseHeaders** **-** DSAPI
FilterContext / ServerSupport Filter Response Headers


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef struct {


   unsigned int  
responseCode;


   char\*         
reasonText;


   char\*         
headerText;


}
FilterResponseHeaders;


 


**Description :**



The
FilterResponseHeaders structure is used by the ServerSupport callback
functionality of the FilterContext.  see FilterContext for more information.


 


responseCode        -
(Output)  Set to the http status code to send back to the client.


reasonText             -
(Output)  Set to the reason response text to add to the response line. It can
be set to NULL if none is available.


headerText             -
(Output)  Points to a buffer of response http headers to append to the default
response headers if any. Can be set to NULL, if no headers are to be appended.
If not NULL, each header must be terminated by a carriage return and line feed
characters ("\r\n"), and the whole sequence of headers must end with
two "\r\n" sequence.


 **See Also :**


**[FilterContext](FilterContext.md)**


**[ServerSupportTypes](ServerSupportTypes.md)**



----------------------------------------------------------------------------------------------------------


 





