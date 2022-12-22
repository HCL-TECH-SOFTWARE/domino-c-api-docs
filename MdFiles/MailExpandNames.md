




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Mail Gateway**



**MailExpandNames** **- Expands
all groups in a recipient text list.**


**----------------------------------------------------------------------------------------------------------**



**#include <mailserv.h>**



STATUS
LNPUBLIC **MailExpandNames(**  

      DHANDLE  hWorkList,  

      WORD  WorkListSize,  

      DHANDLE far \*hOutputList,  

      WORD far \*OutputListSize,  

      BOOL  UseExpanded,  

      DHANDLE  hRecipsExpanded**);**



**Description :**



This
function expands all groups in a recipient text list.


 


**Parameters :**



Input :  

hWorkList  -  Handle of recipient text list to be expanded.  It is assumed that
the recipient text list is prefixed with a WORD containing the Domino data type
and resides in the local directory.  

  

WorkListSize  -  Size of recipients list.  

  

UseExpanded  -  TRUE if this function is to use and update the hRecipsExpanded
list, otherwise FALSE.  

  

hRecipsExpanded  -  Handle to a global text list of recipient group names that
have already been expanded so that these groups will not be expanded again by
this function.  Used only if UseExpanded is TRUE.  If UseExpanded is FALSE, use
NULLHANDLE for this argument.  

  




Output :  

(routine)  -   Return status from the call -- indicates either success
(NOERROR) or what the error is.  

  

  

hWorkList  -  This list is deallocated, even on error conditions.  

  

hOutputList  -  Pointer to returned handle to the new list.  The caller is responsible
for releasing this memory using OSMemFree.  

  

OutputListSize  -  Pointer to returned size of the new list.  

  

hRecipsExpanded  -  The updated text list that reflects any new expansions. 
Used only if UseExpanded is TRUE.  

  




 **See Also :**


**[MailAddRecipientsItem](MailAddRecipientsItem.md)**


**[MailDeleteMessageRecipient](MailDeleteMessageRecipient.md)**


**[MailGetMessageRecipient](MailGetMessageRecipient.md)**



----------------------------------------------------------------------------------------------------------


 





