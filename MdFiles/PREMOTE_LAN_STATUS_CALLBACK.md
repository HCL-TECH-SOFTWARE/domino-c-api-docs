




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




**Initial Release 4.5**



**Data Type : Remote LAN adapter**



**PREMOTE\_LAN\_STATUS\_CALLBACK** **-** Calling
convention for remote LAN service product adapter callback function.


**----------------------------------------------------------------------------------------------------------**



**#include
<net.h>**



**Definition :**



typedef BOOL
(LNCALLBACKPTR PREMOTE\_LAN\_STATUS\_CALLBACK)(


   WORD Action,


   STATUS status,


   char \*pErrText);


 


**Description :**



This typedef
defines the interface to a status callback routine for a remote LAN service
product adapter.  Notes hands the address of this routine to the initialization
function of the LAN service product.  The LAN service product calls this
routine to report ongoing status back to Notes and for Notes to display this
status information.  It also checks for a user abort condition (e.g.  ctl+break
for a PC, or command-period for a Macintosh).


 


Inputs:


            Action               The
type of operation needed. See REMOTE\_LAN\_xxx for possible values.


 


            StatusCode       A
Remote LAN status code, if  type is  REMOTE\_LAN\_DISPLAY\_STATUS.  See
REMOTE\_LANT\_STATUS\_xxx for possible codes.


 


            pErrText       
           The error string, if  type is  REMOTE\_LAN\_DISPLAY\_ERROR\_TEXT.  

  




Outputs:


(routine)           The
return argument is of type BOOL.  This is used to return an abort condition if
one has occurred.  It should be TRUE (1) if operation should continue, and
FALSE (0) if the user has asked for an abort (e.g. ctl+break for a PC, or
command-period for a Macintosh).


 **See Also :**


**[PREMOTE\_LAN\_SERVICE\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CE85C1F5D2E0248085256361003C3CC9)**


**[REMOTE\_LAN\_STATUS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B5DBC1F192673C8985256361003FD569)**



----------------------------------------------------------------------------------------------------------


 





