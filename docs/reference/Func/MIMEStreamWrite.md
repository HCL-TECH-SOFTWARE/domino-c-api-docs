##### Function : MIME
##### MIMEStreamWrite - put a buffer to a MIME stream.
---
```
#include <mime.h>
int LNPUBLIC MIMEStreamWrite(

	unsigned char *pchData,
	unsigned int  uiDataLen,
	MIMEHANDLE  hMIMEStream);
```
**Description :**

This function, MIMEStreamWrite, writes a buffer to the input MIME stream.  You 
must specify as input a pointer to a buffer, an unsigned int with the number of 
bytes to write, and the handle to the MIME stream.

MIMEStreamWrite returns MIME_STREAM_SUCCESS if the buffer is written with no 
errors and MIME_STREAM_IO if there are any errors when it attempts to write to 
the MIME stream.


**Parameters :**
Input :
pchData  -  a pointer to a write buffer.

uiDataLen  -  the number of bytes to write from the write buffer.

hMIMEStream  -  a MIME stream handle

Output :
(routine)  -  returns MIME_STREAM_SUCCESS or MIME_STREAM_IO



**Sample Usage :**
```
int iReturn;
char pchBuf[MAX_BUFFER_SIZE];

if ((iReturn = MIMEStreamWrite(pchBuf, MAX_BUFFER_SIZE, hMIMEStream)) == 
MIME_STREAM_IO) {
	goto exit;
}

```
**See Also :**
[MIMEHANDLE](/reference/Data/MIMEHANDLE)
[MIMEStreamRead](/reference/Func/MIMEStreamRead)
---
