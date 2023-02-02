##### Function : OS Environment Variables
##### OSSetEnvironmentTIMEDATE - Set a given environment variable to a provided TIMEDATE value.
---
##### #include <osenv.h>
void **OSSetEnvironmentTIMEDATE(**

	const char *EnvVariable,
	TIMEDATE *td);
**Description :**
Set a TIMEDATE for an environment variable. This routine writes the given 
TIMEDATE into the given environment variable. If NULL is provided for a value 
to set, the current TIMEDATE is sent the to the given environment variable.
**Parameters :**
Input :
EnvVariable  -  Name of environment variable (ASCIZ).

td  -  TIMEDATE  to set.


**Sample Usage :**
```
	/* LastWeekFriday is a TIMEDATE set to a date in the past, say.*/ 

	OSSetEnvironmentTIMEDATE ("LAST_FRIDAY_DATE", &LastWeekFriday); 
	OSSetEnvironmentTIMEDATE ("TODAY_DATE", NULL); 
```
**See Also :**
[](D:/md_files/.md)
---
