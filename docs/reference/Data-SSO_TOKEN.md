##### Data Type : User Registration
##### SSO_TOKEN - Structure that defines a Single Sign-On token.
---
##### #include <bsafe.h>
**Description :**
This structure contains information representing an authentication token used 
for Single Sign-On. The typical use is to store this information in a browser 
'cookie' for interoperability with Domino protocols that support Single Sign-On 
(IE: HTTP and DIIOP), as well as IBM WebSphere Advanced Server.

mhName  - MEMHANDLE to a null-terminated name for the token when set as a 
cookie. Access with OSMemoryLock.
mhDomainList - MEMHANDLE to a list of null-delimited DNS domains for the token 
when set as a cookie. Access with OSMemoryLock.
wNumDomains - Total number of domains contained in the mhDomainList member.
bSecureOnly - BOOL recommending that the token only be set on a secure 
connection.
mhData  - MEMHANDLE to a the null-terminated token data.

See the Domino Administrators Guide for information on configuring Single 
Sign-On.

**See Also :**
[SECTokenFree](D:/md_files/SECTokenFree.md)
[SECTokenGenerate](D:/md_files/SECTokenGenerate.md)
[SECTokenValidate](D:/md_files/SECTokenValidate.md)
---
