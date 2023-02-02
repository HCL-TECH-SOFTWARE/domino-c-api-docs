##### Data Type : IDs
##### NOTEID - Note ID within a database.
---
##### #include <nsfdata.h>
**Description :**
A NOTEID identifies a particular note within a given database. Use a NOTEID and 
a database handle to open a note.

A NOTEID is a file position that is guaranteed never to change within the 
database.  It does not contain information about which database the note 
resides in. The NOTEID does not change when the note is modified. Two replica 
copies of the same note, in two separate replica databases, will most likely 
have different NOTEIDs.
**See Also :**
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[ORIGINATORID](D:/md_files/ORIGINATORID.md)
[UNIVERSALNOTEID](D:/md_files/UNIVERSALNOTEID.md)
---
