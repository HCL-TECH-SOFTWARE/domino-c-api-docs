##### Function : OS Environment Variables
##### OSGetEnvironmentSeqNo - Returns a sequence number that represents the number of times any environment variable has been changed.
---
##### #include <osenv.h>
WORD **OSGetEnvironmentSeqNo(**
void);
**Description :**
This routine returns a sequence number that represents the number of times an 
environment variable has been changed. Returns 0 if none. This is useful to 
determine when an environment variable has a new value.
**Parameters :**

Output :
(routine)  -  Value of sequence number.


**Sample Usage :**
```
	/* Presume EnvironmentSeqNo external WORD variable. */ 

	WORD NewEnvironmentSeqNo = OSGetEnvironmentSeqNo(); 
	if (NewEnvironmentSeqNo != EnvironmentSeqNo) 
	{ 
	 EnvironmentSeqNo = NewEnvironmentSeqNo; 
	 /* Perform environment variable change logic. */ 
	}
```
**See Also :**
[](D:/md_files/.md)
---
