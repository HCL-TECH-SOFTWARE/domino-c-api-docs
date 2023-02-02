##### Function : OS Environment Variables
##### OSGetEnvironmentTIMEDATE - Get a timedate from an environment variable. 
---
##### #include <osenv.h>
BOOL **OSGetEnvironmentTIMEDATE(**

	const char *EnvVariable,
	TIMEDATE *td);
**Description :**
Get a timedate from an environment variable. This routine reads the given 
environment variable and converts it to a timedate.
**Parameters :**
Input :
EnvVariable  -  Name of environment variable (Test_Variable).

td  -  TIMEDATE structure to receive value.

Output :
(routine)  -  TRUE if variable found and its value returned. 

FALSE if variable not found or it could not be converted into a timedate.


**Sample Usage :**
```
	if (!OSGetEnvironmentTIMEDATE (buffer, 
	&LastMMRTruncationDate) || 
	(TimeDateCompare(&LastMMRTruncationDate, 
	&TruncationCutoffDate) > 0)) 
	{ 
	 LastMMRTruncationDate = TruncationCutoffDate; 
	 OSSetEnvironmentTIMEDATE (buffer, &TruncationCutoffDate); 
	}
```
**See Also :**
[](D:/md_files/.md)
---
