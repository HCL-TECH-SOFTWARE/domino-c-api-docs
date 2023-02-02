##### Symbolic Value : User
##### KFM_pubkey_xxx - Specification for the type of public key.
---
##### #include <kfm.h>
**Description :**
One of these symbols is specified in the call to SECKFMGetPublicKey.  Every 
user (North American and International) has both a Primary (long) and 
International (short) key.  The Primary key is always used for authentication 
and signing.  The International key is used if the encryptor or decryptor is an 
International user.  The Primary key is used if both the encryptor and 
decryptor are North American users.
**See Also :**
[SECKFMGetPublicKey](D:/md_files/SECKFMGetPublicKey.md)
---
