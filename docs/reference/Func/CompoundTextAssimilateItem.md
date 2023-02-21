##### Function : Compound Text
##### CompoundTextAssimilateItem - Assimilates one or more TYPE_COMPOSITE items into a CompoundText context.
---
```
#include <easycd.h>
STATUS LNPUBLIC CompoundTextAssimilateItem(

	DHANDLE  hCompound,
	NOTEHANDLE  hNote,
	char far *pszItemName,
	DWORD  dwFlags);
```
**Description :**

This routine assimilates the contents of one or more named TYPE_COMPOSITE items 
from a document into a CompoundText context.  The contents are assimilated in 
that PABIDs and styles are fixed up (renumbered/renamed as needed) before they 
are appended to the CompoundText context.

Note: This function does not handle features of rich text that depend on 
special items that reside outside the rich text field specified by the 
"pszItemName" parameter.

Two such features of rich text include doc links that depend on the special 
$Links item, and font faces that depend on the special $Fonts item. These 
special items in the note reside outside the specified rich text field.  
Therefore, when CompoundTextAssimilateItem merges a rich text field containing 
doc links consisting of CDLINK2 records into a Compound Text context, the doc 
link in the resulting compound text does not function. A work-around to this 
problem is demonstrated by sample program HISTORY in the RICHTEXT directory. 

Also, when CompoundTextAssimilateItem merges a rich text field containing font 
faces that require a font table (a $Fonts item in the note)  the resulting 
compound text does not reflect the font face used in the original field.

**Parameters :**
Input :
hCompound  -  Handle of the CompoundText context.

hNote  -  Handle of the note that contains the TYPE_COMPOSITE item(s) to assimilate.

pszItemName  -  Pointer to null-terminated item name to assimilate.

dwFlags  -   Assimilation flags reserved for future use.  Set this parameter to 0L.

Output :
(routine)  -   Return status from this call: 

NOERROR - Successfully assimilated the specified item.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.



**Sample Usage :**
```
COMPOUNDSTYLE  Style;
STATUS         Status;
DHANDLE         hCompound;
DWORD          dwNormalStyle;
char  *pszTree = "They cannot see the forest\nfor the trees.";
char  *pszDogs = "It was for\nthe dogs.";

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

Status = CompoundTextAddTextExt(hCompound,
                             dwNormalStyle,
                             DEFAULT_FONT_ID,
                             pszDogs,
                             (DWORD)strlen(pszDogs),
                             "\r\n",
                             COMP_PRESERVE_LINES,
                             NULL);
if (Status != NOERROR)
{
CompoundTextDiscard(hCompound);
return Status;
}

Status = CompoundTextAssimilateItem( hCompound,
       hOriginalNote,
       "Body",
       0L);

...

```
**See Also :**
[CompoundTextAssimilateFile](/domino-c-api-docs/reference/Func/CompoundTextAssimilateFile)
---
