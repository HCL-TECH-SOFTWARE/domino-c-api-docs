




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



**FilterReturnCode** **-** DSAPI Values
returned from a filter event


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


   kFilterNotHandled =
0,


  
kFilterHandledRequest = 1,


   kFilterHandledEvent
= 2,


   kFilterError = 3


} FilterReturnCode;


 


**Description :**



Return value
set when the filter has completed.  For each event the filter is handling, a
return value must be sent to signify further action.  The values to return are
defined below.


 


kFilterNotHandled               -
signals that the filter did not process the event.


kFilterHandledRequest        -
signals that the http request has completly been processed by the filter. A
response has already been sent to the client, and the http stack must terminate
the processing of the request.


kFilterHandledEvent            -
signals that the event has been handled by the filter, but further processing
is to take place to completly service the http request.


kFilterError                         -
signals that the filter encountered and error while processing the event. In
this case the http stack is to stop processing the request, and send an
appropriate error response to the user.


 **See Also :**


**[DSAPI\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AE031231D689E71785256A6800499C37)**



----------------------------------------------------------------------------------------------------------


 





