##### Data Type : encryption
##### CIPHERHANDLE - A handle for a cryptographic operation
---
```
#include <nsfnote.h>
```

**Definition :**

typedef MEMHANDLE CIPHERHANDLE;

**Description :**

This data type is a handle necessary for certain cryptographic operations.  It is acquired and used by various NSFNoteCipherxxx functions, and destroyed via NSFCipherDestroy when no longer needed.


**See Also :**
---
