




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




**Initial Release 4.5**



**Function : Item (Field)**



**NSFItemGetModifiedTimeByBLOCKID** **- Get the
last modified time for an item, given the item's BLOCKID.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemGetModifiedTimeByBLOCKID(**  

      DHANDLE  hNote,  

      BLOCKID  bhItem,  

      DWORD  Flags,  

      TIMEDATE \*retTime**);**



**Description :**



Find an item
with a given BLOCKID and return the time it was last modified. The BLOCKID can
easily be found using the call NSFItemInfo.


 


**Parameters :**



Input :  

hNote  -  The note handle.  If this handle is NULLHANDLE, then the retTime
argument is cleared (TimeDateClear is performed on retTime) and
NSFItemGetModifiedTimeByBLOCKID returns NOERROR.  

  

bhItem  -  The BLOCKID for the item we are interested in.  

  

Flags  -  Reserved for future use.  Must be set to 0L.  

  




Output :  

(routine)  -  NOERROR - Successfully got the last modified time  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

retTime  -  Time that the item was last updated to the note.  

  




 **See Also :**


**[NSFItemGetModifiedTime](NSFItemGetModifiedTime.md)**



----------------------------------------------------------------------------------------------------------


 





