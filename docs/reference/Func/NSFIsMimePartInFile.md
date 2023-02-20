##### Function : MIME
##### NSFIsMimePartInFile - Checks to see if the given MIME part's content is in a file.
---
```
#include <nsfmime.h>
BOOL NSFIsMimePartInFile(

	NOTEHANDLE  hNote,
	BLOCKID  bhMIMEItem,
	WORD  wMaxFileNameLen,
	char*pszFileName);
```
**Description :**

This API check is to see if the given MIME part's content is in a file in the 
given note handle. It checks that the given MIME part is stored in the file 
content, and when it is true it returns the file name of the MIME part's 
content.

**Parameters :**
Input :
hNote  -  Handle to the containing note. 


bhMIMEItem  -  BLOCKID of the $FILE item to check.

wMaxFileNameLen  -  Maximum number of bytes to write to file name buffer.

Output :
(routine)  -  TRUE, if the MIME part's content is redirected to a file. FALSE otherwise. 


pszFileName  -  The file name which contains the MIME part's content, otherwise NULL. 


**Sample Usage :**
```
BLOCKID bhPart = { NULL }; char szFileName[MAXPATH+1] = { 0 };
STATUS error = NOERROR; 
NOTEHANDLE hMemo = NULLHANDLE; /* Open Note handle */
 /* Get BLOCKID of note item into bhPart */ 
if (NSFIsMimePartInFile(hNote, bhPart, szFileName, sizeof(szFileName)-1))
{
printf("\nMIME part content is in file.\n");
wFileLen = strlen(szFileName);
if (wFileLen)
{
printf("File Name from MIME part [%s]\n", szFileName);
} 
else
{
printf("File Name not present.\n");
} } 
```
**See Also :**
[CalCreateEntry](/reference/Func/CalCreateEntry)
[CalReadEntry](/reference/Func/CalReadEntry)
---
