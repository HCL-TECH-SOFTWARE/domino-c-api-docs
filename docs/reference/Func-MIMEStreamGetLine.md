##### Function : MIME
##### MIMEStreamGetLine - Get a line from a MIME stream.
---
##### #include <mime.h>
int LNPUBLIC **MIMEStreamGetLine(**

	char *pszLine,
	unsigned int  uiMaxLineSize,
	MIMEHANDLE  hMIMEStream);
**Description :**
This function, MIMEStreamGetLine, returns an ASCIIZ line from the input MIME 
stream.  You must specify as input a pointer to an output line buffer, the 
maximum size of the buffer (including space for the terminating NULL 
character), and the handle to the MIME stream.

On entry MIMEStreamGetLine writes a NUL byte to the first byte pointed to by 
'pszLine'.  It returns MIME_STREAM_SUCCESS if the line is read and returned 
with no errors, MIME_STREAM_EOS if all data has been returned from the MIME 
stream, and MIME_STREAM_IO if there are any errors when it attempts to read the 
MIME stream.

**Parameters :**
Input :

uiMaxLineSize  -  The maximum size of the output buffer in bytes, including room for the NULL terminator

hMIMEStream  -  A MIME stream handle

Output :
(routine)  -  Returns MIME_STREAM_SUCCESS, MIME_STREAM_EOS, or MIME_STREAM_IO



pszLine  -  A pointer to an output line buffer.

**Sample Usage :**
```
#define MAX_LINE_SIZE 80

int iReturn;
char aszLine[MAX_LINE_SIZE];

if ((iReturn = MIMEStreamGetLine(aszLine, MAX_LINE_SIZE, hMIMEStream)) == 
MIME_STREAM_IO) {
	goto exit;
}

```
**See Also :**
[MIMEHANDLE](D:/md_files/MIMEHANDLE.md)
[MIMEStreamPutLine](D:/md_files/MIMEStreamPutLine.md)
---
