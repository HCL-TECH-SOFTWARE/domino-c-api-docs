##### Function : LDAP
##### ldap_compare_ext_s - Synchronous compare attribute value assertion with controls.
---
```
#include <ldap.h>
int LNPUBLIC ldap_compare_ext_s(

	LDAP *ld,
	const char *dn,
	const char *attr,
	const struct berval *bvalue,
	LDAPControl **sctrls,
	LDAPControl **cctrls);
```
**Description :**

This function will do a synchronous compare attribute value assertion, with 
controls, against an LDAP entry.

Implemented as a macro:

#define ldap_compare_ext_s(ld, dn, attr, bvalue, sctrl, cctrl)\
	        ND_ldap_compare_ext_s((ld), (dn), (attr), (bvalue), (sctrl), 
(cctrl))

**Parameters :**
Input :
ld  -  The LDAP session handle.

dn  -  The distinguished name of the entry to compare against.

attr  -  The attribute to compare against.

bvalue  -  The attribute value to compare against those found in the given entry. This is a pointer to a struct berval so it is possible to compare binary values.

sctrls  -  Pointer to a list of LDAP server controls.  NULL if no server controls are to be used.

cctrls  -  Pointer to a list of LDAP client controls.  NULL if no client controls are to be used.

Output :
(routine)  -  LDAP_COMPARE_TRUE, LDAP_COMPARE_FALSE  - If the operation was successful, or another LDAP result code if not.



**Sample Usage :**
```
    /* compare the value "person" against the objectclass attribute */
    printf("\n  Comparison results:\n\n");

    compAttribute = "objectclass";
    compValue = "person";
    bvalue.bv_val = compValue;
    bvalue.bv_len = strlen(compValue);

    rc = ldap_compare_ext_s( ld, DN, compAttribute, &bvalue, NULL, NULL );
    switch ( rc )
    {
         case LDAP_COMPARE_TRUE:
             printf( "\tThe value \"person\" is contained in the objectclass "
                     "attribute.\n" );
             break;
         case LDAP_COMPARE_FALSE:
             printf( "\tThe value \"person\" is not contained in the 
objectclass "
                     "attribute.\n" );
             break;
         default:
             ldap_perror( ld, "ldap_compare_s" );
    }

    /* compare the value "xyzzy" against the objectclass attribute */
    compValue = "xyzzy";
    bvalue.bv_val = compValue;
    bvalue.bv_len = strlen(compValue);

    rc = ldap_compare_ext_s( ld, DN, compAttribute, &bvalue, NULL, NULL );
    switch ( rc )
    {
         case LDAP_COMPARE_TRUE:    
             printf( "\tThe value \"xyzzy\" is contained in the objectclass "
                     "attribute.\n" );
             break;
         case LDAP_COMPARE_FALSE:
             printf( "\tThe value \"xyzzy\" is not contained in the objectclass 
"
                     "attribute.\n" );
             break;
         default:
             ldap_perror( ld, "ldap_compare_s" );
    }
```
**See Also :**
---
