##### Data Type : HTML
##### OLEOBJHTMLPARAM - HTML parameter entry.
---
```
#include <oleods.h>
```

**Definition :**
```
typedef struct {
   WORD wLength;           /* Size of this structure including both
                              fixed and variable sections */
 WORD wsDataFldLength;   /* Length of Data Field */
   WORD wsDataFmtsLength;  /* Length of Data Formats */
   WORD wsDataSrcLength;   /* Length of Data Source */
   WORD wsNameLength;      /* Length of Name */
   WORD wsTypeLength;      /* Length of Type */
   WORD wsValueLength;     /* Length of Value */
   WORD wsValueTypeLength; /* Length of Value Type */
   WORD wReserved1;        /* Unused, must be 0 */
   WORD wReserved2;        /* Unused, must be 0 */
/*
   The variable length portions go here in the following order:
   Data Field - column name from the data source object
   Data Formats - indicates whether bound data is plain text or HTML
   Data Source - "#ID" of the data source object
   Name - name of this parameter
   Type - internal media type
   Value - value associated with parameter
   Value Type - type of value (data, ref, object) 
*/
} OLEOBJHTMLPARAM;
```

**Description :**




**See Also :**
[OLEOBJHTMLDATA](/domino-c-api-docs/reference/Data/OLEOBJHTMLDATA)
---
