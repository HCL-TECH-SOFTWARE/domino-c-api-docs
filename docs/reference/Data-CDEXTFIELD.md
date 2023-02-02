##### Data Type : Composite Data
##### CDEXTFIELD - Extended field attributes
---
##### #include <editods.h>
**Description :**
New field attributes have been added in Release 4.0 of Notes.  To preserve 
compatibility with existing applications, the new attributes have been placed 
in this extension to the CDFIELD record.  This record is optional, and may not 
be present in the $Body item of the form note.

The fields in this structure are:

    Header - Defines this composite data item as a CDEXTFIELD item.

    Flags1 - Extended field flags;  see entry for FEXT_xxx (CDEXTFIELD - Flags1)

    Flags2 - Optional extended field flags.  May be set to 0 or FEXT_xxx 
(CDEXTFIELD - Flags2)

    EntryHelper - Field entry helper type;  see entry for FIELD_HELPER_xxx

    EntryDBNameLen - Length of helper database name

    EntryViewNameLen - Length of helper view name

    EntryColumnNumber - Column number of helper

The structure is followed by the name of the helper database (if any) and the 
name of the helper view (if any).  These names are stored in LMBCS with no NULL 
delimter.  The total size of the CDEXTFIELD record includes these strings.
**See Also :**
[CDEXTFIELD_xxxHELPER](D:/md_files/CDEXTFIELD_xxxHELPER.md)
[CDFIELD](D:/md_files/CDFIELD.md)
[FIELD_HELPER_xxx](D:/md_files/FIELD_HELPER_xxx.md)
[FEXT_xxx (Flags1)](D:/md_files/FEXT_xxx (Flags1).md)
[FEXT_xxx (Flags2)](D:/md_files/FEXT_xxx (Flags2).md)
---
