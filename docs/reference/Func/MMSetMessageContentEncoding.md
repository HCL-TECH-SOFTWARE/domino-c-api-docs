##### Function : MIME
##### MMSetMessageContentEncoding - set Conversion Controls 'message content encoding' setting
---
```
#include <mailmisc.h>
void LNPUBLIC MMSetMessageContentEncoding(

	CCHANDLE  hCC,
	WORD  wMessageContentEncoding);
```
**Description :**

The function  MMSetMessageContentEncoding sets the Conversions Controls 
'message content encoding' setting to the input value, 
wMessageContentEncoding.  No checking is done for out of bounds values.


**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

wMessageContentEncoding  -  the value to use for the Conversion Controls 'message content encoding' setting.

Output :
(routine)  -  void



**Sample Usage :**
```
MMSetMessageContentEncoding(hCC, 0); /* message content encoding */
	    /* 0 - text/plain (w/o images & attachments) */
	    /* 1 - text/plain (w/images & attachments) */
	    /* 2 - text/html (w/images & attachments) */
	    /* 3 - multipart/alternative: text/plain & text/html (w/images & 
attachments) */


```
**See Also :**
[CCHANDLE](/domino-c-api-docs/reference/Data/CCHANDLE)
[MMGetMessageContentEncoding](/domino-c-api-docs/reference/Func/MMGetMessageContentEncoding)
---
