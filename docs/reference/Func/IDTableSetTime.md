##### Function : ID Table
##### IDTableSetTime - Sets the TIMEDATE structure that is stored in an ID Table.
---
```
#include <idtable.h>
void LNPUBLIC IDTableSetTime(

	void far *pIDTable,
	TIMEDATE  Time);
```
**Description :**

This function sets the TIMEDATE structure that is stored in an ID Table.  This 
storage is reserved for the caller usage and can be used to date an ID Table 
for later comparison with other versions of the same ID Table.

**Parameters :**
Input :
pIDTable  -  A pointer to an ID Table.

Time  -  A TIMEDATE structure containing whatever time/date you wish to associate with an ID Table.

Output :
(routine)  -  None.



**Sample Usage :**
```

   /* Store the current timedate in the ID Table for later use */

   OSCurrentTIMEDATE(&current_td); /* Get current Time/Date values */
   IDTableSetTime(idtable_ptr, current_td);
      

```
**See Also :**
[IDTableFlags](/reference/Func/IDTableFlags)
[IDTableSetFlags](/reference/Func/IDTableSetFlags)
[IDTableSize](/reference/Func/IDTableSize)
[IDTableTime](/reference/Func/IDTableTime)
---
