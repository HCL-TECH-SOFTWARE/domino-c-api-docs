##### Function : HTML
##### HTMLProcessInitialize - Initializes the HTML API process-wide resources.
---
##### #include <htmlapi.h>
STATUS LNPUBLIC **HTMLProcessInitialize(**
void);
**Description :**
This function initializes the HTML API process-wide resources. Normally called 
once, when user process is initializing.Calling this is Optional -- if not 
called, the first call to HTMLCreateConverter will do initialization.Multiple 
calls are OK -- they do not "nest" (i.e. multiple calls do not pair with 
HTMLProcessTerminate().) Calling this after a call to HTMLProcessTerminate() 
results in undefined behavior.
Threading: can be called from multiple threads concurrently  with 
HTMLCreateConverter()
**Parameters :**

Output :
(routine)  -  Return status from this call.
	NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


**See Also :**
[HTMLProcessTerminate](D:/md_files/HTMLProcessTerminate.md)
---
