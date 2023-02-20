##### Function : Database
##### NSFDbGetMultNoteInfoByUNID - Get information for a number documents in a database from their UNIDs in a single call.
---
```
#include <nsfdb.h>
STATUS LNPUBLIC NSFDbGetMultNoteInfoByUNID(

	DBHANDLE  hDB,
	WORD  Count,
	WORD  Options,
	DHANDLE  hInBuf,
	DWORD *retSize,
	DHANDLE *rethOutBuf);
```
**Description :**

NSFDbGetMultNoteInfoByUNID may used to get information for a number documents 
in a database from their UNIDs in a single call. The caller provides a handle 
to an array of UNIDs in CANONICAL form and a count of the number of UNIDs in 
that array. The caller also specifies what information they would like returned 
for each of these documents. This may include the note id, the sequence time, 
the sequence number and the OID. If the OID is requested then requests for the 
sequence time and sequence number are ignored as they are included in the OID. 
A handle is returned to a buffer with entries for the documents composed of the 
requested information in the same order as the UNIDs in the input  array. Each 
component of the entry is in canonical form and the order of the information in 
the entries is note id, OID, sequence time and sequence number; although the 
actual information returned is dependent on the request.

For documents that do not exist in the database the returned data will be 
zeroed unless the compress option (fINFO_COMPRESS) is used with a request for 
note ids. In that case a count of the number of consecutive nonexistent 
documents always less than 
NOTEID_MIN will be returned encoded as a note id. The returned buffer will 
contain no other information for those UNIDs.

If the preserve reserved (fINFO_PRESERVE_RESERVED) option is requested then 
deleted documents will have NOTEID_RESERVED set in the returned note id.

The number UNIDs passed in must be less than 32767 and the total size of the 
output buffer must not exceed 64k.

**Parameters :**
Input :
hDB  -  A handle to an open Domino database.

Count  -  The number of UNIDs in the input array.

Options  -  Specify the infomation to return:

		fINFO_NOTEID	- Return NoteID 
		fINFO_SEQTIME	- Return SequenceTime from OID 
		fINFO_SEQNUM	- Return Sequence number from OID 
		fINFO_OID	- Return OID (disables SeqTime & number & UNID)
		fINFO_COMPRESS	- Compress non-existent UNIDs

hInBuf  -  Handle to the array of UNIDS.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

		NOERROR - Successfully retrieved the note information.

		ERR_xxx - Errors returned by lower level functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user.


retSize  -  Size of the information in the returned buffer.

rethOutBuf  -  Handle for returned data.


**See Also :**
[fINFO_XXX](/reference/Symb/fINFO_XXX)
[NSFDbGetMultNoteInfo](/reference/Func/NSFDbGetMultNoteInfo)
[NSFDbGetNoteInfo](/reference/Func/NSFDbGetNoteInfo)
[NSFDbGetNoteInfoByUNID](/reference/Func/NSFDbGetNoteInfoByUNID)
[OID](/reference/Data/OID)
[ORIGINATORID](/reference/Data/ORIGINATORID)
[UNID](/reference/Data/UNID)
[UNIVERSALNOTEID](/reference/Data/UNIVERSALNOTEID)
---
