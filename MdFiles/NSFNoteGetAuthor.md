




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




**Initial Release 4.0**



**Function : Note**



**NSFNoteGetAuthor** **- Return
the author of the note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteGetAuthor(**  

      NOTEHANDLE  hNote,  

      char far \*retName,  

      WORD far \*retNameLength,  

      BOOL far \*retIsItMe**);**



**Description :**



Given a
handle to an open note, return the first author item for the note.  If the
pointer argument retIsItMe is non-NULL, this routine will also compare the
author item to the current user's name, and store the result at that address.


 


**Parameters :**



Input :  

hNote  -  Handle to an open note.  

  




Output :  

(routine)  -  Return status from this call:  

  

NOERROR - Success  

  

ERR\_ITEM\_NOT\_FOUND - No author was found for this note.  

  

ERR\_xxx - Errors returned by lower level Notes functions: (memory management,
file operations, network errors, etc.).  There are so many possible causes,
that it is best to use the code in a call to OSLoadString and display/log the
error for the user as your default error handling.  

  

  

retName  -  Optional - if not NULL, the first author item is written to this
address.  retName is not null-terminated.  

  

retNameLength  -  Number of bytes in the first author item.  

  

retIsItMe  -  Optional - if this pointer is non-NULL, TRUE is stored if the
author item is the same as the current user, FALSE if not.  

  




 **See Also :**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





