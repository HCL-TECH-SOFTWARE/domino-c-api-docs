##### Data Type : Administration Process
##### ADMINReqParams - Parameters of an administration request
---
```
#include <adminp.h>
```

**Definition :**

typedef struct {
   DWORD Flags;             /* Reserved */
   DWORD dwDeleteInNABType; /* DELETE_xxxx_IN_NAB defined above */
	char far *chGroupName;   /* if dwDeleteInNABType equals
                               DELETE_PERSON_IN_NAB a pointer to a
                               group (termination perhaps) to have
                               the name added */
   char far *chAltName;     /* if dwDeleteInNABType equals
                               DELETE_PERSON_IN_NAB a pointer to
                               the person's Alternate Name */
   char far *chFirstName;   /* for ADMINReqMoveComplete, a pointer
                               to a new first name for the
                               person */
   char far *chMiddleInitial; /* for ADMINReqMoveComplete, a
                               pointer to a new middle initial for
                               the person */
   char far *chLastName;    /* for ADMINReqMoveComplete, a pointer
                               to a new last name for the person */
   char far *chAltCommonName; /* for ADMINReqRename,
                               ADMINReqRecertify, and
                               ADMINReqMoveComplete, a pointer to a
                               new alternate common name for the
                               person */  
   char far *chAltOrgUnitName; /* for ADMINReqRename,
                               ADMINReqRecertify, and
                               ADMINReqMoveComplete, a pointer to a
                               new alternate org unit for the
                               person */  
   char far *chAltLanguage; /* for ADMINReqRename,
                               ADMINReqRecertify, and
                               ADMINReqMoveComplete, a pointer to a
                               new alternate language for the
                               person */ 
   BOOL fDontUseV1ChangeRequest; /* for ADMINReqMoveUserInHier,
                               TRUE indicates that support for a
                               simultaneous hierarchy move and name
                               change.  Recognized only by v5.02
                               and above clients and servers */

/* 5.x structure ended here.  The following fields were added for Rnext */

	DBHANDLE dbhDirectory; /* for ADMINReqDeleteInNAB, a handle to 
	       the directory from which the Person, 
	       Server, or Group is to be deleted if 
	       the target directory is not names.nsf */

} ADMINReqParams;

**Description :**

This structure contains the parameters of an administration request.  When setting this structure, first initialize the values of structure members to 0.


**See Also :**
[ADMINReqChkAccessMoveReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessMoveReplica)
[ADMINReqChkAccessNewReplica](/domino-c-api-docs/reference/Func/ADMINReqChkAccessNewReplica)
[ADMINReqDeleteInACL](/domino-c-api-docs/reference/Func/ADMINReqDeleteInACL)
[ADMINReqDeleteInNAB](/domino-c-api-docs/reference/Func/ADMINReqDeleteInNAB)
[ADMINReqMoveComplete](/domino-c-api-docs/reference/Func/ADMINReqMoveComplete)
[ADMINReqMoveUserInHier](/domino-c-api-docs/reference/Func/ADMINReqMoveUserInHier)
[ADMINReqRecertify](/domino-c-api-docs/reference/Func/ADMINReqRecertify)
[ADMINReqRename](/domino-c-api-docs/reference/Func/ADMINReqRename)
[ADMINReqUpgradeToHier](/domino-c-api-docs/reference/Func/ADMINReqUpgradeToHier)
---
