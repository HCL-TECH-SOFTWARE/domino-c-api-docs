##### Function : LDAP
##### ldap_delete_s - Initiate a synchronous ldap delete operation.
---
##### #include <ldap.h>
int LNPUBLIC **ldap_delete_s(**

	LDAP *ld,
	const char *dn);
**Description :**
This function will initiate a synchronous ldap delete operation.

Note that the entry to delete must be a leaf entry (i.e., it must have no 
children). Deletion of entire subtrees in a single operation is not supported 
by LDAP.

Implemented as a macro:

#define ldap_delete_s(ld, dn) ND_ldap_delete_s((ld), (dn))
**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to delete.  If NULL, a zero length DN is sent to the server.

Output :
(routine)  -  LDAP_SUCCESS  - If the request was successfully sent, or another LDAP result code if not.


**Sample Usage :**
```
    if (( rc = ldap_delete_s( ld, ndn )) != LDAP_SUCCESS )
    {
         /* If entry does not exist, fine.  Ignore this error. */
         if ( rc == LDAP_NO_SUCH_OBJECT )
         {
              printf( "\tEntry \"%s\" is not in the directory.  "
              "\n\t  No need to delete.\n", ndn );
         }
         else
         {
             ldap_perror( ld, "ldap_delete_s" );
             NotesTerm();
             return( 1 );
         }
    }
    else
    {
          printf( "\tDeleted entry \"%s\".\n", ndn );
    }
```
**See Also :**
[](D:/md_files/.md)
---
