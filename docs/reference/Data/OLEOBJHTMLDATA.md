##### Data Type : HTML
##### OLEOBJHTMLDATA - OLE Object - HTML Data.
---
```
#include <oleods.h>
```

**Definition :**
```
typedef struct {        
   WORD  wLength;               /* Size of this structure including
                                   both fixed and variable
                                   sections */
   WORD  wsURLBaseLength;       /* Length of Base URL */
   WORD  wsURLCodeBaseLength;   /* Length of CodeBase URL */
   WORD  wsMIMETypeCodeLength;  /* Length of MIME CodeType */
   WORD  wsURLDataLength;       /* Length of Data URL */
   WORD  wsDataFldLength;       /* Length of Data Field name */
   WORD  wsDataSrcLength;       /* Length of Data Source ID */
   DWORD dwFlags;               /* Flags */
   WORD  wsLangLength;          /* Length of Language */
   WORD  wsNameLength;          /* Length of Name */
   WORD  wsMIMETypeDataLength;  /* Length of MIME Type */
   WORD  wcEvents;              /* Number of events */
   WORD  wcParams;              /* Number of params */
   WORD  wHeight;               /* Height of object */
   WORD  wWidth;                /* Width of object */
   WORD  wReserved1;            /* Unused, must be 0 */
   WORD  wReserved2;            /* Unused, must be 0 */
   WORD  wReserved3;            /* Unused, must be 0 */
   WORD  wReserved4;            /* Unused, must be 0 */
   WORD  wReserved5;            /* Unused, must be 0 */
   WORD  wReserved6;            /* Unused, must be 0 */
/*
   The variable length portions go here in the following order:
   URLBase - Base URL
   CodeBase - URL that references where to find implementation of the object. 
   CodeType - MIME type of the code referenced by CLSID
   Data - URL of the data to be loaded
   Data Field - column name from the data source object
   Data Source - "#ID" of the data source object
   Lang - ISO standard language abbreviation
   Name - variable name
   Type - MIME type of Data attribute.
   Events - array or list of events (OLEOBJHTMLEVENT structures)
   Params - array or list of params (OLEOBJHTMLPARAM structures)
*/
} OLEOBJHTMLDATA;
```

**Description :**




**See Also :**
[OLEOBJHTMLEVENT](/domino-c-api-docs/reference/Data/OLEOBJHTMLEVENT)
[OLEOBJHTMLPARAM](/domino-c-api-docs/reference/Data/OLEOBJHTMLPARAM)
---
