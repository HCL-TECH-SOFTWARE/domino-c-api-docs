




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



**NSFItemAppendTextList** **- Add an
entry to a TYPE\_TEXT\_LIST item in a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFItemAppendTextList(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      const char far \*entry\_text,  

      WORD  text\_len,  

      BOOL  duplicate\_flag**);**



**Description :**



This
function takes a handle to an open note, the name for the text list Item you
wish to add to , the text you wish to have added as the NEXT entry in the list
and the length of that text string.  The last argument is a BOOL indicating
whether or not you wish to allow the creation of duplicate strings in the
list.    

  

If the text list Item does not already exist, one will be created using the
name provided and the text provided as the FIRST entry.  The Item Flags are set
to ITEM\_SUMMARY.


 


**Parameters :**



Input :  

note\_handle  -  A handle to an open note (NOTEHANDLE).  

  

item\_name  -  A pointer to a null-terminated item name.  

  

entry\_text  -  A pointer to a string containing the text you wish to add as the
NEXT entry in the existing text list in the open note.  

  

text\_len  -  A WORD containing the length of the string to be added.  If
MAXWORD is specified, then the string is treated as a null-terminated string,
and the length of the string is used instead.  

  

duplicate\_flag  -  A BOOL containing a flag indicating whether or not to allow
duplicate entries in the text list.  TRUE - If you wish to allow them and FALSE
- If you do not.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully added Text Entry to Text List Item in note.  

  

ERR\_MEMORY - Not enough global memory available for allocation  

  

ERR\_SEGMENT\_TOO\_BIG - Requested size is greater than the maximum supported
(MAXWORD -  (2\*sizeof(WORD)))  

  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, etc.).  There are so many possible causes, that It is best to use
the code in a call to OSLoadString and display/log the error for the user as
your default error handling.  

  

  




 **Sample Usage :**


  

   if (error\_status = NSFItemAppendTextList(note1\_handle,  

                                          TEXT\_LIST\_ITEM, SOME\_TEXT2,  

                                          MAXWORD,  

                                          FALSE))  

       goto Exit;  

  

  




 **See Also :**


**[NSFItemCreateTextList](NSFItemCreateTextList.md)**


**[NSFItemGetTextListEntries](NSFItemGetTextListEntries.md)**


**[NSFItemGetTextListEntry](NSFItemGetTextListEntry.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**



----------------------------------------------------------------------------------------------------------


 





