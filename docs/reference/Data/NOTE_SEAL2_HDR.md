##### Data Type : Note
##### NOTE_SEAL2_HDR - Seal header infomation structure
---
```
#include <addinout.h>
```

**Definition :**
```
typedef struct {
	DWORD dwVersion;    /* Structure version number, currently MBZ   */ 
	                             /*   (must be 
zero)                          */
	DWORD dwTotalRecordSize;     /* Size of this record + variable data 
+     */
	                             /*   extension descriptors and 
records       */
	DWORD dwFlags;     /* Flags, undefined bits MBZ -               */
	                               /*   see SEAL2HDR_xxx 
below                  */
	DWORD dwEntriesThisItem;     /* Number of NOTE_SEAL2s in this $Seal2 
item */
	WORD  wReserved;             /* Currently must be 
zero                    */
	WORD  wBulkKeyLength;      /* Bulk key length                           
*/
	WORD  wBulkKeyType;    /* Bulk key type                             */
	WORD  wAlgType;     /* Bulk encryption algorithm                 */
	DWORD dwInitVectorLen;      /* Length of initialization vector, if 
any   */
	DWORD dwNumExtensions;      /* Number of header extension 
records        */
	      /* Variable header data follows:             */
	      /*  BYTE initVector[dwInitVectorLen]         */
	      /*  NOTE_RECORD_DESC recDesc[dwNumExtensions]*/
	      /*  dwNumExtensions extension records        */
} NOTE_SEAL2_HDR;
```

**Description :**

Seal header infomation structure.


**See Also :**
---
