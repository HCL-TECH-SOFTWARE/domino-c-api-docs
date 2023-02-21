##### Function : MIME
##### NSFMimePartAppend - Adds a TYPE_MIME_PART item to a note

---
```
#include <nsfmime.h>
STATUS LNPUBLIC NSFMimePartAppend(

	NOTEHANDLE  hNote,
	char *pchItemName,
	WORD  wItemNameLen,
	WORD  wPartType,
	DWORD  dwFlags,
	char *pchPart,
	WORD  wPartLen);
```
**Description :**

The function NSFMimePartAppend adds a TYPE_MIME_PART item to an open note.  The 
TYPE_MIME_PART item begins with a MIME_PART ODS structure (see MIME_PART in 
mimeods.h) and is followed by the part data.  The part data may consist of a 
boundary, headers, and the part 'body'.  If the caller is adding a part with a 
boundary or headers, the bit flags MIME_PART_HAS_BOUNDARY and 
MIME_PART_HAS_HEADERS, respectively, should be set in the dwFlags argument.

If the part is a multipart type --e.g., 'Content-type: multipart/mixed; 
boundary="__BoundaryString__"'-- wPartType should be set to MIME_PART_PROLOG.

If the part is a message type --e.g., 'Content-type: message/rfc822'-- 
wPartType should be set to MIME_PART_MESSAGE.

If the part is only a terminating boundary (e.g. '--__BoundaryString__--'), 
wPartType should be set to MIME_PART_EPILOG.

If the part is a typical MIME part (e.g., 'Content-type: text/plain'), 
wPartType should be set to MIME_PART_BODY.


**Parameters :**
Input :
hNote  -  a handle to an open note.

pchItemName  -  Pointer to buffer containing item name to use; typically should be MAIL_BODY_ITEM.

wItemNameLen  -  item name length.

wPartType  -  the type of MIME part to add.

dwFlags  -  flags that describe the MIME part -- has headers, has  boundary, etc.

pchPart  -  pointer to the part data to add.

wPartLen  -   the part data length in bytes.

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully added the MIME part.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




**Sample Usage :**
```
#define HEADERS "Content-type: text/plain; charset=\"us-ascii\"\015\012\015\012"
#define BODY "This is a text plain part.\015\012"
#define PARTLEN ((sizeof(HEADERS)-1)+(sizeof(BODY)-1))

STATUS error;
char achPart[PARTLEN+1];

strcpy(achPart, HEADERS);
strcat(achPart, BODY);

error = NSFMimePartAppend(hNote,
	     MAIL_BODY_ITEM,
	     sizeof(MAIL_BODY_ITEM)-1,
	     MIME_PART_BODY,
	     MIME_PART_HAS_HEADERS,
	     achPart,
	     PARTLEN);
if (error) {
	goto exit;
}

```
**See Also :**
[MIMEPARTTYPE](/domino-c-api-docs/reference/Data/MIMEPARTTYPE)
[MIME_PART_xxx](/domino-c-api-docs/reference/Symb/MIME_PART_xxx)
[NOTEHANDLE](/domino-c-api-docs/reference/Data/NOTEHANDLE)
[NSFMimePartDelete](/domino-c-api-docs/reference/Func/NSFMimePartDelete)
---
