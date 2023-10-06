##### Data Type : User Registration
##### REG_PERSON_INFO - Structure that defines person registration information.
---
```
#include <reg.h>
```

**Definition :**
```
typedef struct reg_person_info
	{
	DWORD  Size;   /* size of this structure - must initialize with sizeof 
(REG_PERSON_INFO) */

	/* person name information */
	char   *LastName;
	char   *FirstName;
	char   *MiddleName;
	char   *OrgUnit;
	char   *ShortName;
	char   *AlternateName;
	char  *AltOrgUnit;
	char  *InternetAddress;

	/* person password information */
	char  *Password;
	WORD  PasswordQuality;

	/* person internet key information */
	WORD  INetKeyWidth;

	/* person language info */
	char  *AltLanguage;
	char  *PreferredLanguage;

	/* setup profile info */
	char  *ProfileName;

	/* person group membership */
	void   *pGroupList;

	/* policy information */
	char  *ExplicitPolicy;
	/* PolicyOverride function used when registering via policy 
(fREGExtRegUsingPolicy) 
	as a hook to modify registration items after policy evaluation but 
before 
	registration processing
	
	NOTE: As to not munge with internal memory, you should change pointers 
	to point to your memory, you should not change callback memory:
	
	Example:  To change the policy derived roaming subdirectory
	
	Don't do change callback memory buffer:
	 Cstrcpy (PersonInfo->RoamingInfo->SubDirectory, "your new sub 
directory");

	Make the callback pointer point to your buffer:
	 Cstrcpy (szYourBuffer, "your new sub directory");
	 PersonInfo->RoamingInfo->SubDirectory = szYourBuffer;
	
	*/
	STATUS (LNCALLBACKPTR PolicyOverride)(HCERTIFIER hCertCtx, 
	      char far **RegServer,
	      struct reg_person_info far *PersonInfo);

	/* registration flags */
	REGFlags  Flags;
	REGFlagsExt  FlagsExt;

	REG_MAIL_INFO_EXT *MailInfo;

	REG_ID_INFO  *IDInfo;
	
	REG_MISC_INFO *MiscInfo;

	REG_ROAMING_INFO *RoamingInfo;

	/* when specified with fREGExtReturnPersonNote - return the person note 
and DB handle */
	NOTEHANDLE  *phRetPersonNote;
	DBHANDLE  *phRetPersonNoteNAB;

	/* when specified, use this NoteID as the current person doc Note*/
	NOTEID	ADContactNoteID;

	DWORD Reserved[4];
	void *pReserved[4];
	char        *ForeignDN;     /* distinguished name of the entry in a 
non-domino repository (i.e LDAP DN) in Notes format */
	DIRENTRY    *phDirEntry;    /* DIRENTRY of person to be returned to 
caller, see fREGExtReturnPersonDirEntry */
	} REG_PERSON_INFO;


```

**Description :**

<br>
This structure defines person registration information for the REGNewPerson function.  The entire structure must<br>
be initialized to zero.<br>

<ul>The fields in the structure are (all fields that are not used must be NULL/O):<br>
Size			Size of this structure - must be initialized with sizeof (REG_PERSON_INFO)<br>
LastName			Last name of the new person.<br>
FirstName			First name of the new person.<br>
MiddleName		Middle name of the new person.<br>
OrgUnit			Organizational unit of the new person.<br>
ShortName			Short name of the new person.<br>
AlternateName		Alternate name of the new person.<br>
AltOrgUnit			Alternate org unit of the new person.<br>
InternetAddress		The internet address of the new person.<br>
Password  			(Optional).  The password for the new server.<br>
PasswordQuality		Quality of password required for this server (0 - 16).<br>
INetKeyWidth		(Optional) The width of the internet key in bits (see fREGExtCreateINetKeyPair) Valid values are:<br>
					0 - default<br>
					1024<br>
AltLanguage		The alternate language of the new person.<br>
PreferredLanguage		The preferred language of the new person.<br>
ProfileName  		(Optional).  Setup profile name(s).<br>
pGroupList  			(Optional).  A pointer to a list of groups to add the new person to, constructed with ListAllocate and ListAddEntries. <br>
ExplicitPolicy		Explicit policy to assign to the new person(and/or the explicit policy to use when registering the new person (see fREGExtRegUsingPolicy).<br>
PolicyOverride		Callback function used when registering person via policy (see fREGExtRegUsingPolicy) as a hook to modify registration items after policy evaluation but before 					registration processing.<br>
	<br>
				NOTE: You should consider all memory passed back to be read only, you should change pointers <br>
					to point to your memory, you should not change callback memory:<br>
	<br>
				Example:  To change the policy derived roaming subdirectory.<br>
	<br>
				Don't do change callback memory buffer:<br>
					Cstrcpy (PersonInfo-&gt;RoamingInfo-&gt;SubDirectory, &quot;your new sub directory&quot;);<br>
<br>
				Make the callback pointer point to your buffer:<br>
					Cstrcpy (szYourBuffer, &quot;your new sub directory&quot;);<br>
					PersonInfo-&gt;RoamingInfo-&gt;SubDirectory = szYourBuffer;<br>
<br>
Flags  			Flags that are set to specify options.  See Symbolic Value, fREGxxx, in this reference.<br>
FlagsExt 	 		Flags that are set to specify options.  See Symbolic Value, fREGExtxxx, in this reference.<br>
MailInfo			(Optional) Pointer to a REG_MAIL_INFO_EXT strucutre<br>
IDInfo			(Optional) Pointer to a REG_ID_INFO structure<br>
MiscInfo			(Optional) Pointer to a REG_MISC_INFO structure<br>
RoamingInfo		(Optional) Pointer to a REG_ROAMING_INFO structure<br>
phRetPersonNote		(Optional) Pointer to receive the note handle of the new person document if the caller has specified the REGExtFlag fREGExtReturnPersonNote.  Please see fREGExtxxx.<br>
phRetPersonNoteNAB	(Optional) Pointer to receive the database handle of the database where the new person document was created.<br>
Reserved			Reserved - must be 0<br>
pReserved			Reserved - must be NULL</ul>
   ForeignDN;     		Distinguished name of the entry in a non-domino repository (i.e LDAP DN) in Notes format.<br>
   phDirEntry;   		<font size="2">/* Internal use */</font>


**See Also :**
[fREGExtxxx](/domino-c-api-docs/reference/Symb/fREGExtxxx)
[fREGxxx](/domino-c-api-docs/reference/Symb/fREGxxx)
[REGNewPerson](/domino-c-api-docs/reference/Func/REGNewPerson)
---
