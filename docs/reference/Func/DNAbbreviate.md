##### Function : Distinguished Name
##### DNAbbreviate - Abbreviates a canonical distinguished name.
---
```
#include <dname.h>
STATUS LNPUBLIC DNAbbreviate(

	DWORD  Flags,
	const char far *TemplateName,
	const char far *InName,
	char far *OutName,
	WORD  OutSize,
	WORD far *OutLength);
```
**Description :**

This function converts a distinguished name in canonical format to abbreviated 
format.  A fully distinguished name is in canonical format - it contains all 
possible naming components.  The abbreviated format of a distinguished name 
removes the labels from the naming components.

**Parameters :**
Input :
Flags  -  Abbreviation flags.  Use 0L if no flags are desired.  See Symbolic Value, DN_ABBREV.

TemplateName  -  Currently not supported.  Always pass in NULL for this argument.

InName  -  Pointer to the null terminated canonicalized distinguished name that is to be abbreviated.  If this name includes non-standard components or is a non-distinguished name with no included domain name, the returned name is a copy of the input name.

OutSize  -  Size of the OutName buffer.

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_xxx - Error returned by lower level functions.  Call OSLoadString to interpret the code.


OutName  -  Pointer to the returned abbreviated name string (null terminated).  This string must be allocated by the caller.  A buffer size of MAXUSERNAME is sufficient.

OutLength  -  Optional.  Pointer to the returned length of the returned abbreviated name string.  Use NULL if this information is not needed.


**Sample Usage :**
```
#define DNAME_JAYNE \                                 
"CN=Jayne Doe/OU=Inside Sales/OU=Sales/O=ABCorp/C=US" 


/* ..... */

char AbbrevName[MAXUSERNAME];
WORD retLen;
    

error = DNAbbreviate (0L,                                                
                      NULL,                /* user's template */      
                      DNAME_JAYNE,         /* distinguished name to   
                                              be abbreviated */       
                      AbbrevName,          /* abbreviated name */     
                      MAXUSERNAME,         /* max output length */    
                      &retLen);            /* returned output len */ 
```
**See Also :**
[DNCanonicalize](/reference/Func/DNCanonicalize)
[DNParse](/reference/Func/DNParse)
[DN_ABBREV_xxx](/reference/Symb/DN_ABBREV_xxx)
---
