##### Function : Canonical Format Conversion
##### odsmacro - Define ODS conversion symbol.
---
```
#include <ods.h>
void odsmacro(

	(any data type)  name,
	int  num,
	int  size);
```
**Description :**

This macro is used to define conversion codes that identify Domino data 
structures that are stored in canonical format to the ODS conversion routines.  
The name of the conversion code consists of an underscore followed by the name 
of the structure.  For example, the conversion code for a WORD is _WORD, and 
the code for a CDHEADER is _CDHEADER.

**Parameters :**
Input :
name  -  Domino symbol for which an ODS conversion code is to be defined.

num  -  Value of the ODS conversion code for this symbol.

size  -  Size of the object in bytes.



**See Also :**
[ODSReadMemory](/reference/Func/ODSReadMemory)
[ODSLength](/reference/Func/ODSLength)
[ODSWriteMemory](/reference/Func/ODSWriteMemory)
[_xxx (ODS Types)](/reference/Symb/_xxx (ODS Types))
---
