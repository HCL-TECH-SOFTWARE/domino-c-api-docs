##### Function : MIME
##### MIMEStreamRead - get a buffer from a MIME stream.
---
```
#include <mime.h>
int LNPUBLIC MIMEStreamRead(

	unsigned char *pchData,
	unsigned int *puiDataLen,
	unsigned int  uiMaxDataLen,
	MIMEHANDLE  hMIMEStream);
```
**Description :**

This function, MIMEStreamRead, returns a buffer from the input MIME stream.  
You must specify as input a pointer to an output buffer, a pointer to an 
unsigned int to received the number of bytes read, the maximum size of the 
buffer, and the handle to the MIME stream.

MIMEStreamRead returns MIME_STREAM_SUCCESS if the buffer is read and returned 
with no errors, MIME_STREAM_EOS if all data has been returned from the MIME 
stream, and MIME_STREAM_IO if there are any errors when it attempts to read the 
MIME stream.


**Parameters :**
Input :

uiMaxDataLen  -  the maximum size of the output buffer in bytes, including room for the NUL terminator.

hMIMEStream  -  a MIME stream handle

Output :
(routine)  -  returns MIME_STREAM_SUCCESS, MIME_STREAM_EOS, or MIME_STREAM_IO


pchData  -  a pointer to an output buffer.

puiDataLen  -  a pointer to an unsigned int for returning the number of bytes read.


**Sample Usage :**
```
int iReturn;
char pchBuf[MAX_BUFFER_SIZE];
unsigned int uiNumBytesRead;

if ((iReturn = MIMEStreamRead(pchBuf, &uiNumBytesRead, MAX_BUFFER_SIZE, 
hMIMEStream)) == MIME_STREAM_IO) {
	goto exit;
}

```
**See Also :**
[MIMEHANDLE](/reference/Data/MIMEHANDLE)
[MIMEStreamWrite](/reference/Func/MIMEStreamWrite)
---
