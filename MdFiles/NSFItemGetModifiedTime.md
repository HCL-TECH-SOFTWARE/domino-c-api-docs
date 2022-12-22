




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



**NSFItemGetModifiedTime** **- Get the
last modified time for an item.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemGetModifiedTime(**  

      DHANDLE  hNote,  

      const char \*ItemName,  

      WORD  ItemNameLength,  

      DWORD  Flags,  

      TIMEDATE \*retTime**);**



**Description :**



Find the
first item of the given name in a note and return its last modified time.


 


**Parameters :**



Input :  

hNote  -  The note handle.  If this handle is NULLHANDLE, then the retTime
argument is cleared (TimeDateClear is performed on retTime) and
NSFItemGetModifiedTime returns NOERROR.  

  

ItemName  -  The item name.  

  

ItemNameLength  -  The length of the item name or MAXWORD for null terminated
strings.  

  

Flags  -  Reserved for future use.  Must be set to 0L.  

  




Output :  

(routine)  -  NOERROR - Successfully got the time the item was last modified.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

retTime  -  Time that the item was last updated to the note.  

  




 **See Also :**


**[NSFItemGetModifiedTimeByBLOCKID](NSFItemGetModifiedTimeByBLOCKID.md)**



----------------------------------------------------------------------------------------------------------


 





