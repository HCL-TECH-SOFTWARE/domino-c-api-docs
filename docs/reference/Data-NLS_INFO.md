##### Data Type : Character Manipulation
##### NLS_INFO - The data structure that defines the attributes of a character set.
---
##### #include <nls.h>
**Description :**
An NLS_INFO struct defines the attributes of a character set.  It contains a 
number of flags and pointers to various translation tables.  Most of the 
National Language Services (NLS) functions take a pointer to an NLS_INFO struct 
as one of their arguments.  You should initialize the NLS_INFO struct by 
calling the function OSGetLMBCSCLS() before calling one of the NLS functions.

Note: This data structure should be treated as READ-ONLY -- modifying the data 
structure could have undesired consequences.
**See Also :**
[NLS_PINFO](D:/md_files/NLS_PINFO.md)
---
