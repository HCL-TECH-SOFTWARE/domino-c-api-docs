##### Symbolic Value : Basic Encoding Rules
##### LBER_xxx (errors) - Used to report BER errors
---
```
#include <lber.h>
```

**Symbolic Values :**

	LBER_ERROR	  -  BER error.

	LBER_DEFAULT	  -  BER error (same as LBER_ERROR).


**Description :**

Note that LBER_ERROR and LBER_DEFAULT are values that can never appear as valid BER tags, and so it is safe to use them to report errors.  In fact, any tag for which the following is true is invalid:  (( tag &amp; 0x00000080 ) != 0 ) &amp;&amp; (( tag &amp; 0xFFFFFF00 ) != 0 )


**See Also :**
---
