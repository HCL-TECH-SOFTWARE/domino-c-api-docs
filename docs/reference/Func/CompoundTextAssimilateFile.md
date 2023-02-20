##### Function : Compound Text
##### CompoundTextAssimilateFile - Assimilates contents of a CD file into a CompoundText context.
---
```
#include <easycd.h>
STATUS LNPUBLIC CompoundTextAssimilateFile(

	DHANDLE  hCompound,
	char far *pszFileName,
	DWORD  dwFlags);
```
**Description :**

This routine assimilates the contents of a CD file (a file containing rich 
text) into a CompoundText context.  The contents are assimilated in that PABIDs 
and styles are fixed up (renumbered/renamed as needed) before they are appended 
to the CompoundText context.

A CD file is a file containing data in Domino rich text format. 
CompoundTextClose() creates a CD file when closing a stand alone context 
containing more than 64K bytes of rich text.  A CD file consists of a datatype 
word (usually TYPE_COMPOSITE) followed by any number of CD records. The data 
type word is always in Host (machine-specific) format.  The remainder of the 
data in a CD file is in Domino Canonical format.

**Parameters :**
Input :
hCompound  -  Handle of the CompoundText context.

pszFileName  -  Pointer to null-terminated file specification of the file to assimilate. The file must contain the data for a Domino rich text field in Domino canonical format, beginning with the data type word.

dwFlags  -  Assimilation flags reserved for future use.  Set this parameter to 0L.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully assimilated the contents of the CD file.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```
COMPOUNDSTYLE  Style;
STATUS         Status;
DHANDLE         hCompound;
DWORD          dwNormalStyle;
char  *pszTree = "They cannot see the forest\nfor the trees.";

Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);
if (Status != NOERROR)
 return Status;

CompoundTextInitStyle(&Style);
Status = CompoundTextDefineStyle( hCompound
                                  "Normal",
                                  &Style,
                                  &dwNormalStyle);
                                   
Status = CompoundTextAddTextExt(hCompound,
                             dwNormalStyle,
                             DEFAULT_FONT_ID,
                             pszTree,
                             (DWORD)strlen(pszTree),
                             "\r\n",
                             COMP_PRESERVE_LINES,
                             NULL);
if (Status != NOERROR)
{
CompoundTextDiscard(hCompound);
return Status;
}

Status = CompoundTextAssimilateFile( hCompound,
       "c:\\rich.txt",
       0L);
if (Status != NOERROR)
{
CompoundTextDiscard(hCompound);
return Status;
}
...
```
**See Also :**
[CompoundTextAssimilateItem](/reference/Func/CompoundTextAssimilateItem)
[CompoundTextClose](/reference/Func/CompoundTextClose)
---
