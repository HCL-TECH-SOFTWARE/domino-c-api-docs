##### Function : MIME
##### MIMEStreamRewind - rewind the MIME stream to the beginning.
---
##### #include <mime.h>
int LNPUBLIC **MIMEStreamRewind(**

	MIMEHANDLE  hMIMEStream);
**Description :**
This function, MIMEStreamRewind, rewinds a MIME stream to the beginning.  You 
must specify as input the handle to the MIME stream.

MIMEStreamRewind returns MIME_STREAM_SUCCESS if the buffer is rewound with no 
errors and MIME_STREAM_IO if there are any err.

**Parameters :**
Input :
hMIMEStream  -  a MIME stream handle


Output :
(routine)  -  returns MIME_STREAM_SUCCESS or MIME_STREAM_IO


**Sample Usage :**
```
int iReturn;

if ((iReturn = MIMEStreamRewind(hMIMEStream)) == MIME_STREAM_IO) {
	goto exit;
}

```
**See Also :**
[](D:/md_files/.md)
---
