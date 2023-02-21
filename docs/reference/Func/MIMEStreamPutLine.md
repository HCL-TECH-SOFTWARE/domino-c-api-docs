##### Function : MIME
##### MIMEStreamPutLine - Write a line to a MIME stream.
---
```
#include <mime.h>
int LNPUBLIC MIMEStreamPutLine(

	char *pszLine,
	MIMEHANDLE  hMIMEStream);
```
**Description :**

This function MIMEStreamPutLine writes a line of data to a MIME stream.  You 
must specify as input a pointer to a line of NUL terminated text and the handle 
to the MIME stream.

MIMEStreamPutLine appends the input line to the MIME stream and then appends 
carriage return, line feed (CRLF) to the MIME stream.  If the data is written 
sucessfully to the MIME stream, MIMEStreamPutLine returns MIME_STREAM_SUCCESS.  
If it detects any errors while writing to the MIME stream, it returns 
MIME_STREAM_IO.  Note that the MIME stream must be opened for write by 
specifying the MIME_STREAM_OPEN_WRITE flag on the MIMEStreamOpen call.


**Parameters :**
Input :
pszLine  -  A pointer to a line of NULL terminated text.

hMIMEStream  -  A handle to the MIME stream.

Output :
(routine)  -  Return status from this call.
	MIME_STREAM_IO - returned if there are errors writing to the stream or if the stream was not opened for writing.




**Sample Usage :**
```
int iReturn;

if ((iReturn = MIMEStreamPutLine(pszLine, hMIMEStream)) == MIME_STREAM_IO) {
	goto exit;
}

```
**See Also :**
[MIMEStreamGetLine](/domino-c-api-docs/reference/Func/MIMEStreamGetLine)
[MIMEStreamItemize](/domino-c-api-docs/reference/Func/MIMEStreamItemize)
[MIME_STREAM_xxx](/domino-c-api-docs/reference/Symb/MIME_STREAM_xxx)
---
