##### Function : Compound Text
##### CompoundTextAddParagraphExt - Writes a paragraph of text to a CompoundText context.
---
```
#include <easycd.h>
STATUS LNPUBLIC CompoundTextAddParagraphExt(

	DHANDLE  hCompound,
	DWORD  dwStyleID,
	FONTID  FontID,
	char far *pchText,
	DWORD  dwTextLen,
	NLS_PINFO  pInfo);
```
**Description :**

NOTE: This function replaces the deprecated function CompoundTextAddParagraph.

	This routine writes a paragraph of text to a CompoundText context.  The 
text must not contain any special characters such as '\r', '\n' or '\0'.

This routine is best used when you know the exact format of the text you want 
written to the CompoundText context (for example you just created a text string 
using sprintf).  Use CompoundTextAddTextExt if you would like text parsed into 
lines and/or paragraphs before is is written into the CompoundText context.

This routine provides the most efficient means of getting text into CD format 
because, if translation is not necessary, the text is never parsed.

If the pInfo parameter is specified, the text will be translated (imported) 
into Domino format (LMBCS) using the specified character set. Specify NULL for 
pInfo if the text is LMBCS format already.

To specify a character set, call NLS_load_charset first, specifying the file 
name of the appropriate character set. NLS_load_charset returns a pointer to 
use as the pInfo parameter value.

**Parameters :**
Input :
hCompound  -  Handle of CompoundText context.

dwStyleID  -  CompoundText style ID as defined by a previous call to CompoundTextDefineStyle.

FontID  -  Specifies the FONTID.

pchText  -  Pointer to a buffer that contains the text to add.

dwTextLen  -  Length of the text to add.

pInfo  -  Pointer to an NLS_INFO structure.

Output :
(routine)  -    Return status from this call: 

NOERROR - Successfully added the paragraph to the CompoundText context.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```

COMPOUNDSTYLE  Style;
STATUS         Status;
DHANDLE         hCompound;
WORD           dwNormalStyle;
char  *pszTree = "They cannot see the forest for the trees.";
char  *pszDogs = "It was for the dogs.";


Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);
if (Status != NOERROR)
 return Status;

CompoundTextInitStyle(&Style);
Status = CompoundTextDefineStyle( hCompound
                                  "Normal",
                                  &Style,
                                  &dwNormalStyle);
                                   
Status = CompoundTextAddParagraphExt(hCompound,
                                     dwNormalStyle,
                                     DEFAULT_FONT_ID,
                                     pszTree,
                                     (DWORD)strlen(pszTree),
                                     NULL);
if (Status != NOERROR)
{
CompoundTextDiscard(hCompound);
return Status;
}

Status = CompoundTextAddParagraphExt(hCompound,
                                     dwNormalStyle,
                                     DEFAULT_FONT_ID,
                                     pszDogs,
                                     (DWORD)strlen(pszDogs),
                                     NULL);
if (Status != NOERROR)
{
CompoundTextDiscard(hCompound);
return Status;
}
...
```
**See Also :**
[NLS_load_charset](/domino-c-api-docs/reference/Func/NLS_load_charset)
[CompoundTextAddTextExt](/domino-c-api-docs/reference/Func/CompoundTextAddTextExt)
[CompoundTextDefineStyle](/domino-c-api-docs/reference/Func/CompoundTextDefineStyle)
[NLS_PINFO](/domino-c-api-docs/reference/Data/NLS_PINFO)
---
