##### Symbolic Value : Rich Text
##### xxxRECORDLENGTH - Specifies the number of bytes necessary to hold the length of a particular CD record.
---
##### #include <ods.h>
**Description :**
Every CD record begins with a header.  There are three types of headers, BSIG, 
WSIG, and LSIG.  The first byte of the header is a signature which identifies 
the type of the header and the type of the CD record that follows.   For the 
LSIG header, the signature byte is OR'd with WORDRECORDLENGTH to produce a WORD 
signature.  The Length member of the header is of type DWORD.  For the WSIG 
header, the signature byte is OR'd with WORDRECORDLENGTH to produce a WORD 
signature.  The Length member of the header is of type WORD.   For the BSIG 
header, the signature is of type BYTE and the Length member of the header is 
also of type BYTE.
**See Also :**
[BSIG](D:/md_files/BSIG.md)
[LSIG](D:/md_files/LSIG.md)
[SIG_CD_xxx](D:/md_files/SIG_CD_xxx.md)
[WSIG](D:/md_files/WSIG.md)
---
