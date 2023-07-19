##### Symbolic Value : LDAP
##### LDAP_xxx(1) - Possible error codes that can be returned.
---
```
#include <ldap.h>
```

**Symbolic Values :**

	LDAP_SUCCESS	  -  Success.

	LDAP_OPERATIONS_ERROR	  -  Operations error.

	LDAP_PROTOCOL_ERROR	  -  Protocol error.

	LDAP_TIMELIMIT_EXCEEDED	  -  Time limit exceeded.

	LDAP_SIZELIMIT_EXCEEDED	  -  Size Limit exceeded.

	LDAP_COMPARE_FALSE	  -  Compare was false.

	LDAP_COMPARE_TRUE	  -  Compare was true.

	LDAP_STRONG_AUTH_NOT_SUPPORTED	  -  Strong authentication is not supported.

	LDAP_STRONG_AUTH_REQUIRED	  -  Strong authentication is required.

	LDAP_PARTIAL_RESULTS	  -  The error code was never officially supported in LDAPv2, nor is it supported in LDAPv3. However, we'll keep it around since practically all clients which bind v2 expect UMich-style referrals.

	LDAP_REFERRAL	  -  Referral. Error new in LDAPv3.

	LDAP_ADMINLIMIT_EXCEEDED	  -  Admin limit exceeded. Error new in LDAPv3.

	LDAP_UNAVAILABLE_CRITICAL_EXTENSION	  -  Unavailable critical extension. Error new in LDAPv3.

	LDAP_CONFIDENTIALITY_REQUIRED	  -  Confidentiality required. Error new in LDAPv3.

	LDAP_SASL_BIND_IN_PROGRESS	  -  SASL bin in progress. Error new in LDAPv3.

	LDAP_NO_SUCH_ATTRIBUTE	  -  No such attribute. Error indicates an attribute problem.

	LDAP_UNDEFINED_TYPE	  -  Undefined type. Error indicates an attribute problem.

	LDAP_INAPPROPRIATE_MATCHING	  -  Inappropriate matching. Error indicates an attribute problem.

	LDAP_CONSTRAINT_VIOLATION	  -  Constraint violation. Error indicates an attribute problem.

	LDAP_TYPE_OR_VALUE_EXISTS	  -  Type or value already exists. Error indicates an attribute problem.

	LDAP_INVALID_SYNTAX	  -  Invalid syntax. Error indicates an attribute problem.

	LDAP_NO_SUCH_OBJECT	  -  No such object. Error indicates a naming problem.

	LDAP_ALIAS_PROBLEM	  -  Alias problem. Error indicates a naming problem.

	LDAP_INVALID_DN_SYNTAX	  -  Invalid distinguished name syntax. Error indicates a naming problem.

	LDAP_IS_LEAF	  -  Is leaf. Error indicates a naming problem, not used in LDAPv3.

	LDAP_ALIAS_DEREF_PROBLEM	  -  Alias deref problem. Error indicates a naming problem.

	LDAP_INAPPROPRIATE_AUTH	  -  Inappropriate Authentication. Error indicates a security problem.

	LDAP_INVALID_CREDENTIALS	  -  Invalid credentials. Error indicates a security problem.

	LDAP_INSUFFICIENT_ACCESS	  -  Insufficient access. Error indicates a security problem.

	LDAP_BUSY	  -  Busy. Error indicates a service problem.

	LDAP_UNAVAILABLE	  -  Unavailable. Error indicates a service problem.

	LDAP_UNWILLING_TO_PERFORM	  -  Unwilling to perform. Error indicates a service problem.

	LDAP_LOOP_DETECT	  -  Loop detect. Error indicates a service problem.

	LDAP_NAMING_VIOLATION	  -  Naming violation. Error indicates an update problem.

	LDAP_OBJECT_CLASS_VIOLATION	  -  Object class violation. Error indicates an update problem.

	LDAP_NOT_ALLOWED_ON_NONLEAF	  -  Not allowed on non-leaf. Error indicates an update problem.

	LDAP_NOT_ALLOWED_ON_RDN	  -  Not allowed on a relative distinguished name. Error indicates an update problem.

	LDAP_ALREADY_EXISTS	  -  Already exists. Error indicates an update problem.

	LDAP_NO_OBJECT_CLASS_MODS	  -  No object class modifications. Error indicates an update problem.

	LDAP_RESULTS_TOO_LARGE	  -  Results too large. Error indicates an update problem, reserved for CLDAP.

	LDAP_AFFECTS_MULTIPLE_DSAS	  -  Affects multiple DSAS. Error indicates an update problem (LDAPv3).


**Description :**

Many of the LDAP API routines return result codes, some of which indicate local API errors and some of which are LDAP resultCodes that are returned by servers.  All of the result codes are non-negative integers.


**See Also :**
---
