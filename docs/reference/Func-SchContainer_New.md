##### Function : Calendaring and Scheduling
##### SchContainer_New - Allocate a new object container.
---
##### #include <schedule.h>
STATUS LNPUBLIC **SchContainer_New(**

	HCNTNR FAR *rethCntnr);
**Description :**
This routine allocates a new Calendaring and Scheduling object container.
**Parameters :**

Output :
(routine)  -  NOERROR - Successfully allocated a new container.
ERR_xxx - There are many possible errors. It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



rethCntnr  -  Returns a handle to the object container.

**See Also :**
[SchContainer_Free](D:/md_files/SchContainer_Free.md)
---
