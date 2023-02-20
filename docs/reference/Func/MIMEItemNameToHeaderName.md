##### Function : MIME
##### MIMEItemNameToHeaderName - Map a Notes item name name to an Internet header, optionally providing additional information about the item.  
---
```
#include <mime.h>
STATUS LNPUBLIC MIMEItemNameToHeaderName(

	WORD  wMessageType,
	char *pszItemName,
	char *retszHeaderName,
	WORD  wHeaderNameSize,
	WORD *retwHeaderType);
```
**Description :**

This function accepts a Notes item name input and returns the corresponding 
header name, along with optional additional information.

You must specify as input the message type (default: MIME_HEADER_MAP_EMAIL), a 
pointer to the ASCIIZ item name (e.g., "SendTo"), a pointer to an output buffer 
for the ASCIIZ header name, the size of the output header name buffer 
(including the terminating '\0' character), and an optional pointer to the 
output header type.

Upon entry MIMEItemNameToHeaderName sets the return header type to 
MIME_HEADER_FORMAT_TEXT.

If MIMEItemNameToHeaderName finds an header name for the input item name, it 
returns the header name in the output item name buffer and the header type the 
output header type.

If MIMEItemNameToHeaderName cannot find a header name for the input item name, 
it sets the output header name to "X-Notes-Item".


**Parameters :**
Input :
wMessageType  -  Type of RFC822 Message

pszItemName  -  Notes Item Name to Convert

wHeaderNameSize  -  Size of RFC822 Header Name Buffer

Output :
(routine)  -  Return status from this call.
	NOERROR - Successfully converted the note.
	ERR_MISC_RETURN_TRUNC - Error returned if the output header name was truncated.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


retszHeaderName  -  Return RFC822 Header Name Buffer.

retwHeaderType  -  Optional Return the Type of Header.


**Sample Usage :**
```
#define MAX_HEADER_NAME_LEN 32

char aszHeaderName[MAX_HEADER_NAME_LEN];
WORD wHeaderType;
STATUS error;

if (error = MIMEItemNameToHeaderName(
	  MIME_HEADER_MAP_EMAIL,     // Type of Message
	  "SendTo",                   // Item Name
	  aszHeaderName,              // Return Header Name Buffer
	  MAX_HEADER_NAME_LEN,        // Size of Header Name Buffer (including 
'\0' terminator)
	  &wHeaderType )) {           // Optional Return the Type of Header: 
MIME_HEADER_FORMAT_XXXX
	goto exit;
}

```
**See Also :**
[MIMEHeaderNameToItemName](/reference/Func/MIMEHeaderNameToItemName)
[MIME_HEADER_FORMAT_xxx](/reference/Symb/MIME_HEADER_FORMAT_xxx)
[MIME_HEADER_MAP_xxx](/reference/Symb/MIME_HEADER_MAP_xxx)
---
