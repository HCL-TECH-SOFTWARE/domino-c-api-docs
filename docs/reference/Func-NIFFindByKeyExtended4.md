##### Function : NIF
##### NIFFindByKeyExtended4 - Identical to NIFFindByKeyExtended3 with the addition of an associated timer for search operation (avoids hanging the collection).
---
##### #include <nif.h>
STATUS **NIFFindByKeyExtended4(**

	void *KeyBuffer,
	DWORD  FindFlags,
	DWORD  ReturnFlags,
	void *pReserved,
	NIFFINDBYKEYPROC  NIFFindByKeyCallback,
	NIFFINDBYKEYCTX *Ctx,
	DWORD  dwTimeOutSecs,
	COLLECTIONPOSITION *retIndexPos,
	DWORD *retNumMatches,
	WORD *retSignalFlags,
	DHANDLE *rethBuffer,
	DWORD *retSequence);
**Description :**
NIFFindByKey looks up index entry by "key." Given a "key" buffer in the 
standard format of a summary buffer, this routine locates the entry that 
matches the given key or keys. Supply as many "key" summary items as required 
to correspond to the way the index collates to find a unique entry.
If multiple index entries match the specified key (especially if not enough key 
items were specified), the index position of the FIRST matching entry is 
returned ("first" is defined by the entry which collates before all others in 
the collated index).
**Parameters :**
Input :
KeyBuffer  -  Address of "key" summary buffer.

FindFlags  -  Find flags word (FIND_xxx).

ReturnFlags  -  PMask specifying what information is to be returned on each entry
(READ_MASK_xxx).  Information is always returned in the
order of the bits which are 1, from bit 0 to bit 15.

pReserved  -  For the embedded ReadEntries call case, arguments to be passed. Its for internal use,
pass NULL for other cases. (see nifnetods.h, FIND_BY_KEY_READENT_ARGS struct).

NIFFindByKeyCallback  -  a callback function invoked for every full summary buffer 
and at end.

Ctx  -  handle to context structure (see nif.h) for said callback.

dwTimeOutSecs  -  timeout sec to preeempt the FindByKey function.
If 0 then Looks for NIF_FBK_TIMEOUT_SECS env value to set the preempt time.

Output :
(routine)  -  Error status (ERR_NOT_FOUND if none found at all)
On successful search, it returns NOERROR. 


retIndexPos  -  

retNumMatches  -  Place to receive # entries which match (optional).

retSignalFlags  -  Place to receive extra sharing warning flags (optional).

rethBuffer  -  Handle of return buffer (may be NULLHANDLE).

retSequence  -  Index Modified Sequence number.

**Sample Usage :**
```
COLLECTIONPOSITION posCollection;
NIFFINDBYKEYCTX ctx = { 0 };
memset(&ctx, sizeof(NIFFINDBYKEYCTX), 0);

if (error = NIFOpenCollection(
hDb, /* handle of db with view */
hDb, /* handle of db with data */
ViewID, /* noteID of the view */
0, /* collection open flags */
NULLHANDLE, /* handle to unread ID list (input and return) */
&hCollection, /* collection handle (return) */
NULLHANDLE, /* handle to open view note (return) */
NULL, /* universal noteID of view (return) */
NULLHANDLE, /* handle to collapsed list (return) */
NULLHANDLE)) /* handle to selected list (return) */
goto EXIT1;

error = NIFFindByKeyExtended4(
hCollection,
pKey, /* refer to key */
FIND_CASE_INSENSITIVE|FIND_AND_READ_MATCHES | FIND_SPECIFIC_MATCHES | 
FIND_FIRST_EQUAL, /* match rules */
ReturnFlags, NULL,
&posCollection, /* where match begins (return) */
&NumNotesMatch, NULL, NULL, NULL, NIFFindByKeyCallBack, &ctx, 1);/* how many 
match (return) */
```
**See Also :**
[](D:/md_files/.md)
---
