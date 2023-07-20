##### Symbolic Value : Domino Upgrade Services
##### fDUSxxx - Flags which specify Migrate Options for a given DUS.
---
```
#include <dus.h>
```

**Symbolic Values :**

	fDUSDoMailConversion	  -  Mail exists to convert and should be converted.

	fDUSGenerateRandPWs	  -  Generate random passwords if no user password supplied.

	fDUSAdvancedDlg	  -  Advanced dialog is available DUSAdvancedDlg is implemented.

	fDUSUseFullNameProvided	  -  Use the full name provided as a secondary Domino user name.

	fDUSAllowEmptyGroups	  -  Allow addition of empty groups to the Domino Directory (Server's Address book).

	fDUSMailConversionOnly	  -  Only convert mail for this migrating user. The person document and ID file must already exist in the Domino Directory in this case.

	fDUSAddAdminToACL	  -  Add the administrator to the mail file access control list during registration mail creation. This allows mail conversion access to mail file in two pass migration scenarios (directory migrated first, mail converted at a later date).

	fDUSOverwritePasswords	  -  Generate random password for every user, always overwriting any existing password.

	fDUSUseFilters	  -  If the flag is set, user will be allowed to type other filters, otherwise, (s)he will only be able to choose among default filters, and options such as "All Users and Groups", "All Users" and "All Groups".

	fDUSExternalEntry	  -  If flags is set for a group member, it will not be registered in Notes, only added to the group.

	fDUSIgnoreEntry	  -  If flags is set for a group member, it will neither be registered in Notes, nor added to the group.


**Description :**

These flags further define what is needed for this particular DUS being activated.  With the exception fo fDUSAdvancedDlg, all other options are listed in the Domino User Registarion 'People and Groups Migration' dialog under 'Migration Options'. 


**See Also :**
[DUSStart](/domino-c-api-docs/reference/Func/DUSStart)
---
