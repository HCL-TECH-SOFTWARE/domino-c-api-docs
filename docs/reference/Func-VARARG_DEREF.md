##### Function : Extension Manager
##### VARARG_DEREF - Deference elements of a variable argument list.
---
##### #include <global.h>
<type> **VARARG_DEREF(**

	VARARG_PTR  aap);
**Description :**
This function is used to deference elements of a variable argument list of an 
API function in a Extension Manager callback.  This function is implemented as 
a macro.

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
aap  -  Pointer into a variable argument list. 

Output :
(routine)  -   The type of element dereferenced. 


aap  -  Dereferenced argument list element.

**See Also :**
[EMHANDLER](D:/md_files/EMHANDLER.md)
[EMRECORD](D:/md_files/EMRECORD.md)
[VARARG_ADDR](D:/md_files/VARARG_ADDR.md)
[VARARG_COPY](D:/md_files/VARARG_COPY.md)
[VARARG_GET](D:/md_files/VARARG_GET.md)
[VARARG_PEEK](D:/md_files/VARARG_PEEK.md)
[VARARG_PTR](D:/md_files/VARARG_PTR.md)
[VARARG_PTR_P](D:/md_files/VARARG_PTR_P.md)
[VARARG_START](D:/md_files/VARARG_START.md)
---
