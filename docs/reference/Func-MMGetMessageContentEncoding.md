##### Function : MIME
##### MMGetMessageContentEncoding - Get Conversion Controls 'message content encoding' setting.
---
##### #include <mailmisc.h>
WORD LNPUBLIC **MMGetMessageContentEncoding(**

	CCHANDLE  hCC);
**Description :**
The function  MMGetMessageContentEncoding returns the current Conversions 
Controls 'message content encoding' setting.
**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  the WORD value for the current message content encoding setting:
                  0 - text/plain (w/o images & attachments) 
                  1 - text/plain (w/images & attachments) 
                  2 - text/html (w/images & attachments)
                  3 - multipart/alternative: text/plain & text/html (w/images & attachments)


**Sample Usage :**
```
WORD wMessageContentEncoding;

wMessageContentEncoding = MMGetMessageContentEncoding(hCC);

```
**See Also :**
[CCHANDLE](D:/md_files/CCHANDLE.md)
[MMSetMessageContentEncoding](D:/md_files/MMSetMessageContentEncoding.md)
---
