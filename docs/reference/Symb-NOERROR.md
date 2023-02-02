##### Symbolic Value : Error Handling
##### NOERROR - Function return STATUS code indicating "success".
---
##### #include <globerr.h>
**Description :**
Many API functions return a value of type STATUS.  A return value of NOERROR 
indicates success.  The value of NOERROR is 0 so that the following expression 
is more readable:


    if (error = NotesAPIFunction(...))
        return(error);
**See Also :**
[STATUS](D:/md_files/STATUS.md)
---
