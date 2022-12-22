




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



**NSFNoteUpdateExtended** **- Write
in-memory note to on-disk database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteUpdateExtended(**  

      NOTEHANDLE  hNote,  

      DWORD  UpdateFlags**);**



**Description :**



This
function writes the in-memory version of a note to its database.  Prior to
issuing this call, a new note (or changes to a note) are not a part of the
on-disk database.  This function allows using extended 32-bit DWORD update
options, as described in the entry UPDATE\_xxx.  

  

You should also consider updating the collections associated with other Views
in a database via the function NIFOpenCollection or NIFUpdateCollection, if you
have added and/or deleted a substantial number of documents.  If the Server's
Indexer Task does not rebuild the collections associated with the database's
Views,  the first user to access a View in the modified database might
experience an inordinant delay, while the collection is rebuilt by the Notes
Workstation (locally) or Server Application (remotely).


 


**Parameters :**



Input :  

hNote  -  Handle of note to write to database.  

  

UpdateFlags  -  Flags that control the manner in which the note update is done.
The flags are defined in UPDATE\_xxx and may be ORed together.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR  

ERR\_DATA\_ONLY  

ERR\_UPDATE\_CLASS  

ERR\_VERSION  

ERR\_CONFLICT  

ERR\_NOT\_AUTHOR  

ERR\_NEW\_NAME\_KEY  

  

ERR\_SUMMARY\_TOO\_BIG -  "Field is too large (32K) or field's column in selection
formula is too large".  You have appended more than about 16184 bytes to
this note in items that have the ITEM\_SUMMARY flag set. API functions such as
NSFItemSetText set the ITEM\_SUMMARY flag by default. Work around this problem
by using NSFItemAppend to append some of these fields to the note without
setting the ITEM\_SUMMARY flag in the item\_flags argument to NSFItemAppend.   

  

  




 **See Also :**


**[ITEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/00F200B70087008C85255E2D007931E6)**


**[NIFOpenCollection](NIFOpenCollection.md)**


**[NIFUpdateCollection](NIFUpdateCollection.md)**


**[NSFItemAppend](NSFItemAppend.md)**


**[NSFNoteClose](NSFNoteClose.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[UPDATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4A0056976E)**


**[NSFNoteUpdate](NSFNoteUpdate.md)**



----------------------------------------------------------------------------------------------------------


 





