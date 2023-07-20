##### Data Type : Composite Data
##### CDEXTFIELD - Extended field attributes
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   DWORD Flags1;            /* Field Flags (see FEXT_xxx) */
   DWORD Flags2;
   WORD  EntryHelper;       /* Field entry helper type
                              (see FIELD_HELPER_xxx) */
   WORD  EntryDBNameLen;    /* Entry helper DB name length */
   WORD  EntryViewNameLen;  /* Entry helper View name length */
   WORD  EntryColumnNumber; /* Entry helper column number */
   /* Now comes the variable part of the struct... */
} CDEXTFIELD;
```

**Description :**

New field attributes have been added in Release 4.0 of Notes.  To preserve compatibility with existing applications, the new attributes have been placed in this extension to the CDFIELD record.  This record is optional, and may not be present in the $Body item of the form note.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
    Header - Defines this composite data item as a CDEXTFIELD item.<br>
<br>
    Flags1 - Extended field flags;  see entry for FEXT_xxx (CDEXTFIELD - Flags1)<br>
<br>
    Flags2 - Optional extended field flags.  May be set to 0 or FEXT_xxx (CDEXTFIELD - Flags2)<br>
<br>
    EntryHelper - Field entry helper type;  see entry for FIELD_HELPER_xxx<br>
<br>
    EntryDBNameLen - Length of helper database name<br>
<br>
    EntryViewNameLen - Length of helper view name<br>
<br>
    EntryColumnNumber - Column number of helper<br>
<br>
The structure is followed by the name of the helper database (if any) and the name of the helper view (if any).  These names are stored in LMBCS with no NULL delimter.  The total size of the CDEXTFIELD record includes these strings.</ul>



**See Also :**
[CDEXTFIELD_xxxHELPER](/domino-c-api-docs/reference/Symb/CDEXTFIELD_xxxHELPER)
[CDFIELD](/domino-c-api-docs/reference/Data/CDFIELD)
[FIELD_HELPER_xxx](/domino-c-api-docs/reference/Symb/FIELD_HELPER_xxx)
[FEXT_xxx (Flags1)](/domino-c-api-docs/reference/Symb/FEXT_xxx (Flags1))
[FEXT_xxx (Flags2)](/domino-c-api-docs/reference/Symb/FEXT_xxx (Flags2))
---
