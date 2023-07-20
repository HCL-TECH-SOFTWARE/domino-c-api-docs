##### Symbolic Value : MIME
##### MIME_STREAM_xxx - flags and return values used by MIMEStreamxxx APIs.
---
```
#include <mime.h>
```

**Symbolic Values :**

	MIME_STREAM_OPEN_READ	  -  for the input note, open a MIME stream for reading.

	MIME_STREAM_OPEN_WRITE	  -  for the input note, open a MIME stream for writing.

	MIME_STREAM_MIME_INCLUDE_HEADERS	  -  Include MIME Headers.

	MIME_STREAM_RFC2822_INCLUDE_HEADERS	  -  Include RFC822 Headers

	MIME_STREAM_INCLUDE_HEADERS	  -  for the input note, include the part headers in the MIME stream.

	MIME_STREAM_SUCCESS	  -  return value: successful MIME stream I/O.

	MIME_STREAM_EOS	  -  return value: End Of Stream -- no more data in the MIME stream.

	MIME_STREAM_IO	  -  return value: I/O error; e.g.., a write to a read-only MIME stream.

	MIME_STREAM_ITEMIZE_HEADERS	  -  flag to MIMEStreamItemize: create items for part headers (only for initial RFC822 headers, not MIME part headers)

	MIME_STREAM_ITEMIZE_BODY	  -  flag to MIMEStreamItemize: create items for part bodies.

	MIME_STREAM_ITEMIZE_FULL	  -  OR'd MIME_STREAM_ITEMIZE_HEADERS and MIME_STREAM_ITEMIZE_BODY flags.

	MIME_STREAM_NO_DELETE_ATTACHMENTS	  -  flag to MIMEStreamItemize: don't delete attachment during itemization.


**Description :**

flags and return values used by MIMEStreamxxx APIs.


**See Also :**
[MIMEStreamClose](/domino-c-api-docs/reference/Func/MIMEStreamClose)
[MIMEStreamGetLine](/domino-c-api-docs/reference/Func/MIMEStreamGetLine)
[MIMEStreamItemize](/domino-c-api-docs/reference/Func/MIMEStreamItemize)
[MIMEStreamOpen](/domino-c-api-docs/reference/Func/MIMEStreamOpen)
[MIMEStreamPutLine](/domino-c-api-docs/reference/Func/MIMEStreamPutLine)
---
