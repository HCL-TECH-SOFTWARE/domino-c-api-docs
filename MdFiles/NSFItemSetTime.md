




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Function : Item (Field)**



**NSFItemSetTime** **- Append an
Item of TYPE\_TIME to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemSetTime(**  

      NOTEHANDLE  note\_handle,  

      const char far \*td\_item\_name,  

      const TIMEDATE far \*td\_item\_ptr**);**



**Description :**



This
function takes a handle to an open note, the name for the Item you wish to
append and the TIMEDATE  you wish to have stored in that Item.  It an Item of
that name already exists, it is first deleted and then the new value is
appended with the same Item name.   

  

Note: NSFItemSetTime sets the ITEM\_SUMMARY flag in the item. Items with the
ITEM\_SUMMARY flag set are stored in the note's summary buffer. These items may
be used in view columns,  selection formulas, and @functions. The maximum size
of the summary buffer is 32K per note. If you append more than 32K bytes of
data in items that have the ITEM\_SUMMARY flag set, NSFItemSetTime will succeed,
but NSFNoteUpdate will return ERR\_SUMMARY\_TOO\_BIG. To avoid this, decide which
fields are not used in view columns, selection formulas, or @ functions. For
these "non-computed" fields, do not use the higher-level API
functions such as NSFItemSetText and NSFItemSetTime. Instead, use NSFItemAppend
to append these items to the document without setting the ITEM\_SUMMARY flag in
the item\_flags argument.    

  

API program may read, modify, and write items that do not have the summary flag
set, but they must open the note first. Items that do not have the summary flag
set can not be accessed in the summary buffer.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

td\_item\_name  -  A pointer to a null-terminated Item name.    

  

td\_item\_ptr  -  A pointer to the TIMEDATE structure you wish to append to the
open note.  

The TIMEDATE structure is a binary representation of a time/date.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added TIMEDATE Item to the note.  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file operations,
etc.).  There are so many possible causes, that It is best to use the code in a
call to OSLoadString and display/log the error for the user as your default
error handling.  

  

  




 **Sample Usage :**


  

  

   /\* Store Item of TYPE\_TIME in in-memory copy of Note \*/  

  

   OSGetIntlSettings(&intl\_format);  

   OSCurrentTIMEDATE(&original\_td);  

   if (error\_status = NSFItemSetTime(note1\_handle, TIME\_ITEM,  

                                     &original\_td))  

       goto Exit;  

  




 **See Also :**


**[NSFItemGetTime](NSFItemGetTime.md)**


**[NSFItemTimeCompare](NSFItemTimeCompare.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFItemAppend](NSFItemAppend.md)**



----------------------------------------------------------------------------------------------------------


 





