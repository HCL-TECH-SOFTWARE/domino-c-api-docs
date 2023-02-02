##### Function : LDAP
##### ldap_init - Initialize a session with an LDAP server.
---
##### #include <ldap.h>
LDAP * LNPUBLIC **ldap_init(**

	const char *defhost,
	int  defport);
**Description :**
This function initializes a session with an LDAP server and returns a "session 
handle," a pointer to an opaque structure that MUST be passed to subsequent 
calls pertaining to the session. This routine returns a NULL if the session 
cannot be initialized.

Implemented as a macro:

#define ldap_init(defhost, defport) ND_ldap_init((defhost), (defport))
**Parameters :**
Input :
defhost  -  A space-separated list of hostnames or dotted strings representing the IP address of hosts running an LDAP server to connect to. Each hostname in the list MAY include a port number which is separated from the host itself with a colon (:) character.  The hosts will be tried in the order listed, stopping with the first one to which a successful connection is made.

Note: A suitable representation for including a literal IPv6[10] address in the hostname parameter is desired, but has not yet been determined or implemented in practice.

defport  -  The TCP port number to connect to. The default LDAP port of 389 can be obtained by supplying the value zero (0) or the macro LDAP_PORT (389).  If a host includes a port number then this parameter is ignored.

Output :
(routine)  -  A pointer to a session handle.

NULL - If the session cannot be initialized.


**Sample Usage :**
```
    if ( (ld = ldap_init( HOST, PORT )) == NULL )
    {
	 perror( "ldap_init" );
	 NotesTerm();
	 return( 1 );
    }

```
**See Also :**
[ldap_open](D:/md_files/ldap_open.md)
---
