##### Function : MIME
##### MIMEConvertMIMEPartsCC - Converts all TYPE_MIME_PART items in an open note to TYPE_COMPOSITE items.
---
```
#include <mime.h>
STATUS LNPUBLIC MIMEConvertMIMEPartsCC(

	NOTEHANDLE  hNote,
	BOOL  bCanonical,
	CCHANDLE  hCC);
```
**Description :**

This function converts all TYPE_MIME_PART items in an open note to 
TYPE_COMPOSITE items.    It does not update the Domino database; to update the 
database, call NSFNoteUpdate.

You must specify as input the handle to the open note and a BOOLEAN value 
indicating if the note was opened in canonical format (TRUE) or host format 
(FALSE).  In addition, you may specify a handle pointer to the Conversion 
Controls settings.  The Conversion Controls settings may be changed to override 
aspects of server-side or client-side configuration; see MMSet* and MMGet* 
functions below and see also the description of the CCHANDLE data type and the 
description of the MMMConvDefaults function.  If the hCC handle is NULL, 
MIMEConvertMIMEPartsCC uses its internal default settings (same as those set by 
MMConvDefaults).

For each TYPE_MIME_PART item (which may actually be several items -- e.g., 
'Body'), MIMEConvertMIMEPartsCC performs a conversion to Composite Document 
(CD) format.

(R6.x) Note that the conversion is not performed with 100% fidelity.  
MIMEConvertMIMEPartsCC supports HTML font effects specified as separate 
elements (e.g., <b> to set bold face), but it does not support styles, whether 
specified as a CSS document, a <style> element, or as a 'style=' parameter to 
other elements (e.g., <div> or <span>).  MIMEConvertMIMEPartsCC does not fully 
support the conversion of multipart/related parts; image placement in the 
converted document will not match the original placement in the source 
document.  The rendering of tables and lists also may be somewhat different in 
the converted document.  MIMEConvertMIMEPartsCC also does not convert "active 
content"; for example, Javascript contained in an application/x-javascript 
part.  Such parts are retained as attachments in the converted document.

(R7.x/R8) Note that the conversion is not performed with 100% fidelity.  
MIMEConvertMIMEPartsCC supports HTML font effects specified as separate 
elements (e.g., <b> to set bold face), but it does not support styles, whether 
specified as a CSS document, a <style> element, or as a 'style=' parameter to 
other elements (e.g., <div> or <span>).  The rendering of tables and lists also 
may be somewhat different in the converted document.  MIMEConvertMIMEPartsCC 
also does not convert "active content"; for example, Javascript contained in an 
application/x-javascript part.  Such parts are retained as attachments in the 
converted document.

If MIMEConvertMIMEPartsCC is called on the Domino server, its actions are 
affected by its configuration as specified in the Domino Server Configuration; 
see the MIME pages of the Server Configuration for details.  If 
MIMEConvertMIMEPartsCC is called on the Notes client, its actions are affected 
by its configuration as specified in the Personal Name and Address book; see 
the International MIME Settings document for details.

**Parameters :**
Input :
hNote  -  The handle to the open note to be converted.

bCanonical  -  A boolean flag that is TRUE if the input note is in canonical format,  FALSE otherwise.

hCC  -  If non-NULL, the handle to the Conversion Controls settings.  If NULL, the default settings are used (same as those set by MMConvDefaults).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
/* get the notes flags, determine if the note was opened in canonical format, */
/*  create the default conversion control settings and then call 
MIMEConvertMIMEPartCC */

WORD wNoteFlags;
BOOL bCanonical;
CCHANDLE hCC = NULLHANDLE;
STATUS error;

NSFNoteGetInfo(hNote, _NOTE_FLAGS, &wNoteFlags);

bCanonical = (wNoteFlags & NOTE_FLAG_CANONICAL) != 0;

if (error = MMreateConvControls(&hCC)) { /* create the default conversion 
control settings */
	goto exit;
}

MMSetReadReceipt(hCC, 1);  /* 0 - Do not pass read receipt requests when 
importing or exporting (default) */
	    /* 1 - Support read receipt requests (as Return-Receipt-To when 
exporting) */
	    /* 2 - Support read receipt requests (as 
Disposition-Notification-To when exporting) */

if (error = MIMEConvertMIMEPartsCC(hNote, bCanonical, hCC)) {
	goto exit;
}

if (error = MMDestroyConvControls(hCC)) { /* destroy the default conversion 
control settings */
	goto exit;
}

```
**See Also :**
[MIMEConvertMIMEPartCC](/domino-c-api-docs/reference/Func/MIMEConvertMIMEPartCC)
[TYPE_xxx](/domino-c-api-docs/reference/Symb/TYPE_xxx)
---
