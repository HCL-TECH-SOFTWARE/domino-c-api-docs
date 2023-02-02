##### Function : Compound Text
##### CompoundTextAddRenderedNote - Renders a note into Composite Data format and adds it to a CompoundText context.
---
##### #include <easycd.h>
STATUS LNPUBLIC **CompoundTextAddRenderedNote(**

	DHANDLE  hCompound,
	NOTEHANDLE  hNote,
	NOTEHANDLE  hFormNote,
	DWORD  dwFlags);
**Description :**
This function takes as input a CompoundText context handle and a note handle. 
The function will render the specified note in Composite Data format(i.e., 
richtext) and add the rendered note to the CompoundText context.  This allows 
an editable copy of an entire note to be embedded in another note.
**Parameters :**
Input :
hCompound  -  The handle of the CompoundText context that will contain the rendered note.

hNote  -  The handle of the note that is to be rendered.

hFormNote  -  The handle of the form note to use to render the note.  If NULLHANDLE is specified, and note to be rendered contains a FIELD_FORM item, the FIELD_FORM form will be used to render the note. If NULLHANDLE is specified and the note does not contain a FIELD_FORM, then the database's default form will be used.

dwFlags  -  Reserved - must be 0.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully added the rendered note to the CompoundText context.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


**See Also :**
[CompoundTextAddDocLink](D:/md_files/CompoundTextAddDocLink.md)
[CompoundTextAddParagraphExt](D:/md_files/CompoundTextAddParagraphExt.md)
[CompoundTextAddTextExt](D:/md_files/CompoundTextAddTextExt.md)
[CompoundTextCreate](D:/md_files/CompoundTextCreate.md)
[CompoundTextDefineStyle](D:/md_files/CompoundTextDefineStyle.md)
[CompoundTextInitStyle](D:/md_files/CompoundTextInitStyle.md)
---
