




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




 


**Symbolic Value : Note**



**UPDATE\_xxx** **-** Flags to
control how a note is updated or deleted.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      UPDATE\_FORCE     -  Do an update or delete even if some
other user has updated the note between the time the note was read into memory
and the time we try to write it. This flag is appropriate for both updating and
deleting a note.  

  

      UPDATE\_NAME\_KEY\_WARNING     -  Give an error if the updated note contains
a new field name that wasn't already defined in one of the forms in the
database. This flag is appropriate for updating a note only.  

  

      UPDATE\_NOCOMMIT          -  Do not flush all data to disk after the
update. The note will be updated by the system, but non-summary data may not be
immediately written to disk. This may improve the speed of NSFNoteUpdate if
many operations are to be done sequentially, but risks loss of data if the
machine crashes before data can be flushed to the disk. Summary data is always
written to disk regardless of whether this flag is set or clear. This flag is
appropriate for both updating and deleting a note.  

  

      UPDATE\_NOREVISION        -  Do not maintain revision history. This flag
is appropriate for updating a note only.  

  

      UPDATE\_NOSTUB   -  Leave no trace of the note in the database if the note
is deleted. This flag is only appropriate for deleting a note. You can use this
flag on a deletion stub by removing the RRV\_DELETED flag from the note id of
the deletion stub before calling NSFNoteDelete or NSFNoteDeleteExtended. Once
the deletion stub is removed, the deletion of the note will not be replicated.
Otherwise, UPDATE\_NOSTUB is only useful for applications that do NOT use views,
and do not replicate. For example, a gateway may periodically examine a
mail.box file, using NSFSearch and simply delete a document (using
UPDATE\_NOSTUB) when it's done with it. The database does not replicate, nor
does it need views. UPDATE\_NOSTUB ensures that there is minimum waste space
allocated to stubs that are never needed in a highly volatile request-style
database. Documents that are deleted with UPDATE\_NOSTUB will still appear in
the Domino views of the database and may cause problems when replicated. The
documents themselves will not exist in the database and therefore cannot be
opened.  

  

      UPDATE\_INCREMENTAL     -  Compute incremental note info.  

  

      UPDATE\_DELETED             -  The current update is a step in the process
of deleting a note. API programs only use this flag in the context of a
database hook driver. See Data Type DBHOOKVEC. Normally, API programs do not
set this flag in calls to NSFNoteUpdate or NSFNoteDelete. NSFNoteDelete
specifies this flag when it calls NSFNoteUpdate in the process of writing the
deletion stub to the disk.  

  

      UPDATE\_DUPLICATES        -  Obsolete. Allow duplicate items of the same
name. This flag is appropriate for updating a note only.  

  

      UPDATE\_SHARE\_SECOND             -  Extended (32-bit DWORD) option: Split
the second update of this note with the Note Object Store.  

  

      UPDATE\_SHARE\_OBJECTS            -  Extended (32-bit DWORD) option: Share
only objects with the Note Object Store, not the summary information.  

  




**Description :**



These flags
control the manner in which Domino and Notes updates or deletes the on-disk
copy of a note.  The extended (32-bit) options are ignored if passed to
NSFNoteUpdate or NSFNoteDelete;  these options can only be passed to
NSFNoteUpdatedExtended, NSFNoteDeleteExtended and NSFDbCopyNoteExt.


 **See Also :**


**[NSFNoteUpdate](NSFNoteUpdate.md)**


**[NSFNoteDelete](NSFNoteDelete.md)**


**[NSFNoteUpdateExtended](NSFNoteUpdateExtended.md)**


**[NSFNoteDeleteExtended](NSFNoteDeleteExtended.md)**


**[NSFDbCopyNoteExt](NSFDbCopyNoteExt.md)**



----------------------------------------------------------------------------------------------------------


 





