##### Symbolic Value : Formula
##### ESCxxx - Special @Function Escape Codes.
---
```
#include <nsfdata.h>
```

**Symbolic Values :**

	ESCBEGIN	  -  Begin escape sequence

	ESCEND	  -  End escape sequence


**Description :**

Some @Functions cannot be translated when the formula is evaluated.  Instead, the value must be obtained when the result is to be displayed or used.  These functions place a special escape sequence in the result string where the actual values is to be placed.<br>
<br>
@Functions which generate these escape sequences are:<br>
<br>
        @DocNumber<br>
        @DocSiblings<br>
        @DocChildren<br>
        @DocDescendants<br>
        @IsExpandable<br>
        @DocLevel<br>
        @IsCategory<br>
        @DocParentNumber<br>



**See Also :**
[NSFTranslateSpecial](/domino-c-api-docs/reference/Func/NSFTranslateSpecial)
---
