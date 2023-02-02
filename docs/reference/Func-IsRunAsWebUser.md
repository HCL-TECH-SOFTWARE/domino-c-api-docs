##### Function : Agents
##### IsRunAsWebUser - Indicate if a user is a web user.
---
##### #include <agents.h>
BOOL **IsRunAsWebUser(**

	HAGENT  hAgent);
**Description :**
Indicate if a user is a web user.
**Parameters :**
Input :
hAgent  -  Agent handle of the user.

Output :
(routine)  -  True if a user is a web user, otherwise false.


**Sample Usage :**
```
	/* HAGENT hagent set to current running agent context.*/ 

	BOOL bRunAsWebAgent = IsRunAsWebUser(hagent); 
```
**See Also :**
[](D:/md_files/.md)
---
