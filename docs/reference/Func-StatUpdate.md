##### Function : Statistics Reporting
##### StatUpdate - Updates a statistic's value.
---
##### #include <stats.h>
STATUS LNPUBLIC **StatUpdate(**

	const char far *Facility,
	const char far *StatName,
	WORD  Flags,
	WORD  ValueType,
	const void far *Value);
**Description :**
This function updates the value of a statistic for the current server session.  
For information regarding the Lotus Domino server statistics see the 
Administering the Domino System documentation.
**Parameters :**
Input :
Facility  -  Name of facility.  See Symbolic Value, STATPKG_xxx for a list of existing Domino facilities.  If the facility is not an existing facility monitored by Domino, a new facility with the  accompanying statistic will be created for the current server session.  

StatName  -  Name of statistic.  If the facility and statistic combination is not one that exists and is monitored by Domino, a new statistic will be created for the current server session. 

Flags  -  Flags that modify the behavior of StatUpdate. Specify 0 for default behavior. Specify ST_UNIQUE if only one instance of statistic should be allowed.  Specify ~ST_UNIQUE if you want to append another instance of this statistic.  Specify ST_ADDITIVE if the value type of the statistic is VT_LONG or VT_NUMBER and you want the new value added to the current value of the statistic.

ValueType  -  Value type of the statistic:  VT_LONG, VT_TEXT, VT_TIMEDATE, or VT_NUMBER.

Value  -  Value of the statistic.

Output :
(routine)  -  Return status from this call -- indicates either success (NOERROR) or what the error is.


**Sample Usage :**
```

 nError = StatUpdate (STATPKG_SERVER,          /* name of facility */
                      "Administrator",         /* stat name */
                      ST_UNIQUE,               /* stat is unique */
                      VT_TEXT,                 /* stat value type */
                      NEW_SERVER_ADMINISTRATOR); /* new name */

```
**See Also :**
[StatDelete](D:/md_files/StatDelete.md)
[STATPKG_xxx](D:/md_files/STATPKG_xxx.md)
[ST_xxx](D:/md_files/ST_xxx.md)
---
