##### Function : Extension Manager
##### VARARG_COPY -  Copy a variable argument list.
---
```
#include <global.h>
<type> VARARG_COPY(

	VARARG_PTR  dest,
	<type>  src);
```
**Description :**

This function is used to copy the variable argument list of an API function in 
a Extension Manager callback.  This function is implemented as a macro.

Platforms that strictly comply to the C standard do not allow passing of 
variable argument lists by reference using '&' and '*' operators because the 
standard states that you may get undetermined results.  However, you are 
allowed to pass a variable argument list without these operators.  On Linux for 
zSeries, whenever you pass a variable argument list the contents will always be 
modified upon returning from the function passing it in as a parameter 
(assuming some function below accesses the list.)  For these types of 
platforms, the following macros are defined to just pass the list without using 
the '&' operator.  All platforms can still use a variable argument list as a 
pointer by simply using the VARARG_PTR_P type.

#if defined(ZLINUX)
typedef VARARG_PTR VARARG_PTR_P;
#define VARARG_ADDR(_AAP) _AAP
#define VARARG_DEREF(_AAP) _AAP
#define VARARG_COPY __va_copy
#else
typedef VARARG_PTR * VARARG_PTR_P;
#define VARARG_ADDR(_AAP) &_AAP
#define VARARG_DEREF(_AAP) *_AAP
#define VARARG_COPY(dest, src) (dest)=(src)
#endif


**Parameters :**
Input :
dest  -  Variable argument list pointer.

src  -  Pointer to the argument list provided to the core function.  The format of the argument list depends on the actual function.

Output :
(routine)  -  The type of the return value is specified by the "Type" argument.


dest  -  Variable argument list pointer, now pointing to the source argument list.


**Sample Usage :**
```
        if (EM_GETPASSWORD != data->EId)
                return (ERR_EM_CONTINUE);

               /* Fetch the arguments */
	     VARARG_COPY(pArgs, data->Ap);

            MaxPwdLen = VARARG_GET (pArgs, DWORD);
            retLength = VARARG_GET (pArgs, DWORD far *);
          retPassword = VARARG_GET (pArgs, char far *);
             FileName = VARARG_GET (pArgs, char far *);
            OwnerName = VARARG_GET (pArgs, char far *);
              DataLen = VARARG_GET (pArgs, DWORD);
                 Data = VARARG_GET (pArgs, BYTE far *);
```
**See Also :**
[EMHANDLER](/domino-c-api-docs/reference/Data/EMHANDLER)
[EMRECORD](/domino-c-api-docs/reference/Data/EMRECORD)
[VARARG_ADDR](/domino-c-api-docs/reference/Func/VARARG_ADDR)
[VARARG_DEREF](/domino-c-api-docs/reference/Func/VARARG_DEREF)
[VARARG_GET](/domino-c-api-docs/reference/Func/VARARG_GET)
[VARARG_PEEK](/domino-c-api-docs/reference/Func/VARARG_PEEK)
[VARARG_PTR](/domino-c-api-docs/reference/Data/VARARG_PTR)
[VARARG_PTR_P](/domino-c-api-docs/reference/Data/VARARG_PTR_P)
[VARARG_START](/domino-c-api-docs/reference/Func/VARARG_START)
---
