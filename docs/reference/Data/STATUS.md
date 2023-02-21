##### Data Type : Error Handling
##### STATUS - Return code type for most IBM C API functions for Domino and Notes.
---
```
#include <global.h>
```
**Description :**

Many IBM C API functions for Domino and Notes return a value of type STATUS.  A 
return value of NOERROR indicates success. The value of NOERROR is 0 so that 
the following expression is more readable:

    if (error = LotusCAPIFunction(...))
        return(error);

The C API defines various non-zero STATUS values, or error codes, that are 
returned by C API functions in response to various error conditions. Specific 
error codes are defined in the C API header files globerr.h, nsferr.h, 
niferr.h, etc.

Under Windows, Domino and Notes use STATUS error codes as resource IDs that 
identify strings. These strings reside in string tables associated with the 
Domino and Notes DLLs. 

If a C API function returns a non-zero error code, your program may interpret 
this code by calling the function OSLoadString. OSLoadString takes an error 
code as input, and returns a printable error string as output. You may print 
the resultant error string to the screen or display it in a dialog box.

The 16-bit value of a STATUS error code consists of two bit flags, a subsystem 
code, and an error code specific to the subsystem.

The bit flag STS_REMOTE indicates that the error was detected on a remote IBM 
Domino Server, rather than on the local machine. The bit flag STS_DISPLAYED 
indicates that some component of the system has already reported this error to 
the user, so your program probably does not need to.

TheC API macro ERR() masks off these two bit flags, yielding an error code with 
just the subsystem identifier and the subsystem-specific error code. Use the 
macro ERR() to mask off these bits before passing a STATUS error code to 
OSLoadString, because these bits may prevent OSLoadString from interpreting the 
code correctly.

The C API provides two other macros, PKG() and ERRNUM(), that take STATUS error 
codes as input. The macro PKG() yields a subsystem code, e.g. PKG_NSF, that 
identifies the subsystem that encountered the error.  The macro ERRNUM() takes 
a STATUS error code as input and yields the specific error code as output.

If you are comparing a status code to a specific set of known error codes 
(ERR_xxx), you should strip off the STS_REMOTE and STS_DISPLAYED flags before 
comparing the values, since the comparison will not match if either one of 
these flags are set.

**Sample Usage :**
```

STATUS      error;
char        szNotesError[MAX_NOTES_ERROR];

if (error = NSFDbOpen(szName))
{
    OSLoadString(NULLHANDLE, ERR(error), szNotesError, MAX_NOTES_ERROR);

    printf("Unable to open database: %s.\n", szNotesError);

    return;
}
```
**See Also :**
[NOERROR](/domino-c-api-docs/reference/Symb/NOERROR)
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
[PKG_xxx [ADDIN]](/domino-c-api-docs/reference/Symb/PKG_xxx [ADDIN])
---
