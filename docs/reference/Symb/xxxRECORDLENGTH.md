##### Symbolic Value : Rich Text
##### xxxRECORDLENGTH - Specifies the number of bytes necessary to hold the length of a particular CD record.
---
```
#include <ods.h>
```

**Symbolic Values :**

	LONGRECORDLENGTH	  -  The header is an LSIG structure and the Length member is of type DWORD.

	WORDRECORDLENGTH	  -  The header is a WSIG structure and the Length member is of type WORD.

	BYTERECORDLENGTH	  -  The header is a BSIG structure.


**Description :**

Every CD record begins with a header.  There are three types of headers, BSIG, WSIG, and LSIG.  The first byte of the header is a signature which identifies the type of the header and the type of the CD record that follows.   For the LSIG header, the signature byte is OR'd with WORDRECORDLENGTH to produce a WORD signature.  The Length member of the header is of type DWORD.  For the WSIG header, the signature byte is OR'd with WORDRECORDLENGTH to produce a WORD signature.  The Length member of the header is of type WORD.   For the BSIG header, the signature is of type BYTE and the Length member of the header is also of type BYTE.


**See Also :**
[BSIG](/domino-c-api-docs/reference/Data/BSIG)
[LSIG](/domino-c-api-docs/reference/Data/LSIG)
[SIG_CD_xxx](/domino-c-api-docs/reference/Symb/SIG_CD_xxx)
[WSIG](/domino-c-api-docs/reference/Data/WSIG)
---
