##### Data Type : User Registration
##### REG_PERSON_INFO - Structure that defines person registration information.
---
##### #include <reg.h>
**Description :**
This structure defines person registration information for the REGNewPerson 
function.  The entire structure must
be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):
Size   Size of this structure - must be initialized with sizeof 
(REG_PERSON_INFO)
LastName   Last name of the new person.
FirstName   First name of the new person.
MiddleName  Middle name of the new person.
OrgUnit   Organizational unit of the new person.
ShortName   Short name of the new person.
AlternateName  Alternate name of the new person.
AltOrgUnit   Alternate org unit of the new person.
InternetAddress  The internet address of the new person.
Password     (Optional).  The password for the new server.
PasswordQuality  Quality of password required for this server (0 - 16).
INetKeyWidth  (Optional) The width of the internet key in bits (see 
fREGExtCreateINetKeyPair) Valid values are:
	    0 - default
	    1024
AltLanguage  The alternate language of the new person.
PreferredLanguage  The preferred language of the new person.
ProfileName    (Optional).  Setup profile name(s).
pGroupList     (Optional).  A pointer to a list of groups to add the new person 
to, constructed with ListAllocate and ListAddEntries. 
ExplicitPolicy  Explicit policy to assign to the new person(and/or the explicit 
policy to use when registering the new person (see fREGExtRegUsingPolicy).
PolicyOverride  Callback function used when registering person via policy (see 
fREGExtRegUsingPolicy) as a hook to modify registration items after policy 
evaluation but before      registration processing.
	
	   NOTE: You should consider all memory passed back to be read only, 
you should change pointers 
	    to point to your memory, you should not change callback memory:
	
	   Example:  To change the policy derived roaming subdirectory.
	
	   Don't do change callback memory buffer:
	    Cstrcpy (PersonInfo->RoamingInfo->SubDirectory, "your new sub 
directory");

	   Make the callback pointer point to your buffer:
	    Cstrcpy (szYourBuffer, "your new sub directory");
	    PersonInfo->RoamingInfo->SubDirectory = szYourBuffer;

Flags     Flags that are set to specify options.  See Symbolic Value, fREGxxx, 
in this reference.
FlagsExt     Flags that are set to specify options.  See Symbolic Value, 
fREGExtxxx, in this reference.
MailInfo   (Optional) Pointer to a REG_MAIL_INFO_EXT strucutre
IDInfo   (Optional) Pointer to a REG_ID_INFO structure
MiscInfo   (Optional) Pointer to a REG_MISC_INFO structure
RoamingInfo  (Optional) Pointer to a REG_ROAMING_INFO structure
phRetPersonNote  (Optional) Pointer to receive the note handle of the new 
person document if the caller has specified the REGExtFlag 
fREGExtReturnPersonNote.  Please see fREGExtxxx.
phRetPersonNoteNAB (Optional) Pointer to receive the database handle of the 
database where the new person document was created.
Reserved   Reserved - must be 0
pReserved   Reserved - must be NULL
   ForeignDN;       Distinguished name of the entry in a non-domino repository 
(i.e LDAP DN) in Notes format.
   phDirEntry;     /* Internal use */
**See Also :**
[fREGExtxxx](D:/md_files/fREGExtxxx.md)
[fREGxxx](D:/md_files/fREGxxx.md)
[REGNewPerson](D:/md_files/REGNewPerson.md)
---
