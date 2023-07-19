##### Data Type : Mixed 32/16-bit Model
##### NOTESPTR - * OBSOLETE * Mixed 32/16-bit pointer declaration
---
```
#include <global.h>
```

**Definition :**

#define NOTESPTR FAR *

**Description :**

***OBSOLETE - Included for backward compatibility only***
<ul><br>
<br>
This macro isolates the different syntax for pointer declarations required by different compilers when using the mixed 32/16-bit model to build 32-bit applications for OS/2 2.1.</ul>



**Sample Usage :**
```
#include <global.h>

    /* Subroutine to increment a long integer */
NOTESPTR IncrementLong (long NOTESPTR longPtr)
{
    (*longPtr)++;
    return (longPtr);
}

int main (void)
{
    long    myValue = 0;
    long    *flatPointer = &myValue;  /* 32-bit pointer to data */

        /* Illustrate the pedantically correct typecasts */
    flatPointer = (long *) IncrementLong ((long NOTESPTR) (&myValue));

    return ((int) *flatPointer);
}
```

**See Also :**
---
