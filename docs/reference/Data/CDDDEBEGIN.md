##### Data Type : Composite Data
##### CDDDEBEGIN - Specifies the start of a DDE link.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct
    {
        WSIG Header;                  /* Signature and length of 
                                         this record */
        char ServerName[DDESERVERNAMEMAX];  /* Null terminated 
                                               server name */
        char TopicName[100];        /* Null terminated DDE Topic
                                       (usually a file name) */
        char ItemName[DDEITEMNAMEMAX];  /* Null terminated Place 
                                           reference string */
        DWORD Flags;                /* See DDEFLAGS_xxx flag
                                       definitions */
                                     
        char PasteEmbedDocName[80]; /* only used on when making 
                                       new link during Paste 
                                       Special */
        WORD EmbeddedDocCount;      /* Number of embedded docs 
                                       for this link */
                                    /* (MUST BE 0 or 1) */
        WORD ClipFormat;            /* Clipboard format with
                                       which data should be 
                                       rendered */
                                    /* ( See DDEFORMAT_xxx) */

        /* Null terminated embedded document name which is 
           attached to the note follows.. */
        }CDDDEBEGIN;

```

**Description :**

A CD record of this type specifies the start of a DDE link.<br>
<br>
Note that CDDDEBEGIN records reside in items of type TYPE_COMPOSITE. Therefore, API programs that run on non-Intel architecture platforms must perform host/canonical conversion on structures of this type when accessing these records in an item in a note.


**See Also :**
[CDDDEEND](/domino-c-api-docs/reference/Data/CDDDEEND)
---
