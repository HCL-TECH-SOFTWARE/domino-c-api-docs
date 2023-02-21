##### Function : MIME
##### MIMEConvertCDParts - Convert all of the TYPE_COMPOSITE items to TYPE_MIME_PART.
---
```
#include <mime.h>
STATUS LNPUBLIC MIMEConvertCDParts(

	NOTEHANDLE  hNote,
	BOOL  bCanonical,
	BOOL  bIsMIME,
	CCHANDLE  hCC);
```
**Description :**

This function converts the all TYPE_COMPOSITE items in an open note to 
TYPE_MIME_PART items.    It does not update the Domino database; to update the 
database, call NSFNoteUpdate.

You must specify as input the handle to the open note, a BOOLEAN value 
indicating if the note was opened in canonical format (TRUE) or host format 
(FALSE), a BOOLEAN value indicating if the note has MIME information, and 
(optionally) a handle to the Conversion Controls settings.  The Conversion 
Controls settings may be changed to override aspects of server-side or 
client-side configuration; see MMSet* and MMGet* functions below and see also 
the description of the CCHANDLE data type and the description of the 
MMConvDefaults function.  If the hCC handle is NULL, MIMEConvertCDParts uses 
its internal default settings (same as those set by MMConvDefaults).

(R6.x) Note that the conversion is not performed with 100% fidelity.  
MIMEConvertCDParts can create reasonable HTML documents from a given Notes Rich 
Text document, but not all CD features can be represented as HTML;  e.g., 
sections.  In addition. MIMEConvertCDParts will not render inline images in 
their original position in the converted document, instead rendering them at 
the end of the converted document.

(R7.x/R8) Note that the conversion is not performed with 100% fidelity.  
MIMEConvertCDParts can create reasonable HTML documents from a given Notes Rich 
Text document, but not all CD records can be represented as HTML; e.g., 
sections.  In R7 and subsequent releases, MIMEConvertCDParts can more 
faithfully render inline images in the converted document by creating a 
multipart/related document.

If MIMEConvertCDParts is called on the Domino server, its actions are affected 
by its configuration as specified in the Domino Server Configuration; see the 
MIME pages of the Server Configuration for details.  If MIMEConvertCDParts is 
called on the Notes client, its actions are affected by its configuration as 
specified in the Personal Name and Address book; see the International MIME 
Settings document for details.


**Parameters :**
Input :
hNote  -  The handle to the open note to be converted.

bCanonical  -  A boolean flag that is TRUE if the input note is in canonical format,  FALSE otherwise.

bIsMIME  -  A boolean flag that is TRUE if the input note contains any TYPE_RFC822_TEXT or TYPE_MIME_PART items.

hCC  -  If non-NULL, the handle to the Conversion Controls settings.  If NULL, the default settings are used (same as those set by MMConvDefaults).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
/* get the notes flags, determine if the note was opened in canonical format, */
/*  create the default conversion control settings and then call 
MIMEConvertCDParts */

WORD wNoteFlags;
BOOL bCanonical;
CCHANDLE hCC = NULLHANDLE;
STATUS error;
BOOL bIsMIME;

NSFNoteGetInfo(hNote, _NOTE_FLAGS, &wNoteFlags);

bCanonical = (wNoteFlags & NOTE_FLAG_CANONICAL) != 0;

bIsMIME = NSFNoteHasMIMEPart(hNote);

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

if (error = MIMEConvertCDParts(hNote, bCanonical, bIsMIME, hCC)) {
	goto exit;
}

if (error = MMDestroyConvControls(hCC)) { /* destroy the default conversion 
control settings */
	goto exit;
}


```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[NOTEHANDLE](/domino-c-api-docs/reference/Data/NOTEHANDLE)
---
