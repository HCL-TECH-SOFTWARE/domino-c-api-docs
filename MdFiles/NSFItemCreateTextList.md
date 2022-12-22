




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



**NSFItemCreateTextList** **- Append a
TYPE\_TEXT\_LIST item to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemCreateTextList(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      const char far \*item\_text,  

      WORD  text\_len**);**



**Description :**



This
function takes a handle to an open note, the name for the text list item you
wish to append , the text you wish to have stored as the FIRST entry in the
list and the length of that text string.  If an Item of that name already
exists, it is first deleted and then the new value is appended with the same
item name.  

  

Note: NSFItemAppendTextList sets the ITEM\_SUMMARY flag in the item. Items with
the ITEM\_SUMMARY flag set are stored in the note's summary buffer. These items
may be used in view columns,  selection formulas, and @functions. API program
may read the summary buffer without opening the note. The maximum size of the
summary buffer is 32K per note. If you append more than 32K bytes of data in
items that have the ITEM\_SUMMARY flag set, NSFItemAppendTextList will succeed,
but NSFNoteUpdate will return ERR\_SUMMARY\_TOO\_BIG. To avoid this, decide which
fields are not used in view columns, selection formulas, or @ functions. Append
these "non-computed" fields to the document using NSFItemAppend
without setting the ITEM\_SUMMARY flag in the item\_flags argument.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note in memory.  

  

item\_name  -  A pointer to a null-terminated Item name.  

  

item\_text  -  A pointer a null-terminated LMBCS string containing the text you
wish to add as the first entry in the text list being appended to the open
note.  It can be no longer than 60K.  

  

text\_len  -  A WORD containing the length of the null-terminated LMBCS string
text list entry.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added Text List Item to note.  

  

ERR\_MEMORY - Not enough global memory available for allocation  

  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported
(60K).  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, etc.).  There are so many possible causes, that It is best to use
the code in a call to OSLoadString and display/log the error for the user as
your default error handling.  

  

  




 **Sample Usage :**


  

   /\* Create, populate, and store Item of TYPE\_TEXT\_LIST in  \*/  

   /\* in-memory copy of Note.                                \*/  

   

  if (error\_status = NSFItemCreateTextList(note1\_handle,  

                                          TEXT\_LIST\_ITEM,  

                                          SOME\_TEXT1,  

                                          strlen(SOME\_TEXT1)))  

       goto Exit;


 **See Also :**


**[NSFItemAppendTextList](NSFItemAppendTextList.md)**


**[NSFItemGetTextListEntries](NSFItemGetTextListEntries.md)**


**[NSFItemGetTextListEntry](NSFItemGetTextListEntry.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFItemAppend](NSFItemAppend.md)**



----------------------------------------------------------------------------------------------------------


 





