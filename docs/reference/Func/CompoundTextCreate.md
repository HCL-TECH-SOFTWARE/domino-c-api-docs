##### Function : Compound Text
##### CompoundTextCreate - Creates a CompoundText context.
---
```
#include <easycd.h>
STATUS LNPUBLIC CompoundTextCreate(

	NOTEHANDLE  hNote,
	char far *pszItemName,
	DHANDLE far *phCompound);
```
**Description :**

This function creates a CompoundText context.

A CompoundText context is an abstraction in which TYPE_COMPOSITE data may be 
generated without having to manipulate CD records directly.

There are two types of Compound Text contexts:

ItemContext

An ItemContext, which is created by specifying a note handle and item name in 
the hNote and pszItemName parameters, is one that is associated with a Domino 
document.  As data is added to the context (or when the context is closed via 
the CompoundTextClose function), the resulting CD records are written to the 
associated document as one or more TYPE_COMPOSITE items of the specified name.

An ItemContext provides the most efficient means for generating TYPE_COMPOSITE 
items in a document.

StandaloneContext

A StandaloneContext, which is created when the hNote and pszItemName parameters 
are not specified (NULLHANDLE and NULL respectively), may be useful in some 
situations.  As data is added to the context, it is accumulated in an internal 
buffer and flushed to disk as necessary.  When the context is closed via the 
CompoundTextClose function, the resulting CD records are returned in a 
monolithic TYPE_COMPOSITE buffer, if possible, or temporary file.  See the 
CompoundTextClose routine description for more information on the return value 
from a StandaloneContext.

Once an ItemContext or StandaloneContext has been created, use 
CompoundTextInitStyle, CompoundTextDefineStyle, CompoundTextAddParagraphExt, 
CompoundTextAddTextExt, CompoundTextAddDocLink, CompoundTextAssimilateItem, and 
CompoundTextAssimilateFile to add data to the context.  

If an error occurs after creating the CompoundText context, use 
CompoundTextDiscard to discard the CompoundText context and free the resources 
allocated by the CompoundText context.  Otherwise, use CompoundTextClose to 
close the CompoundText context and free the resources allocated by the 
CompoundText context. 

**Parameters :**
Input :
hNote  -  Optional.  Handle of the Note to associate the context with.  Specify as NULLHANDLE for a StandaloneContext.

pszItemName  -  Optional.  Pointer to a buffer containing the null-terminated item name to generate in the associated note.  Specify as NULL for a StandaloneContext.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully created a CompoundText context.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


phCompound  -  Pointer to a HANDLE where the resulting CompoundText context handle will  be returned.


**Sample Usage :**
```

STATUS    Status;
DHANDLE    hCompound;

...

/* Create a StandaloneContext. */

Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);
if (Status != NOERROR)
 return Status;

...

/* Create an ItemContext. */

Status = CompoundTextCreate(hMailMessage, "Body", &hCompound);
if (Status != NOERROR)
 return Status;
```
**See Also :**
[CompoundTextClose](/domino-c-api-docs/reference/Func/CompoundTextClose)
---
