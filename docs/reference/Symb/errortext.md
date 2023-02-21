##### Symbolic Value : Resource Definition
##### errortext - Assign an error code number to a text string.
---
```
#include <globerr.h>
```
**Description :**

Assigns the given error code to the given text string.  When language 
compiling, the macro actually amounts to nothing more than a comment.  When 
resource compiling a module (RC), the macro is used to map error code numbers 
to a corresponding text string.

Prior to Release 4.5, an alternative form was defined due to a compiler bug in 
MPW C.  The compiler generated an error when a macro evaluated to nothing and 
is followed by another #define.


/* "errortext" designates a user-displayed message (success, error, warning).
 This is translated, and may be shown to a user. There should be
 online help for most of these messages. */

#define errortext(code,text)


**Sample Usage :**
```

#define       MSG_ADDIN_NAME  (PKG_ADDIN)
    errortext(MSG_ADDIN_NAME,  "AddIn Name")

#define       MSG_ADDIN_VERSION  (PKG_ADDIN+1)
    errortext(MSG_ADDIN_VERSION,  "Version 7.22+")

#define       ERR_EXAMPLE         (PKG_ADDIN+2)
    errortext(ERR_EXAMPLE,    
              "AddIn: Error processing input Database %s")


```
**See Also :**
[AddInFormatError](/domino-c-api-docs/reference/Func/AddInFormatError)
[AddInLogError](/domino-c-api-docs/reference/Func/AddInLogError)
[AddInSetStatus](/domino-c-api-docs/reference/Func/AddInSetStatus)
[PKG_xxx [ADDIN]](/domino-c-api-docs/reference/Symb/PKG_xxx [ADDIN])
[OSLoadString](/domino-c-api-docs/reference/Func/OSLoadString)
---
