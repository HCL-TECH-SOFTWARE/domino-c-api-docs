##### Function : HTML
##### HTMLGetText - Retrieves the generated HTML or binary data, copying it into user supplied buffer.
---
##### #include <htmlapi.h>
STATUS LNPUBLIC  **HTMLGetText(**

	HTMLHANDLE  hHTML,
	DWORD  StartingOffset,
	DWORD*pTextLength,
	char *pText);
**Description :**
          
1) Retrieves the generated HTML or binary data, copying it into user supplied 
buffer.
 
2) Note that if this function is called multiple times with different starting 
offsets and with a return buffer smaller than the total text length, the line 
length calculations                   may not be accurate.
            
                Example:  assume return buffer contains:
                    1 2 3 4 5 6 CR LF 7 8 9

                    The text length == 11

                    Call GetText with StartingOffset == 0 and *pTextLength == 
11, then this property
                    will have value of 6

                    Call GetText with StartingOffset == 0 and *pTextLength == 
4, then this property
                    will have value of 4

                    Next call GetText with StartingOffset == 4 and *pTextLength 
== 7, then this
                    property will have value of 4.

**Parameters :**
Input :
hHTML  -  handle to the converter

StartingOffset  -  offset into generated html indicating starting point of the copy.

pTextLength  -   pointer to value containing the maximum number of characters to be copied. The value must be <= to the size of the buffer.

pText  -  modified to contain the HTML.

Output :
(routine)  -  
 NOERROR - Successful.
 ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.




pTextLength  -   modified to contain the actual number of bytes copied

**Sample Usage :**
```
#include <string.h>
#include <stdio.h>
#include <malloc.h>

#include "global.h"
#include "addin.h"
#include "htmlapi.h"
#include "osmisc.h"



STATUS rslt = NOERROR;
DWORD wTextLength = 0;
HTMLHANDLE cvtr = NULL;
char *ImageName = "abook";

BOOL bBinary = FALSE;

void PrintAPIError(STATUS err);

STATUS LNPUBLIC AddInMain(HMODULE hModule, int argc, char* argv[])
{
	
	char **argp = argv;
	char *pszBinaryText = malloc(wTextLength);
	rslt = HTMLProcessInitialize();
	FILE *PictureFie = 0;
	printf("%s\n", "Hi from HAPI");
	if ( NOERROR != rslt ) 
	{
	 printf("%s\n", "** Error on per-process init: ");
	 PrintAPIError(rslt);
	 return rslt;
	}
	
	if(rslt = HTMLCreateConverter(&cvtr))
	{
	 printf("%s\n", "Error in Creating HTMLConverter");
	 PrintAPIError(rslt);
	 return rslt;
	}
	
	printf("%s\n", "converting pitcure");

	if (rslt = HTMLConvertImage(cvtr, ImageName)) 
	{
	 printf("%s%s\n", "E: Error converting Image: ", ImageName);
	 PrintAPIError(rslt);
	 return FALSE;
	}
	
	if(rslt = HTMLGetProperty(cvtr, HTMLAPI_PROP_BINARYDATA, &bBinary))
	{
	 printf("%s%s\n", "E: Error getting Property: 
","HTMLAPI_PROP_BINARYDATA" );
	 PrintAPIError(rslt);
	 return rslt;
	}

	if(rslt = HTMLGetProperty(cvtr, HTMLAPI_PROP_TEXTLENGTH, &wTextLength))
	{
	 printf("%s%s\n", "E: Error getting Property: 
","HTMLAPI_PROP_TEXTLENGTH" );
	 PrintAPIError(rslt);
	}

	
	if(rslt = HTMLGetText(cvtr, 0, &wTextLength, pszBinaryText))
	{
	 printf("%s\n", "E: Error getting BinaryText: ");
	 PrintAPIError(rslt);
	}
	
	if(rslt = HTMLDestroyConverter(cvtr))
	{
	 printf("%s\n","E: Error in destroying HTML Converter: ");  
	 PrintAPIError(rslt);
	}
	
	PictureFie = fopen("Trans.gif", "wb");
	fwrite(pszBinaryText, 1, wTextLength, PictureFie);
	HTMLSetReferenceText(cvtr, refi, "C:\\yuenan.jpg");
	fclose(PictureFie);
	free(pszBinaryText);
	return 0;
}

void PrintAPIError(STATUS err)
{
	char szErrorString[100] = "\0";
	OSLoadString(NULL, ERR(err), szErrorString, 100-1);
	printf("%s\n" ,szErrorString);
}
```
**See Also :**
[HTMLConvertElement](D:/md_files/HTMLConvertElement.md)
[HTMLConvertImage](D:/md_files/HTMLConvertImage.md)
[HTMLConvertItem](D:/md_files/HTMLConvertItem.md)
[HTMLConvertNote](D:/md_files/HTMLConvertNote.md)
[HTMLCreateConverter](D:/md_files/HTMLCreateConverter.md)
[HTMLGetReference](D:/md_files/HTMLGetReference.md)
[HTMLGetText](D:/md_files/HTMLGetText.md)
[HTMLHANDLE](D:/md_files/HTMLHANDLE.md)
---
