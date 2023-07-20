##### Data Type : Composite Data
##### CDSTYLENAME - Stores the style name for a PAB
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   BSIG  Header;
   DWORD Flags;     
   WORD  PABID;     /* ID number of the PAB being named */
   char  StyleName  /* The style name. */
         [MAX_STYLE_NAME+1];
/* If STYLE_FLAG_FONTID, a FONTID follows this structure... */
/* If STYLE_FLAG_PERMANENT, the structure is followed by: */
/*  WORD nameLen   Length of user name */
/*  BYTE userName [nameLen] User name   */
} CDSTYLENAME;
```

**Description :**

This structure stores the style name for a Paragraph Attributes Block (PAB).<br>
<br>
        Header              Defines this composite data item as a CDSTYLENAME item.<br>
        Flags                  Optional.  May be set to 0 or to one or more of STYLE_FLAG_xxx values.<br>
        PABID                ID number of the Paragraph Attributes Block being named<br>
                                     (see CDPABDEFINITION).<br>
        StyleName       Style name character array.<br>
<br>
If the flag STYLE_FLAG_FONTID is set, the record is followed by a FONTID.<br>
<br>
If the flag STYLE_FLAG_PERMANENT is set, the record is followed by a word containing the length of the user name, then the user name (padded with a null byte if the user name is an odd length).  The user name is the name of the user who defined this named style.


**See Also :**
[CDPABDEFINITION](/domino-c-api-docs/reference/Data/CDPABDEFINITION)
[STYLE_FLAG_xxx](/domino-c-api-docs/reference/Symb/STYLE_FLAG_xxx)
---
