##### Data Type : Smartcards
##### SC_MANIP_IMPORTABLE_CERT - Structure used for SC_manip_GetMatchedCert
---
```
#include <kfm.h>
```
**Description :**

SC_MANIP_IMPORTABLE_CERT is used with the SECManipulateSC OpCode 
SC_manip_GetMatchedCert (in SC_manip_xxx) to examine the certificates that are 
available for import from the Smartcard into the ID file.

Version - Must be 0 for this version of the structure.

dwSize -The size of the memory block including this structure.

dwUnused - Unused.

retIDLen - The ID length.

retLabelLen - The label length.

retCertLength - The certificate length.

IDOffset  - The key identifier, common to the X.509 certificate and the 
associated private key.

LabelOffset - The certificate's label, defined by the PKCS #11 specification as 
a string "intended to assist users in browsing". 

CertOffset -  The X.509 certificate.

**See Also :**
[SC_manip_xxx](/domino-c-api-docs/reference/Symb/SC_manip_xxx)
[SECManipulateSC](/domino-c-api-docs/reference/Func/SECManipulateSC)
---
