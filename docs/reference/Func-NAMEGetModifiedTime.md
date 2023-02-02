##### Function : Address Book
##### NAMEGetModifiedTime - Get last modified time of Address book(s)
---
##### #include <lookup.h>
void LNPUBLIC **NAMEGetModifiedTime(**

	TIMEDATE far *retModified);
**Description :**
Note:  Address books refer to both Notes Client Address books, and Domino 
Server Address books know as Domino Directories.

       This function obtains the latest modified time/date of all the Address 
books in the process's list. Use this routine to determine if any of the 
Address books used by your program have been modified since your program 
performed a name lookup.

Name lookup functions create a list of collections from the Address books 
identified by either the Directory Assistance database (formerly referred to as 
the Master Address Book) or the NAMES variable in the notes.ini  file. These 
lookup functions cache the list in memory to improve the efficiency of repeated 
look ups. NAMEGetModifiedTime loops through this list obtaining the data 
modified time/date of each Address book. It returns the latest date found to 
the variable specified by retModified.
**Parameters :**
Input :
retModified  -  Address of a variable to receive last modified date/time

Output :
(routine)  -  None.


retModified  -  The last modified time/date of the most recently modified Address book database

**See Also :**
[NAMELookup](D:/md_files/NAMELookup.md)
[NSFDbModifiedTime](D:/md_files/NSFDbModifiedTime.md)
---
