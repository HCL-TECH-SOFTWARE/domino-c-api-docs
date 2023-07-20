##### Data Type : LDAP
##### timeval - LDAP time value structure
---
```
#include <ldap.h>
```

**Definition :**
```
/*
  *   Time structure
  */

#if defined(UNIX)
#include <sys/time.h>
/* timeval is defined in <winsock2.h>, inc\wsock16.h, and inc\wsock32.h for 
Windows builds.*/
#elif !defined(W)
typedef struct timeval 
	{
	long tv_sec;  /* seconds */
	long tv_usec; /* and microseconds */
	} timeval;

#endif
```

**Description :**

Implementations of the LDAP API MUST ensure that the struct timeval type is by default defined as a consequence of including the ldap.h header.  Because struct timeval is usually defined in one or more system headers, it is possible for header conflicts to occur if ldap.h also defines it or arranges for it to be defined by including another header.  Therefore, applications MAY want to arrange for struct timeval to be defined before they include ldap.h.  To support this, the ldap.h header MUST NOT itself define struct timeval if the preprocessor symbol LDAP_TYPE_TIMEVAL_DEFINED is defined before ldap.h is included.


**See Also :**
---
