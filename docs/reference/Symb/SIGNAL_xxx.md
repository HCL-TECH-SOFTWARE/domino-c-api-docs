##### Symbolic Value : Views
##### SIGNAL_xxx - NIFReadEntries() - retSignalFlags
---
```
#include <nif.h>
```
**Description :**

NIFReadEntries() returns these flags, as output, in the WORD specified by the 
retSignalFlags parameter. NIFReadEntries() may set multiple signal flags in the 
SignalFlags word by bitwise Or-ing the individual flag values together.

If NIFReadEntries() sets one of the  flags represented by SIGNAL_ANY_CONFLICT, 
the collection has changed since it was last read. Your program may respond to 
this signal by updating the collection with NIFUpdateCollection(), resetting 
the COLLECTIONPOSITION, and calling NIFReadEntries() again.

If NIFReadEntries() sets the SIGNAL_MORE_TO_DO flag, then the end of the 
collection has not been reached and there exists more information than could 
fit in the return buffer.  Your program may respond to this signal by calling 
NIFReadEntries  again to retrieve an additional buffer of information.

**Sample Usage :**
```
   do
   {
      if ( error = NIFReadEntries(
             hCollection,&CollPosition,NAVIGATE_NEXT,
             1L,NAVIGATE_NEXT,0xFFFFFFFF, READ_MASK_NOTEID,
             &hBuffer, NULL, NULL, &EntriesFound,
             &SignalFlag))       /* share warning signal flag */
      {
         return (ERR(error));
      }

      if (hBuffer == NULLHANDLE)
      {
         return (NOERROR);
      }

      IdList = (NOTEID *) OSLockObject (hBuffer);

      for (i=0; i<EntriesFound; i++)
      {
         ProcessOneEntry(IdList[i]); 
      }

      OSUnlockObject (hBuffer);
      OSMemFree (hBuffer);

   }  while (SignalFlag & SIGNAL_MORE_TO_DO);
```
**See Also :**
[NIFReadEntries](/domino-c-api-docs/reference/Func/NIFReadEntries)
[NIFUpdateCollection](/domino-c-api-docs/reference/Func/NIFUpdateCollection)
---
