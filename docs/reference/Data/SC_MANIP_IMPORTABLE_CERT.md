##### Data Type : Smartcards
##### SC_MANIP_IMPORTABLE_CERT - Structure used for SC_manip_GetMatchedCert
---
```
#include <kfm.h>
```

**Definition :**

typedef struct
{
	DWORD Version;     /* This typedef describes version 0 */
	DWORD dwSize; 
	DWORD dwUnused;
	DWORD retIDLen;
	DWORD retLabelLen;
	DWORD retCertLen;
	DWORD IDOffset;    /* Offset in bytes from beginning of structure */
	DWORD LabelOffset; /* Offset in bytes from beginning of structure */
	DWORD CertOffset;  /* Offset in bytes from beginning of structure */
	/* ID */
	/* Label */
	/* Cert */
}
SC_MANIP_IMPORTABLE_CERT;

**Description :**

SC_MANIP_IMPORTABLE_CERT is used with the SECManipulateSC OpCode SC_manip_GetMatchedCert (in SC_manip_xxx) to examine the certificates that are available for import from the Smartcard into the ID file.<br>

<ul><br>
Version - Must be 0 for this version of the structure.<br>
<br>
dwSize -The size of the memory block including this structure.<br>
<br>
dwUnused - Unused.<br>
<br>
retIDLen - The ID length.<br>
<br>
retLabelLen - The label length.<br>
<br>
retCertLength - The certificate length.<br>
<br>
IDOffset  - The key identifier, common to the X.509 certificate and the associated private key.<br>
<br>
LabelOffset - The certificate's label, defined by the PKCS #11 specification as a string &quot;intended to assist users in browsing&quot;. <br>
<br>
CertOffset -  The X.509 certificate.</ul>



**See Also :**
[SC_manip_xxx](/domino-c-api-docs/reference/Symb/SC_manip_xxx)
[SECManipulateSC](/domino-c-api-docs/reference/Func/SECManipulateSC)
---
