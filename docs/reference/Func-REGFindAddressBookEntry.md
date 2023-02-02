##### Function : User Registration
##### REGFindAddressBookEntry - Finds the NOTEID of a Certifier, Server, or User entry in a given  Address book or Domino Directory (Server's Address book).
---
##### #include <reg.h>
STATUS LNPUBLIC **REGFindAddressBookEntry(**

	DBHANDLE  hAddressBook,
	char far *NameSpace,
	char far *Name,
	NOTEID far *EntryNoteID);
**Description :**
This function finds the NOTEID of an existing Certifier, Server, or User entry 
in a given Address book or Domino Directory (Server's Address book).
**Parameters :**
Input :
hAddressBook  -  Handle of a Address Book or Domino Directory obtained from a call to NSFDbOpen (must be closed with NSFDbClose).

NameSpace  -  "$Users", "$Servers" or "$Certifiers".  Only these values are valid.

Name  -  A pointer to the user's, server's, or certifier's full name that is to be looked up.  Hierarchical names must be in canonical format.

Output :
(routine)  -  Return status from this call - indicates either success or what the error is.  The return codes include:

NOERROR - No error.
ERR_xxx - NSF errors.


EntryNoteID  -  Returned note ID of the Address Book or Domino Directory Entry.  If the Entry is not found,  *EntryNoteID is 0 and  NOERROR is returned.

**Sample Usage :**
```

/* Open the Address book or Domino Directory database. */

if (error = NSFDbOpen (FullDBPath, &hNABook))
{
   printf("Error: unable to open N&A book '%s'.\n", FullDBPath);
   return (ERR(error));
}

/* Look up the Organization certifier entry */

if (error = REGFindAddressBookEntry (hNABook, 
                                     "$Certifiers", 
                                     DNAME_ORG_CERT,
                                     &NoteID))
{
   printf("Unable to find orgainizational certifier entry in N&A book.\n");
   OSLoadString(NULLHANDLE, ERR(error), szErr, MAXSPRINTF-1);
   printf("\n\n%s\n",szErr);
}
```
**See Also :**
[NAMELookup](D:/md_files/NAMELookup.md)
---
