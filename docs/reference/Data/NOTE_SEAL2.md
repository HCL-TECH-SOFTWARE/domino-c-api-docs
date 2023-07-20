##### Data Type : Note
##### NOTE_SEAL2 - Note seal structure
---
```
#include <nsfdata.h>
```

**Definition :**
```
typedef struct {
	DWORD dwVersion;   /* Structure version number, currently MBZ   */
	DWORD dwTotalRecordSize;  /* Size of this record + variable data +     
*/
	                              /*   extension descriptors and 
records       */
	DWORD dwFlags;    /* Flags, undefined bits MBZ. Defined below  */
	WORD  wKEKType;    /* Key encryption key type  (SEC_ki_xxx)     */
	WORD  wAlgType;    /* Encryption algorithm used to encrypt the  */
	                              /*   bulk (data) encryption key 
(SEC_ai_xxx) */
	TIMEDATE tdSealed;   /* When the seal was created                 */
	DWORD dwEncryptedBulkKeyLength;  /* Length of the encrypted bulk data 
key */
	DWORD dwNumExtensions;   /* Number of extension records               */
	     /*  Variable data 
follows:                                                   */
	     /*  BYTE              
encryptedBulkKey[dwEncryptedBulkKeyLength]             */
	     /*  NOTE_RECORD_DESC  
recDesc[dwNumExtensions]                               */
	     /*  dwNumExtensions extension records of various 
types                       */
} NOTE_SEAL2;
```

**Description :**

Note seal structure.


**See Also :**
---
