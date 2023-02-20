##### Function : NIF
##### NIFGetCollectionViewNoteIDAndDB - Gets NoteID and DB handle of the given view note collection.
---
```
#include <nif.h>
STATUS NIFGetCollectionViewNoteIDAndDB(

	HCOLLECTION  hCollection);
```
**Description :**

This routine defines if the given user structure is valid. It then validates 
and dereferences the handle, returning a specific error if it is an invalid or 
null handle.

**Parameters :**
Input :
hCollection  -  Per-user collection context handle.

Output :
(routine)  -  On invalid or NULL arguments, returns ERR_MISC_INVALID_ARGS error, on successful conversion returns NOERROR. On all other error returns NOTES Error.  



**Sample Usage :**
```
/* This is a dummy user struct with invalid signature to allow returning a bad 
signature and avoid server crashes for stale handle situations. */
static USER DummyUser = {0};
HCOLLECTION hCollection = NULLHANDLE;
USER *user = NULL;
STATUS error = NOERROR;
CollectionUserExt(hCollection, &user);
error=NIFGetCollectionViewNoteIDAndDB (HCOLLECTION hCollection, NOTEID *NoteID, 
DBHANDLE *hDB)
if(error){
return error ;
}
else{
printf(" invalid or DummyUser ");
}
```
**See Also :**
---
