##### Function : MIME
##### MIMEHeaderNameToItemName - Map an Internet header name to a Notes item name, optionally providing additional information about the item.
---
##### #include <mime.h>
STATUS LNPUBLIC **MIMEHeaderNameToItemName(**

	WORD  wMessageType,
	char *pszHeaderName,
	char *pszHeaderBody,
	char *retszItemName,
	WORD  wItemNameSize,
	WORD *retwHeaderType,
	WORD *retwItemFlags,
	WORD *retwDataType);
**Description :**
This function accepts an input header name and returns the corresponding Notes 
item name, along with optional additional information such as the item flags 
and data type.

You must specify as input the message type (default: MIME_HEADER_MAP_EMAIL), a 
pointer to the ASCIIZ header name (e.g., "To"), an optional pointer to the 
header "body" (i.e., everything after the header name, ':', space), a pointer 
to an output buffer for the ASCIIZ item name, the size of the output item name 
buffer (including the terminating '\0' character), an optional pointer to the 
output header type, an optional pointer to the output item flags, and an 
optional pointer to the output item data type.

Upon entry MIMEHeaderNameToItemName writes a null byte, '\0', to the output 
item name buffer, sets the output header type to MIME_HEADER_FORMAT_TEXT, sets 
the output item flags to 0, and sets the output data type to TYPE_TEXT.

If the input header name is a Content header --e.g., 
Content-Transfer-Encoding-- MIMEHeaderNameToItemName returns the Content header 
name with a '$' prefix --e.g., $Content-Transfer-Encoding-- in the output item 
name buffer.  The output header type and output item flags are returned with 
their initial values as described above.

If MIMEHeaderNameToItemName finds an item name for the input header name, it 
returns the item name in the output item name buffer.  It also returns the 
output header type, output item flags, and output data type that were found 
with the output item name.

If MIMEHeaderNameToItemName cannot find an item name for the input header name 
and the input header name is 'X-Notes-Item', MIMEHeaderNameToItemName checks 
the input header body pointer.  If the pointer is NULL, 
MIMEHeaderNameToItemName returns the ERR_MISC_INVALID_ARGS error; otherwise, it 
parses the header body for the item name, returning it in the output item 
buffer.  In addition, it parses the header body for the the output header type, 
output item flags, and output data type, returning the parsed values.

**Parameters :**
Input :
wMessageType  -  Type of message: MIME_HEADER_MAP_XXXX

pszHeaderName  -  Pointer to input ASCIIZ RFC822 header name

pszHeaderBody  -  Optional pointer to ASCIIZ RFC822 header body (for processing X-Notes-Item headers)

wItemNameSize  -  Size of item name buffer (including '\0' terminator).

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_MISC_INVALID_ARGS - If input header name is X-Notes-Item and 'pszHeaderBody' is NULL.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



retszItemName  -  Pointer to output ASCIIZ item name buffer.

retwHeaderType  -  Optional pointer to output header type: MIME_HEADER_FORMAT_XXXX

retwItemFlags  -  Optional pointer to output item flags: ITEM_XXXX

retwDataType  -  Optional pointer to output data type: TYPE_XXXX

**Sample Usage :**
```
#define MAX_ITEM_NAME_LEN 32

char aszItemName[MAX_ITEM_NAME_LEN];
WORD wHeaderType;
WORD wItemFlags;
WORD wDataType;
STATUS error;

if (error = MIMEHeaderNameToItemName(
	  MIME_HEADER_MAP_EMAIL,     // Type of Message
	  "To",                       // RFC822 Header Name
	  NULL,                       // Optional RFC822 Header Body (for 
processing X-Notes-Item headers)
	  aszItemName,                // Return Item Name Buffer
	  MAX_ITEM_NAME_LEN,          // Size of Item Name Buffer (including 
'\0' terminator)
	  &wHeaderType,               // Optional Return the Type of Header: 
MIME_HEADER_FORMAT_XXXX
	  &wItemFlags,                // Optional Return Item Flags: ITEM_XXXX
	  &wDataType )) {             // Optional Return Data Type: TYPE_XXXX
	goto exit;
}

```
**See Also :**
[ITEM_xxx](D:/md_files/ITEM_xxx.md)
[MIMEItemNameToHeaderName](D:/md_files/MIMEItemNameToHeaderName.md)
[MIME_HEADER_FORMAT_xxx](D:/md_files/MIME_HEADER_FORMAT_xxx.md)
[MIME_HEADER_MAP_xxx](D:/md_files/MIME_HEADER_MAP_xxx.md)
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
