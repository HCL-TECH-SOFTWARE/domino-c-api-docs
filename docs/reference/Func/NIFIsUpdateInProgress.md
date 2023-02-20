##### Function : NIF
##### NIFIsUpdateInProgress - Checks and returns TRUE if a NIF update is in progress.
---
```
#include <nif.h>
BOOL NIFIsUpdateInProgress(

	HCOLLECTION  hCollection);
```
**Description :**

This routine can be called by callers who want to find out if the collection is 
being updated and don't want to perform the update themselves.

**Parameters :**
Input :
hCollection  -  Per-user collection context handle.


Output :
(routine)  -  It returns TRUE if an update is in progress. 



**Sample Usage :**
```
/* Get the view title, and output a line saying we're updating it */ 
if (!NSFNoteOpenExt(hDB, ViewNoteID, OPEN_RAW_MIME, &hNote))
{
if (NIFFormatDesignNoteTitle(hNote, szTitle, sizeof(szTitle)-1))
{
COLLECTION_USER *user = CollectionUser(hCollection);
BOOL uptoDate; 
uptoDate = (user->Remote) ? FALSE : (NIFCollectionUpToDate(hCollection) || 
NIFIsUpdateInProgress(hCollection));
if (!uptoDate) /* SPR KNIL3H9HS7 */
LogEvent(ERR_NIF_UPDATE_NA_VIEW, NULLHANDLE, NOERROR, szTitle);
}
NSFNoteClose(hNote);
}
}
```
**See Also :**
[CalCreateEntry](/reference/Func/CalCreateEntry)
[CalReadEntry](/reference/Func/CalReadEntry)
---
