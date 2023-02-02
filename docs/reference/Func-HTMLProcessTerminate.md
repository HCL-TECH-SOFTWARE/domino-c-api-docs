##### Function : HTML
##### HTMLProcessTerminate - Releases process wide resources.
---
##### #include <htmlapi.h>
void LNPUBLIC **HTMLProcessTerminate(**
void);
**Description :**
This function releases process wide resources. Normally called once, when user 
process is terminating. Can be called earlier, if no other HTML API operations 
are to be performed. Undefined behavior if 
- called before HTMLProcessInitialize() 
- called multiple times.
If not called, process will terminate with HTML API resources still allocated.
(Usually this is not a problem)
 Threading: must be called from one thread, no other concurrent HTML API calls.

**Parameters :**

Output :
(routine)  -  void


**See Also :**
[HTMLProcessInitialize](D:/md_files/HTMLProcessInitialize.md)
---
