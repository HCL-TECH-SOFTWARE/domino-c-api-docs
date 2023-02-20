##### Function : Database
##### NSFDbGetMultNoteInfo - Get information for a number documents in a database from their note ids in a single call.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetMultNoteInfo(

	DBHANDLE  hDb,
	WORD  Count,
	WORD  Options,
	DHANDLE  hInBuf,
	DWORD *retSize,
	DHANDLE *rethOutBuf);
```
**Description :**

NSFDbGetMultNoteInfo may used to get information for a number documents in a 
database from their note ids in a single call.The caller provides a handle to 
an array of note ids in CANONICAL form and a count of the number of note ids in 
that array. The 
caller also specifies what information they would like returned for each of 
these documents. This may include the OID, the UNID,  the note modified time, 
the note class and the bs flags. A handle is returned to a buffer with entries 
for the documents composed
of the note id  and the requested information in the same order as the note ids 
in the input array. Each component of the entry is in canonical form and the 
order of the information in the entries is note id, OID, UNID, modified time, 
note class and bs flags. although the actual information returned is dependent 
on the request.

The returned data will always include the note id, zeroed if the document does 
not exist in the database or with NOTEID_RESERVED set if the document is 
deleted.

**Parameters :**
Input :
hDb  -  A handle to an open Domino database.

Count  -  The number of note ids in the input array.

Options  -  Specify the infomation to return:

		fINFO_UNID			Note's UNID
		fINFO_OID			Note's OID (disables UNID)
		fINFO_ALLOW_HUGE		Allow the returned buffer to exceed 64k.


hInBuf  -  Handle to the array of note ids.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

		NOERROR - Successfully retrieved the note information.

		ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retSize  -  Size of the information in the returned buffer.

rethOutBuf  -  Handle for returned data.


**See Also :**
[fINFO_XXX](/reference/Symb/fINFO_XXX)
[NOTEID](/reference/Data/NOTEID)
[NSFDbGetMultNoteInfoByUNID](/reference/Func/NSFDbGetMultNoteInfoByUNID)
[NSFDbGetNoteInfo](/reference/Func/NSFDbGetNoteInfo)
[NSFDbGetNoteInfoByUNID](/reference/Func/NSFDbGetNoteInfoByUNID)
[OID](/reference/Data/OID)
[ORIGINATORID](/reference/Data/ORIGINATORID)
[UNID](/reference/Data/UNID)
[UNIVERSALNOTEID](/reference/Data/UNIVERSALNOTEID)
---
