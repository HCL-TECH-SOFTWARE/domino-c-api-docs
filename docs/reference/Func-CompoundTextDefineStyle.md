##### Function : Compound Text
##### CompoundTextDefineStyle - Defines a CompoundText style.
---
##### #include <easycd.h>
STATUS LNPUBLIC **CompoundTextDefineStyle(**

	DHANDLE  hCompound,
	char far *pszStyleName,
	COMPOUNDSTYLE far *pDefinition,
	DWORD far *pdwStyleID);
**Description :**
This routine defines a CompoundText style for use in calls to 
CompoundTextAddParagraphExt and CompoundTextAddTextExt..
**Parameters :**
Input :
hCompound  -  Handle of CompoundText context.

pszStyleName  -  Pointer to the null-terminated style name.

pDefinition  -  Pointer to COMPOUNDSTYLE structure which defines paragraph attributes for the style.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully defined a style.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


pdwStyleID  -  Pointer to a DWORD where the Style ID will be returned.  The Style ID is used in subsequent calls to CompoundTextAddParagraphExt and CompoundTextAddTextExt to reference the style definition.

**Sample Usage :**
```

COMPOUNDSTYLE  Style;
DWORD          dwNormalStyle;

CompoundTextInitStyle(&Style);
Status = CompoundTextDefineStyle( hCompound
                                  "Normal",
                                  &Style,
                                  &dwNormalStyle);
```
**See Also :**
[CompoundTextInitStyle](D:/md_files/CompoundTextInitStyle.md)
[CompoundTextAddParagraphExt](D:/md_files/CompoundTextAddParagraphExt.md)
[CompoundTextAddTextExt](D:/md_files/CompoundTextAddTextExt.md)
---
