




<!--
 /\* Font Definitions \*/
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




**Initial Release 8.5.2**



**Function : OOO**



**OOOGetState** **- This
function returns the version (agent, service) and the state (disabled, enabled)
of the out of office functionality.**


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOGetState(**  

      OOOCTXPTR \*pOOOContext,  

      WORD \*retVersion,  

      WORD \*retState**);**



**Description :**



This
function returns the version (agent, service) and the state (disabled, enabled)
of the out of office functionality.The version information can be used to show
or hide UI elements that might not be supported for a given version.  For
example, the agent does not support durations of less than 1 day and some
clients might choose not to show the hours in the user interface.When you need
to make OOOGetState as efficient as possible, call OOOStartOperation with the
home mail server and the handle to the opened mail database. This function is
read only and does not return an error if user ACL rights are below Editor
(which are required to turn on/off the Out of office functionality).If 
OOOGetState is called immediately following OOOEnable it will not reflect the
state set by the OOOEnable.   To see the current state call OOOEndOperation and
start a new operation  using OOOStartOperation, OOOGetState, OOOEndOperation.


 


**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

NOERROR - Successfully perform this function.  

This function can return Domino errors.  

OOO specific errors:  

ERR\_OOO\_MISSING\_INIT - OOOGetState was called prior to OOOInit()  

ERR\_OOO\_MISSING\_PARAM - One or more mandatory parameters were not specified  

ERR\_OOO\_MISSING\_MAILFILE - Mailfile information is not specified  

  

  

retVersion  -  The address of a WORD into which the version number is returned.  

Required parameter.  

Values for retVersion  

#define            OOO\_CONFIG\_AGENT           1  

#define OOO\_CONFIG\_SERVICE                     2  

  

retState  -  The address of a WORD into which the version number is returned.  

Optional parameter. Pass in NULL if not interested in this information.  

Values for retState  

#define OOO\_STATE\_ENABLED                      1  

#define OOO\_STATE\_DISABLED                     0  

  




 **See Also :**


**[OOOEndOperation](OOOEndOperation.md)**


**[OOOStartOperation](OOOStartOperation.md)**



----------------------------------------------------------------------------------------------------------


 





