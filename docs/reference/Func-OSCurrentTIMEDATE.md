##### Function : Time
##### OSCurrentTIMEDATE - Gets the system time/date.
---
##### #include <ostime.h>
void LNPUBLIC **OSCurrentTIMEDATE(**

	TIMEDATE far *retTimeDate);
**Description :**
This function gets the current system time and date, returning it in Domino 
binary format.  The Domino binary time/date format is an internal format, and 
can only be interpreted by using the C API time/date functions.
**Parameters :**

Output :
(routine)  -  None.


retTimeDate  -  The address of a TIMEDATE structure in which the current time and date in Domino binary format is returned.

**Sample Usage :**
```

    OSCurrentTIMEDATE(&binary_td1);   /* Get current Time/Date values */

```
**See Also :**
[ConvertTIMEDATEToText](D:/md_files/ConvertTIMEDATEToText.md)
---
