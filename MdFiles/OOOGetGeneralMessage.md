




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



**OOOGetGeneralMessage** **- This
function gets general message messages**


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOGetGeneralMessage(**  

      OOOCTXPTR \*pOOOContext,  

      char \*pGeneralMessage,  

      WORD \*pGeneralMessageLen**);**



**Description :**



OOO supports
two sets of messages.  They are called General message/subject and Special
message/subject.


This is
function returns the handle to the text of the general message and the size of
the memory containing the message.  


 


**Parameters :**



Input :  

pOOOContext  -  Pointer obtained from the OOOStartOperation call  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

NOERROR - Successfully performed this operation  

  

  

pGeneralMessage  -  The text of the general message, the text may contain
nulls. This is not a null terminated string, use pGeneralMessageLen  to determine
size. The caller is responsible for allocating and freeing this memory.  This
is an optional parameter. Pass in NULL pointer if you want to receive just the
size information.  

  

pGeneralMessageLen  -  The length of the text of the general message.  If 
pGeneralMessage is not specified this is an ouput parameter. If pGeneralMessage
is specified it is input/output parameter.  It specifies the maximum size of
the returned text, and is updated if we have less text than the buffer size.  

  




 **See Also :**


**[OOOSetGeneralMessage](OOOSetGeneralMessage.md)**



----------------------------------------------------------------------------------------------------------


 





