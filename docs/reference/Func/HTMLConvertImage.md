##### Function : HTML
##### HTMLConvertImage - convert image for access
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLConvertImage(

	HTMLHANDLE  hHTML,
	char *pszImageName);
```
**Description :**


Used to access named image (.gif) from the domino web server's icons directory. 
Note that pszImageName is simple name of the image file -- no path names or 
file type suffix.

**Parameters :**
Input :
hHTML  -   handle to the converter

pszImageName  -  pointer to the image name

Output :
(routine)  -  
NOERROR - Successful.
 ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



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
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLConvertElement](/domino-c-api-docs/reference/Func/HTMLConvertElement)
[HTMLConvertItem](/domino-c-api-docs/reference/Func/HTMLConvertItem)
[HTMLConvertNote](/domino-c-api-docs/reference/Func/HTMLConvertNote)
[HTMLCreateConverter](/domino-c-api-docs/reference/Func/HTMLCreateConverter)
[HTMLGetProperty](/domino-c-api-docs/reference/Func/HTMLGetProperty)
[HTMLGetReference](/domino-c-api-docs/reference/Func/HTMLGetReference)
[HTMLGetText](/domino-c-api-docs/reference/Func/HTMLGetText)
---
