##### Symbolic Value : Smartcards
##### SC_manip_xxx - Opcodes defined for SECManipulateSC
---
```
#include <kfm.h>
```
**Description :**

SC_manip_GetVersion:        Get the version of the specification.

                                  Input Parameters:
                                        pContext     - Unused
                                        pdwFlags     - Unused
                                        pdwParam1    - points to a DWORD
                                        pvParam2     - Unused

                                  Output Parameters:
                                        *pdwParam1   - Filled with the version 
of the specification. 0 for 6.0.2

                             SC_manip_GetVersion is the only opcode that can be 
called without a valid SCMCTX.

SC_manip_InitializeContext:  Initialize a Smartcard context.

                                  Input Parameters:
                                        pContext     - Address of a NULLSCMCTX. 
See NULLSCMCTX
                                        pdwFlags     - Unused
                                        pdwParam1    - Unused
                                        pvParam2     - Unused

                                  Output Parameters:
                                        *pContext    - Filled with the 
initialized SCMCTX

                             SC_manip_InitializeContext allocates a SCMCTX and 
initializes the PKCS #11 code. 
                             Returns ERR_BSAFE_SC_INVALID_CONFIG if the local 
smartcard config is incorrect; 
                             Returns ERR_BSAFE_INSERT_SMARTCARD if a token is 
not in the slot.
                             If multiple slots are provided by the PKCS #11 
DLL, this uses the first one.

SC_manip_TerminateContext:   Terminates the Smartcard code.

                                  Input Parameters:
                                        pContext     - Valid context.
                                        pdwFlags     - Unused
                                        pdwParam1    - Unused
                                        pvParam2     - Unused

                                  Output Parameters:
                                        *pContext    - Zeroed.

                             Terminates the Smartcard code, cleans up the ID 
file if any, frees the SCMCTX, and zeroes 
                             *pContext.

SC_manip_CheckCard:          Check the current Smartcard.

                                  Input Parameters:
                                        pContext      - Valid context
                                        pdwFlags      - Unused
                                        pdwParam1     - Unused
                                        pvParam2      - Unused

                                  Output Parameters:
                                        None

                             CheckCard determines if the current smartcard can 
support Notes properly, and will return
                             error codes for any potential problems that it can 
detect. This does not check for free space 
                             on the card.

                                  ERR_BSAFE_SC_INVALID_CONFIG   - Notes is not 
configured to use a smartcard reader. 
                                                                  Does the 
PKCS11_Library notes.ini variable contains the
                                                                  path to your 
PKCS#11 DLL? 
                                  ERR_BSAFE_INSERT_SMARTCARD    - No card is 
present in the reader
                                  ERR_BSAFE_SC_UNSUPPORTED_FUNC - The card 
doesn't support multiple concurrent sessions
                                  ERR_BSAFE_SC_KEY_CREATE       - The card 
doesn't provide the cryptographic capabilities 
                                                                  required by 
Notes. 

SC_manip_EnterIDFile:       Opens the indicated ID file.

                                  Input Parameters:
                                        pContext       - Valid context
                                        pdwFlags       - Unused
                                        *pdwParam1     - Length of the string 
in pvParam2
                                        pvParam2       - BYTE*; null-terminated 
string holding path to the ID file to be 
                                                         opened

                                  Output Parameters:
                                        None

                             Opens the indicated ID file and stores the hKFC in 
the SCMCTX. Will prompt for the ID file if
                             none is provided and the caller  has a valid 
prompt set -- there is no console prompt for an
                             ID file. If the ID is smartcard-enabled and 
SC_manip_EnterPIN was previously called, the ID 
                             file will be unlocked and opened for write.   This 
OpCode may be called repeatedly on a 
                             single context, effective switching the ID file 
being used. SC_manip_InitializeContext 
                             allocates a SCMCTX and initializes the PKCS #11 
code. 

SC_manip_EnterPIN:           Logs the user into the Smartcard.

                                  Input Parameters:
                                        pContext       - Valid context
                                        pdwFlags       - Unused
                                        *pdwParam1     - PIN length
                                        pvParam2       - BYTE*; null-terminated 
string containing the PIN for the current 
                                                         Smartcard

                                  Output Parameters:
                                        None

                             If the token has a protected authentication path, 
this will trigger the protected authentication
                             path. Otherwise, an explicit PIN will be passed to 
C_Login and a NULL or zero-length PIN will cause  
                             Notes to prompt for the PIN.  If 
SC_manip_EnterIDFile was previously called and that ID file is 
                             smartcard-enabled, this OpCode will unlock the ID 
file and re-open the hKFC for write.

SC_manip_SCEnableID:         Smartcard-enable the "entered" ID file with the 
current Smartcard.

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       *pdwParam1     - Password length
                                       pvParam2       - BYTE*; null-terminated 
password for the ID file

                                 Output Parameters:
                                       None

                             Obviously, must be called after 
SC_manip_EnterIDFile and SC_manip_EnterPIN. If a NULL or zero-length 
                             password is passed in, Notes will prompt for the 
ID file's password. 
                             Returns ERR_BSAFE_CERT_ALREADY_IN_ID_FILE if the 
ID file is already smartcard-enabled. 

SC_manip_PushInetKey:        Pushes the private key associated with the current 
signing internet certificate onto the Smartcard. 

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       pdwParam1      - Unused
                                       pvParam2       - Unused

                                 Output Parameters:
                                       None

                             Future versions of this opcode will allow the 
administrator to specify which certificate they want
                             to push onto the Smartcard. 

SC_manip_FindMatchedCerts:   Initializes a search for importable certificates 
and private keys on a Smartcard.  

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       pdwParam1      - Must point to a DWORD
                                       pvParam2       - Unused

                                 Output Parameters:
                                       *pdwParam1     - Number of matching 
certs found

                             The number of importable certs found is returned 
in *pdwParam1. This function does not require an ID
                             file (nor a PIN login, although many cards will 
not yield up useful or complete information without 
                             one), as it can be used for informational purposes 
only.  The range of valid ordinals for 
                             SC_manip_GetMatchedCert and SC_manip_InetCert is 
from 0 to *pdwParam1-1 , inclusive. This OpCode can 
                             take a considerable amount of time to complete, as 
it performs a number of searches on a medium that 
                             is traditionally extremely slow.

SC_manip_GetMatchedCert:     Examines the certificates that are available for 
import from the Smartcard into the ID file.

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       *pdwParam1     - The ordinal of the pair 
to be returned. [0...N-1]
                                       pvParam2       - Optional; points to 
allocated SC_MANIP_IMPORTABLE_CERT

                                 Output Parameters:
                                       *pdwParam1     - Returns the size 
used/needed by the SC_MANIP_IMPORTABLE_CERT
                                       *pvParam2      - If non-NULL and 
sufficiently large, filled in SC_MANIP_IMPORTABLE_CERT

                             This must be called after 
SC_manip_FindMatchedCerts, as it relies on the information that was stored 
                             in the SCMCTX.

SC_manip_ImportInetCert:     Reads the indicated certificate from the Smartcard.

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       *pdwParam1     - The ordinal of the pair 
to be imported
                                       pvParam2       - Unused

                                 Output Parameters:
                                       None

                             Reads the indicated certificate from the 
Smartcard, and stores the certificate, public key, and a 
                             reference to the private key in the Notes ID file. 
If the certificate can be used for signing, then 
                             it will become the default S/MIME signing 
certificate. Must be called after SC_manip_EnterIDFile, 
                             SC_manip_EnterPIN, and SC_manip_FindMatchingCerts.


SC_manip_RefreshTokenInfo    Refreshes the token identification information 
that is stored in the ID file.

                                 Input Parameters:
                                       pContext       - Valid context
                                       pdwFlags       - Unused
                                       *pdwParam1     - Unused 
                                       pvParam2       - Unused

                                 Output Parameters:
                                       None

                             Must be called after SC_manip_EnterIDFile and 
SC_manip_EnterPIN.

SC_manip_PushKyrKey          Pushes the private key from an SSL keyring file 
onto a smartcard or a PKCS#11-based cryptographic
                             accelerator.
                                 
                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - NULL
                                       pdwParam1      - NULL
                                       pvParam2       - Path to keyring file

                                 Output Parameters:
                                       None

                             Pushes the private key from an SSL keyring file 
onto a smartcard or, more likely, a PKCS#11-based 
                             cryptographic accelerator.  SC_manip_PushKyrKey 
can only be called if the server's ID file has 
                             already been smartcard-enabled, potentially via 
SC_manip_SCEnableID, and it must be called after 
                             InitializeContext, SC_manip_EnterIDFile, and 
SC_manip_EnterPIN. 

SC_manip_PushNotesKey        Pushes a "large" (1024 or 2048-bit) Notes key onto 
a smartcard. 
                                  
                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - NULL
                                       pdwParam1      - NULL
                                       pvParam2       - NULL

                                 Output Parameters:
                                       None

                             Writes the (BER-encoded) Notes domestic private 
key to a  smartcard, make the key recoverable, 
                             and replaces the key in the ActiveUDO with a 
pointer to the key on the card.  
                             SC_manip_PushNotesKey can only be called if the ID 
file has already been smartcard-enabled, 
                             potentially via SC_manip_SCEnableID, and it must 
be called after InitializeContext,    
                             SC_manip_EnterIDFile, and SC_manip_EnterPIN.

    SC_manip_EnterIDPassword    Unlock the non-smartcard-enabled ID file 
entered through EnterIDFile with the supplied password. 
                                If *pdwParam1 and pvParam2 are not passed in, 
the user will be prompted for the password, if  
                                possible.

                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - NULL
                                       pdwParam1      - Length of ID file 
password, if any
                                       pvParam2       - Points to ID file 
password, if any

                                 Output Parameters:
                                       None

                                SC_manip_EnterIDPassword is used before the 
SC_manip_LockIDWithKeyRO opcode in order to unlock the 
                                ID file that is about to be smartcard-enabled, 
if the ID file was previously not smartcard-enabled.

   SC_manip_FindAllKeys         Acquire all keys from all smartcards and return 
the number of keys available to the caller.

                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - NULL
                                       pdwParam1      - Must point to a DWORD
                                       pvParam2       - NULL

                                 Output Parameters:
                                        pdwParam1      - Filled in with number 
of certs available

                                SC_manip_FindAllKeys can be used with 
SC_manip_GetMatchedCert in the same fashion as 
                                SC_manip_FindMatchedCerts to find private RSA 
keys without matching certificates.  These keys cannot
                                be imported into the ID file, due to the lack 
of matching certificates, but they can be used with 
                                SC_manip_LockIDWithKeyRO and 
SC_manip_LockIDWithKeyRnd to secure the ID file. 

   SC_manip_LockIDWithKeyRO     Smartcard-enable the ID file by encrypting it 
with a password-equivalent generated by signing a 
                                random seed value. This opcode will work with 
most read-only ID files. 
                                This is a valid upgrade path for regular 
smartcard-enabled ID files. SC_manip_EnterIDPassword must 
                                be used before calling this function with 
non-smartcard-enabled ID files.

                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - Currently unused
                                       pdwParam1      - Ordinal of the key to 
use
                                       pvParam2       - Currently unused

                                 Output Parameters:
                                       None

                                This is currently the recommended technique for 
protecting an ID file with a smartcard. This opcode 
                                uses the same mechanism as the  "Lock ID with 
Key on Smartcard" menu option that is accessible from 
                                the "Other Actions" button on the "Your 
Certificates" pane of the User Security Dialog when a 
                                certificate corresponding to a private key on a 
smartcard has been selected.   An ID file protected 
                                in this fashion cannot be used with a Notes 
client or Domino server before ND7, but can be recovered 
                                through the ID File Recovery process. 

   SC_manip_LockIDWithKeyRnd    Smartcard-enable the ID file by encrypting it 
with a symmetric key that is wrapped by a key on the 
                                token. This is a valid upgrade path for regular 
smartcard-enabled ID files. SC_manip_EnterIDPassword 
                                must be used before calling this function with 
non-smartcard-enabled ID files.

                                 Input Parameters:
                                       pContext       - Must have been be 
initialized
                                       pdwFlags       - Currently unused
                                       pdwParam1      - Ordinal of the key to 
use
                                       pvParam2       - Currently unused

                                 Output Parameters:
                                       None

                                This technique will only work with a small set 
of smartcards with substantially above-average 
                                cryptographic support, including performing 
symmetric encryption in hardware; in most cases,  
                                SC_manip_LockIDWithKeyRO should be used 
instead. As ID File Recovery will not be able to recover an 
                                ID file protected with this technique, this 
function has been effectively deprecated in favor of 
                                SC_manip_LockIDWithKeyRO. 

**See Also :**
[SC_MANIP_IMPORTABLE_CERT](/reference/Data/SC_MANIP_IMPORTABLE_CERT)
[SECManipulateSC](/reference/Func/SECManipulateSC)
---
