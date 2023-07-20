##### Data Type : Composite Data
##### CDFRAMESETHEADER - Preliminary header information to CDFRAMESET and CDFRAME record(s).
---
```
#include <fsods.h>
```

**Definition :**
```
typedef struct {
   WSIG  Header;
   WORD  Version;
   WORD  RecCount;    /* Total number of CDFRAMESET and CDFRAME
                         recs that follow */
   DWORD Reserved[4]; /* Reserved for future use, must be 0 */
} CDFRAMESETHEADER;
```

**Description :**

Beginning header record to both a CDFRAMESET and CDFRAME record.
<ul><br>
<br>
Header<br>
Version		See FRAMESETHEADER_VERSION.<br>
RecCount		Total number of CDFRAMESET and CDFRAME records that follow.<br>
Reserved		Currently not used, must be 0,</ul>



**See Also :**
[CDFRAME](/domino-c-api-docs/reference/Data/CDFRAME)
[CDFRAMESET](/domino-c-api-docs/reference/Data/CDFRAMESET)
[FRAMESETHEADER_VERSION](/domino-c-api-docs/reference/Symb/FRAMESETHEADER_VERSION)
---
