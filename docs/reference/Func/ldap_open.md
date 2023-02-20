##### Function : LDAP
##### ldap_open - Initialize a session with an LDAP server.
---
```
#include <ldap.h>
LDAP * LNPUBLIC ldap_open(

	const char *host,
	int  port);
```
**Description :**

This function initializes a session with an LDAP server and returns a "session 
handle," a pointer to an opaque structure that MUST be passed to subsequent 
calls pertaining to the session. This routine returns a NULL if the session 
cannot be initialized.

Unlike ldap_init, ldap_open attempts to make a server connection before 
returning to the caller.  A more complete description can be found in RFC 1823.

Implemented as a macro:

#define ldap_open(host, port) ND_ldap_open((host), (port))

**Parameters :**
Input :
host  -  A space-separated list of hostnames or dotted strings representing the IP address of hosts running an LDAP server to connect to. Each hostname in the list MAY include a port number which is separated from the host itself with a colon (:) character.  The hosts will be tried in the order listed, stopping with the first one to which a successful connection is made.

Note: A suitable representation for including a literal IPv6[10] address in the hostname parameter is desired, but has not yet been determined or implemented in practice.

port  -  The TCP port number to connect to. The default LDAP port of 389 can be obtained by supplying the value zero (0) or the macro LDAP_PORT (389).  If a host includes a port number then this parameter is ignored.

Output :
(routine)  -  A pointer to a session handle.

NULL - If the session cannot be initialized.



**See Also :**
[ldap_init](/reference/Func/ldap_init)
---
