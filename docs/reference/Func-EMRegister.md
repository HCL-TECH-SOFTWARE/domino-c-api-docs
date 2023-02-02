##### Function : Extension Manager
##### EMRegister - Register callback routine for specific NSF calls.
---
##### #include <extmgr.h>
STATUS LNPUBLIC **EMRegister(**

	EID  EmID,
	DWORD  Flags,
	EMHANDLER  Proc,
	WORD  RecursionID,
	HEMREGISTRATION far *rethRegistration);
**Description :**
Register a callback routine that will be called before or after (or before and 
after) Domino or Notes performs a specified NSF function.

The extension ID codes (EID) are described under EM_xxx.

The recursion ID is used in Domino or Notes core to resolve any recursion 
issues that might arise from the callback function making a call to Domino or 
Notes core functions (for example, calling NSFDbOpen() from an extension 
manager hook for NSFDbOpen()).

If a recursion ID of zero is passed to EMRegister(), Domino or Notes will not 
check for recursion.  The extension manager hook will always be called for that 
function.

In order to prevent recursion, a recursion ID must be obtained by calling 
EMCreateRecursionID() and this recursion ID must be passed to EMRegister().  
Domino or Notes will check before calling the extension manager hook to ensure 
that the current thread has not already called the hook.  If it has, the call 
to the extension manager hook is skipped.
**Parameters :**
Input :
EmID  -  The extension id of the specific NSF call.  See definition of EM_xxx for permissible values.

Flags  -  Indicates when the registered callback function is to be called. Use EM_REG_BEFORE if the callback function is to be called before Domino or Notes performs the NSF function.  Use EM_REG_AFTER  if the callback function is to be called after Domino or Notes performs the NSF function.  They can be ORed together to have the callback function called both before and after the NSF function.

            #define EM_REG_BEFORE		0x0001
            #define EM_REG_AFTER		0x0002

Proc  -  User-written callback function.

RecursionID  -  Unique Id created by a call to EMCreateRecursionID that is used to resolve recursion problems if calls are made to the C API from inside the callback function.  Passing 0 will eliminate the overhead related to checking for recursion problems.

Output :
(routine)  -  
NOERROR
ERR_EM_ILLEGALFLAGS
ERR_EM_ILLEGAL


rethRegistration  -  Handle to be used when de-registering.

**See Also :**
[EMCreateRecursionID](D:/md_files/EMCreateRecursionID.md)
[EMDeregister](D:/md_files/EMDeregister.md)
[EMHANDLER](D:/md_files/EMHANDLER.md)
[EM_xxx](D:/md_files/EM_xxx.md)
---
