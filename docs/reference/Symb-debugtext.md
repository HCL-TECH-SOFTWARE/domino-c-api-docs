##### Symbolic Value : Resource Definition
##### debugtext - Assign an error code number to a text string.
---
##### #include <globerr.h>
**Description :**
Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

Prior to Release 4.5, an alternative form was defined due to a compiler bug in 
MPW C.  The compiler generated an error when a macro evaluated to nothing and 
is followed by another #define.



/* "debugtext" designates DEBUG-only messages. This is not to be
 translated and never shown to a user. */

#define debugtext(code,text)

**Sample Usage :**
```
#define ERR_POOL_FREE_CHAIN   PKG_MISC+26
 debugtext(ERR_POOL_FREE_CHAIN, "Invalid pool free chain")
#define ERR_LOCK_POOL_TWICE   PKG_MISC+27
 debugtext(ERR_LOCK_POOL_TWICE, "Attempt to lock twice using same pool lock")
#define ERR_TOO_MANY_LOCKS   PKG_MISC+28
 debugtext(ERR_TOO_MANY_LOCKS,  "Too many locks on pool")
```
**See Also :**
[AddInFormatError](D:/md_files/AddInFormatError.md)
[AddInLogError](D:/md_files/AddInLogError.md)
[AddInSetStatus](D:/md_files/AddInSetStatus.md)
[PKG_xxx](D:/md_files/PKG_xxx.md)
[OSLoadString](D:/md_files/OSLoadString.md)
---
