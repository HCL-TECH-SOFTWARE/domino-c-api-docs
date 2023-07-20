##### Data Type : Basic Encoding Rules
##### Berval - Structure for returning a sequence of octet strings + length
---
```
#include <lber.h>
```

**Definition :**
```
typedef struct berval {
	ber_len_t  bv_len;
	char   *bv_val;
}  Berval;
```

**Description :**

A Berval structure represents binary data that is encoded using simplified Basic Encoding Rules (BER). The data and size of the data are included in a Berval structure as it contains a sequence of bytes and an indication of its length.  Applications may allocate their own Berval structures.<br>

<ul>The fields in this structure are:<br>
<br>
bv_len	    The length of the data in bytes. This member must always be a nonnegative number.<br>
bv_val	    The pointer to the binary data. This member is not null terminated.<br>
</ul>
The Berval structure should be disposed of using ber_bvfree().


**See Also :**
[ber_bvfree](/domino-c-api-docs/reference/Func/ber_bvfree)
[ber_len_t](/domino-c-api-docs/reference/Data/ber_len_t)
---
