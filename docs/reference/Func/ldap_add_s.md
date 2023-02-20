##### Function : LDAP
##### ldap_add_s - Initiate a synchronous ldap add operation.
---
```
#include <ldap.h>
int LNPUBLIC ldap_add_s(

	LDAP *ld,
	const char *dn,
	LDAPMod **attrs);
```
**Description :**

This function will initiate a synchronous ldap add operation.

Note that the parent of the entry being added must already exist or the parent 
must be empty (i.e., equal to the root DN) for an add to succeed.

Implemented as a macro:

#define ldap_add_s(ld, dn, attrs) ND_ldap_add_s((ld), (dn), (attrs))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to add.  If NULL, a zero length DN is sent to the server.

attrs  -  The entry's attributes, specified using the LDAPMod structure defined for ldap_modify. The mod_type and mod_vals fields MUST be filled in.  The mod_op field is ignored unless ORed with the constant LDAP_MOD_BVALUES, used to select the mod_bvalues case of the mod_vals union. (See: ldap_modify, mod_xxx; LDAP_MOD_xxx)

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.



**Sample Usage :**
```
    if (( rc = ldap_add_s( ld, dn, mods )) != LDAP_SUCCESS )
    {
	/* If entry exists already, fine.  Ignore this error. */
	if ( rc == LDAP_ALREADY_EXISTS )
	{
	 printf( "Entry \"%s is already in the directory.\n", dn );
	}
	else
	{
	 ldap_perror( ld, "ldap_add_s" );
	 free_mods( mods );
	 NotesTerm();
	 return( 1 );
	}
    }
    else
    {
       printf( "\tAdded entry \"%s\".\n", dn );
    }
```
**See Also :**
[ldap_modify](/reference/Func/ldap_modify)
[LDAP_MOD_xxx](/reference/Symb/LDAP_MOD_xxx)
[mod_xxx](/reference/Symb/mod_xxx)
---
