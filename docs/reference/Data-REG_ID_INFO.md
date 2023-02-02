##### Data Type : User Registration
##### REG_ID_INFO - Structure that defines ID registration information.
---
##### #include <reg.h>
**Description :**
This structure defines ID registration information for the REGNewPerson, 
REGNewCertifierExtended, and REGNewServerExtended2 functions.  The entire 
structure must
be initialized to zero.

The fields in the structure are (all fields that are not used must be NULL/O):

Size   Size of this structure - must be initialized with sizeof (REG_ID_INFO)
Type   See Symbolic Value KFM_IDFILE_TYPE_XXX, in this reference and base on 
the entity being registered 
KeyWidth   Key width in bits - valid values: 
	    0 - default
	    630 - Compatible with all releases
	    1024 - Compatible with R6 and later
PasswordKeyWidth  Encryption strength in bits:
	    0 - default
	    64
	    128
FileName   The pathname of the new ID file. If the fREGCreateIDFileNow flag is 
not specified, then this file must exist. 
Reserved   Reserved - must be 0
pReserved   Reserved - must be NULL

**See Also :**
[REGNewCertifierExtended](D:/md_files/REGNewCertifierExtended.md)
[REGNewPerson](D:/md_files/REGNewPerson.md)
[REGNewServerExtended2](D:/md_files/REGNewServerExtended2.md)
---
