##### Data Type : Basic Encoding Rules
##### BerElement - Holds date and state information about encoded data.
---
##### #include <lber.h>
**Description :**
BerElement represents data encoded using the Basic Encoding Rules (BER). 
BerElement is not completely defined in ldap.h because the fields within the 
structure are not intended to be accessible to clients. The BerElement 
structure is an opaque structure. It contains not only a copy of the encoded 
value, but also state information used in encoding or decoding.  Applications 
cannot allocate their own BerElement structures.  The internal state is neither 
thread-specific nor locked, so two threads should not manipulate the same 
BerElement value simultaneously.

A single BerElement value cannot be used for both encoding and decoding.
**See Also :**
[ldap_first_attribute](D:/md_files/ldap_first_attribute.md)
---
