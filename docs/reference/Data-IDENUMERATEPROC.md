##### Data Type : ID Table
##### IDENUMERATEPROC - Action routine for entries in an ID Table.
---
##### #include <idtable.h>
**Description :**
This type defines the interface to the routine called by IDEnumerate().  Under 
Windows, the routine must be exported in the application's .DEF file.

The address of a routine with this interface is passed as a parameter to 
IDEnumerate().  The routine will be called once for each note ID in the ID 
Table.  The first parameter is supplied in the call to IDEnumerate, and the 
second parameter is the current note ID.  If this routine returns an error, 
IDEnumerate will halt and return that error.
**See Also :**
[IDEnumerate](D:/md_files/IDEnumerate.md)
---
