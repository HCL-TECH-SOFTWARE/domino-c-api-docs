




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



**OPEN\_xxx (note)** **-** Controls the
way NSFNoteOpen, NSFNoteOpenByUNID, NSFNoteOpenExt, or NSFDbCopyNoteExt opens a
note.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**


 **Symbolic Values :**      OPEN\_SUMMARY    -  Read only summary information.  

  

      OPEN\_NOVERIFYDEFAULT             -  Do not verify if this is the default
note in this class. A note is a default note if the NOTE\_CLASS\_DEFAULT bit is
OR'd into the note class. Normally, if the NOTE\_CLASS\_DEFAULT bit is OR'd into
the note class, then NSFNoteOpen or NSFNoteOpenByUNID will check this note
against a default note table in the database and verify that the note being
opened is still the default note for that class. If this flag is set, then such
verification will not occur. This flag saves one disk I/O if the note is marked
as being the "default note", in the event that this information is
not desired.  

  

      OPEN\_EXPAND       -  For fields of TYPE\_TEXT, expand the data to 1-entry
TYPE\_TEXT\_LIST values while reading the note. For fields of TYPE\_NUMBER, expand
the data to TYPE\_NUMBER\_RANGE. For fields of TYPE\_TIME, expand the data to
TYPE\_TIME\_RANGE. This option is necessary if the note is to be signed or a
signature verified; please see the entry for NSFNoteSign() for details.  

  

      OPEN\_NOOBJECTS            -  Do not read any objects. Objects include
file attachments and DDE links.Warning: documents opened with OPEN\_NOOBJECTS
then subsequently updated loose all objects that were previously attached.  

  

      OPEN\_SHARE         -  Open in a "shared" memory mode.  

  

      OPEN\_CANONICAL             -  Return ALL item values in canonical form,
including the datatype WORD. API programs should not use this flag when
explicitly calling NSFNoteOpen or NSFNoteOpenByUNID and must not use this flag
when explicitly calling NSFDbCopyNoteExt. However, if the API program is a
Domino database hook driver or an extension manager that accesses note item
data over a network and the note was not opened by the API program itself, then
it must check the OpenFlags parameter in the NoteOpen callback function (if the
program is a database hook driver) or in the callback function for EM\_NSFNOTEOPEN
or EM\_NSFNOTEOPENBYUNID (if the program is an extension manager) to see whether
this flag is set. If this flag is set, use ODSReadMemory to convert any
canonical data to host data. This can also be checked by calling NSFNoteGetInfo
() with the header member \_NOTE\_FLAGS, and checking the flags for the presence
of NOTE\_FLAG\_CANONICAL.  

  

      OPEN\_MARK\_READ            -  Mark unread to read if unread list is
currently associated (database is a remote database).  

  

      OPEN\_ABSTRACT   -  Only open an abstract of large documents.  

  

      OPEN\_RESPONSE\_ID\_TABLE         -  Generate an ID Table of Note IDs for
the responses to this note. Use this option in order to access the Note IDs of
the immediate responses to a given note in a later call to NSFNoteGetInfo()
using \_NOTE\_RESPONSES as the note header member ID.  

  

      OPEN\_WITH\_FOLDERS       -  Include folder objects - the default is not
to. Folder objects appear in Folder notes. Folder notes contain two folder
object items. The names of these items are VIEW\_FOLDER\_IDTABLE and
VIEW\_FOLDER\_OBJECT. Each of these items is of TYPE\_OBJECT. In order to access
these items you must open the note with this flag. This flag can only be used
with functions that take DWORD OPEN\_xxx(note) flags, such as NSFNoteOpenExt.
You do not need to set this flag when calling NSFDbCopyNoteExt.  

  

      OPEN\_RAW\_RFC822\_TEXT            -  If set, leave TYPE\_RFC822\_TEXT items
in native format. Otherwise, convert to TYPE\_TEXT/TYPE\_TIME. This flag can only
be used with functions that take DWORD OPEN\_xxx(note) flags, such as
NSFNoteOpenExt.  

  

      OPEN\_RAW\_MIME\_PART    -  If set, leave TYPE\_MIME\_PART items in native
format. Otherwise, convert to TYPE\_COMPOSITE. This flag can only be used with
functions that take DWORD OPEN\_xxx(note) flags, such as NSFNoteOpenExt.  

  

      OPEN\_RAW\_MIME   -  (OPEN\_RAW\_RFC822\_TEXT | OPEN\_RAW\_MIME\_PART) This flag
can only be used with functions that take 32-bit DWORD OPEN\_xxx(note) flags,
such as NSFNoteOpenExt.  

  




**Description :**



These flags
control the manner in which NSFNoteOpen, NSFNoteOpenByUNID, NSFNoteOpenExt, or
NSFDbCopyNoteExt reads a note into memory.  This, in turn, controls what
information about the note is available to you and how it is structured. 


 **See Also :**


**[NSFDbCopyNoteExt](NSFDbCopyNoteExt.md)**


**[NSFNoteGetInfo](NSFNoteGetInfo.md)**


**[NSFNoteOpen](NSFNoteOpen.md)**


**[NSFNoteOpenByUNID](NSFNoteOpenByUNID.md)**


**[NSFNoteOpenExt](NSFNoteOpenExt.md)**


**[NSFNoteSign](NSFNoteSign.md)**



----------------------------------------------------------------------------------------------------------


 





