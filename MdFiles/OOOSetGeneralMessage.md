




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



**OOOSetGeneralMessage** **- This
function sets general message messages**


**----------------------------------------------------------------------------------------------------------**



**#include <oooapi.h>**



STATUS
LNPUBLIC **OOOSetGeneralMessage(**  

      OOOCTXPTR \*pOOOContext,  

      Const char \*pGeneralMessage,  

      WORD  wGeneralMessageLen**);**



**Description :**



OOO supports
two sets of notification messages.  They are called General message/subject and
Special message/subject. 


The
following text is always appended to the body of the message, where the
"Message subject" is obtained from the message which caused the
notification to be generated.**"Note: This is an automated
response to your message "****Message subject"** **sent on** **2/12/2009
10:12:17 AM****. This is the only notification you will receive while this person
is away.**"     


 


**Parameters :**



Input :  

pOOOContext  -  pointer obtained from the OOOStartOperation call  

  

pGeneralMessage  -  The text of the general message, the text may contain nulls.
The caller is  responsible for allocating and freeing this memory  

  

wGeneralMessageLen  -  The length of the text of the the general message.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   

NOERROR - Successfully performed this operation  

  

  




 **See Also :**


**[OOOGetGeneralMessage](OOOGetGeneralMessage.md)**



----------------------------------------------------------------------------------------------------------


 





