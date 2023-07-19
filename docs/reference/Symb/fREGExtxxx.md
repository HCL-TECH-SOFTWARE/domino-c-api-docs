##### Symbolic Value : User Registration
##### fREGExtxxx - Flag options for REGNewUser.
---
```
#include <reg.h>
```

**Symbolic Values :**

	fREGExtCreateMailFTIndex	  -  This flag should be set during REGNewUser for mail creation.

	fREGExtReturnPersonNote	  -  This flag is set during REGNewUser if the caller wants the note handle of the new person document.

	fREGExtEnforceUniqueShortName	  -  Use this flag to enforce the shortname of the user.

	fREGExtRoamingUserNow	  -  Create roaming files now - person is created with ability to roam.

	fREGExtRoamingFilesUsingAdminp	  -  Create roaming files via the administration process - person is created with ability to roam.

	fREGExtCreateINetKeyPair	  -  Add the INetPublicKey to the person document.

	fREGExtMailReplicasUsingAdminp	  -  Create mail replicas via the administration process.

	fREGExtRoamingReplicasUsingAdminp	  -  Create roaming replicas via the administration process.

	fREGExtRegUsingPolicy	  -  Person registration will use the policy settings (registration) as parameter values for registration.


**Description :**

These values specify options for the FLAGS parameter of REGNewUser.


**See Also :**
[REGNewUser](/domino-c-api-docs/reference/Func/REGNewUser)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
---
