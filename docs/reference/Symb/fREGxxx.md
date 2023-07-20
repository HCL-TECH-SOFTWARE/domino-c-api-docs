##### Symbolic Value : User Registration
##### fREGxxx - Specify options during registration of new servers, workstations, and users and during the creation of new certifiers.
---
```
#include <reg.h>
```

**Symbolic Values :**

	fREGCreateIDFileNow	  -  This flag should be set during REGNewWorkstation, REGNewServer, REGNewUser, and REGNewCertifier if an ID file should be created.

	fREGUSARequested	  -  This flag should be set for all ID's being created for use in the US or Canada.

	fREGCreateMailFileNow	  -  This flag should be set during REGNewWorkstation, REGNewServer, REGNewUser, and REGNewCertifier to create a mail file during registration (it may be created later if , for instance, the mail server is not available).

	fREGCreateAddrBookEntry	  -  This flag should be set during REGNewWorkstation, REGNewServer, REGNewUser, and REGNewCertifier to create or modify an Address book or Domino Directory entry.

	fREGOkayToModifyID	  -  If this flag is not set during REGNewWorkstation, REGNewServer, REGNewUser, or REGNewCertifier and fREGCreateIDFileNow is set and the requested ID file exists, an error will be returned. If the flag is set, the existing ID file will be overwritten. Certificates and encryption keys that were in the existing ID file will no longer exist in the resulting ID file.

	fREGOkayToModifyAddrbook	  -  If this flag is not set during REGNewWorkstation, REGNewServer, REGNewUser, and REGNewCertifier and if fREGCreateAddrBookEntry is set and a user with the same name as the new user is found in the Domino Directory on the registration server, an error will be returned. If the flag is set, the existing Address book or Domino Directory entry will be modified, e.g. non-optional fields will not be overwritten if a null string is passed.

	fREGSaveIDInFile	  -  For use with REGNewWorkstation, REGNewUser, or REGNewServer. Save the ID in a file. The IDFilename parameter must be specified. If this flag is NOTspecified and no IDFileName is specified, then the ID will be saved in the Address book or Domino Directory.

	fREGCreateLimitedClient	  -  For use with REGNewWorkstation or REGNewUser - create a Lotus Notes Mail user.

	fREGCreateDesktopClient	  -  For use with REGNewWorkstation or REGNewUser - create a Lotus Notes Desktop user.

	fREGSaveIDInAddrBook	  -  For use with REGNewWorkstation, REGNewUser, or REGNewServer. Save the ID in the Address book or Domino Directory. If this flag is NOTspecified and an IDFileName is specified, then the ID will be saved in the specified IDFileName. However, if ID vault is enabled on the registration server, ID file will be stored in the vault; The only way to override ID vault is to explicitly specify fREGSaveIDInFile flag.

	fREGCreateMailFileUsingAdminp	  -  Use admin process to create mail file. NOTE: fREGCreateMailFileUsingAdminp and fREGCreateMailFileNow are mutually exclusive. If both flags are specified, then fREGCreateMailFileNow is the action that will be performed.

	fREGSetInternetPassword	  -  Store the password for use as the Internet password. User only

	fREGSetDB2Access	  -  Set DB2 access. Server only


**Description :**

These values specify options during registration of new servers, workstations, and users and during the creation of new certifiers.


**See Also :**
[REGNewCertifier](/domino-c-api-docs/reference/Func/REGNewCertifier)
[REGNewServer](/domino-c-api-docs/reference/Func/REGNewServer)
[REGNewWorkstation](/domino-c-api-docs/reference/Func/REGNewWorkstation)
[REGNewUser](/domino-c-api-docs/reference/Func/REGNewUser)
---
