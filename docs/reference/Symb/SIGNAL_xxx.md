##### Symbolic Value : Views
##### SIGNAL_xxx - NIFReadEntries() - retSignalFlags
---
```
#include <nif.h>
```

**Symbolic Values :**

	SIGNAL_DEFN_ITEM_MODIFIED	  -  At least one of the "definition" view items (Selection formula or sorting rules) has been modified by another user since the last NIFReadEntries. Upon receipt, you may wish to re-read the view note if up-to-date copies of these items are needed. You also may wish to re-synchronize your index position and re-read the rebuilt index. This signal is returned only ONCE per detection.

	SIGNAL_VIEW_ITEM_MODIFIED	  -  At least one of the non-"definition" view items (View name,etc) has been modified since the last NIFReadEntries. Upon receipt, you may wish to re-read the view note if up-to-date copies of these items are needed. This signal is returned only ONCE per detection.

	SIGNAL_INDEX_MODIFIED	  -  The collection index has been modified by another user since the last NIFReadEntries. Upon receipt, you may wish to re-synchronize your index position and re-read the modified index. This signal is returned only ONCE per detection.

	SIGNAL_UNREADLIST_MODIFIED	  -  The unread list has been modified by another window using the same HCOLLECTION context. Upon receipt, you may wish to repaint the window if the window contains the state of the unread flags.

	SIGNAL_DATABASE_MODIFIED	  -  Collection is not up to date.

	SIGNAL_MORE_TO_DO	  -  End of collection has not been reached because the return buffer is too full. The NIFReadEntries call should be repeated to continue reading the desired entries.

	SIGNAL_VIEW_TIME_RELATIVE	  -  The view contains a time-relative formula (e.g., @Now). Use this flag to tell if the collection will EVER be up-to-date since time-relative views, by definition, are NEVER up-to-date.

	SIGNAL_NOT_SUPPORTED	  -  Returned if signal flags are not supported. This is used by NIFFindByKeyExtended when it is talking to a pre-V4 server that does not support signal flags for FindByKey.

	SIGNAL_ANY_CONFLICT	  -  Mask that defines all sharing conflicts, indicating that the database or collection has changed:
(SIGNAL_DEFN_ITEM_MODIFIED | SIGNAL_VIEW_ITEM_MODIFIED | SIGNAL_INDEX_MODIFIED | SIGNAL_UNREADLIST_MODIFIED | SIGNAL_DATABASE_MODIFIED)

	SIGNAL_ANY_NONDATA_CONFLICT	  -  Mask that defines all "sharing conflicts" except for SIGNAL_DATABASE_MODIFIED. This can be used in combination with SIGNAL_VIEW_TIME_RELATIVE to tell if the database or collection has truly changed out from under the user or if the view is a time-relative view which will NEVER be up-to-date. SIGNAL_DATABASE_MODIFIED is always returned for a time-relative view to indicate that it is never up-to-date:
(SIGNAL_DEFN_ITEM_MODIFIED | \
 SIGNAL_VIEW_ITEM_MODIFIED | \
 SIGNAL_INDEX_MODIFIED | \
 SIGNAL_UNREADLIST_MODIFIED)

	SIGNAL_DIFF_READ_NOT_DONE	  -  If a differential view read was requested by providing DiffTime but it could not be performed for some reason, a "regular" ReadEntries is done then this flag is set.


**Description :**

NIFReadEntries() returns these flags, as output, in the WORD specified by the retSignalFlags parameter. NIFReadEntries() may set multiple signal flags in the SignalFlags word by bitwise Or-ing the individual flag values together.<br>
<br>
If NIFReadEntries() sets one of the  flags represented by SIGNAL_ANY_CONFLICT, the collection has changed since it was last read. Your program may respond to this signal by updating the collection with NIFUpdateCollection(), resetting the COLLECTIONPOSITION, and calling NIFReadEntries() again.<br>
<br>
If NIFReadEntries() sets the SIGNAL_MORE_TO_DO flag, then the end of the collection has not been reached and there exists more information than could fit in the return buffer.  Your program may respond to this signal by calling NIFReadEntries  again to retrieve an additional buffer of information.


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
