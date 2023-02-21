##### Function : Item (Field)
##### NSFItemGetTime - Get the value of TYPE_TIME Item.
---
```
#include <nsfnote.h>
BOOL LNPUBLIC NSFItemGetTime(

	NOTEHANDLE  note_handle,
	const char far *td_item_name,
	TIMEDATE far *td_item_value);
```
**Description :**

This function takes a handle to an open note and the name for the Item whose 
value you wish to get.  It returns the Item in the TIMEDATE variable identified 
by the pointer you provide.

**Parameters :**
Input :
note_handle  -  A handle to an open note in memory.

td_item_name  -  A pointer to a null-terminated item name.

Output :
(routine)  -  TRUE - If Item was present and successfully retrieved.  FALSE  - if Item was not present.


td_item_value  -  The address of a TIMEDATE structure in which the Domino binary time/date retrieved from name Item in the open note is returned.


**Sample Usage :**
```

   /* Print the TIMEDATE ITEM */

   if (NSFItemGetTime(note1_handle, TIME_ITEM, &original_td))
   {
       /* Spec Time/Date string format for convert function        */
       td_format.Date = TDFMT_FULL;   /* show year, month, and day */
       td_format.Time = TTFMT_FULL;   /* show hour, minute, and sec*/
       td_format.Zone = TZFMT_ALWAYS; /* TZ- show on at all times  */

       td_format.Structure = TSFMT_DATETIME; /* req'd. Overall Time*/
                                             /* /Date structure    */
       timedate_str = &text_buf2[0];
       if (error_status = ConvertTIMEDATEToText(&intl_format,
                                      &td_format,
                                      &original_td, timedate_str,
                                      MAXALPHATIMEDATE, &text_len))
           goto Exit;
       timedate_str[text_len] = '\0'; /* provide NULL terminator */
       printf("%s: %s\n", TIME_ITEM, timedate_str);
   }

```
**See Also :**
[NSFItemSetTime](/domino-c-api-docs/reference/Func/NSFItemSetTime)
[NSFItemTimeCompare](/domino-c-api-docs/reference/Func/NSFItemTimeCompare)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
---
