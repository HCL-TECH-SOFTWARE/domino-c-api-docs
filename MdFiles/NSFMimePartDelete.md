




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




**Initial Release 7.0.2**



**Function : MIME**



**NSFMimePartDelete** **- delete a
TYPE\_MIME\_PART item from a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfmime.h>**



STATUS
LNPUBLIC **NSFMimePartDelete(**  

      NOTEHANDLE  hNote,  

      char \*pchItemName,  

      WORD  wItemNameLen**);**



**Description :**



The function
NSFMimePartDelete deletes the TYPE\_MIME\_PART items named pchItemName from an
open note.  NSFMimePartDelete does not delete the object associated with a
given TYPE\_MIME\_PART item if the object is shared. 


 


 


**Parameters :**



Input :  

hNote  -  a handle to an open note.  

  

pchItemName  -  a pointer to the TYPE\_MIME\_PART item name.  

  

wItemNameLen  -  the length of the item name.  

  




Output :  

(routine)  -   Return status from this call.  

     NOERROR - Successfully added the MIME part.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


    STATUS error;


 


if (error =
NSFMimePartDelete(hNote, MAIL\_BODY\_ITEM, sizeof(MAIL\_BODY\_ITEM)-1)) {


        goto exit;


}


 


 **See Also :**


**[NSFMimePartAppend](NSFMimePartAppend.md)**



----------------------------------------------------------------------------------------------------------


 





