##### Function : HTML
##### HTMLSetReferenceText - Set reference text to the HTML converter
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLSetReferenceText(

	HTMLHANDLE  hHTML,
	DWORD  Index,
	char *pRefText);
```
**Description :**

 1) A reference is a HTML reference in the notes generated HTML output. For 
example, if there exist a section in the notes document. The section is as 
below:


 section part 1
 section part 2

  The HTML output generated from this section will be like as below:

<a name="_Section1"></a><a 
href="/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&ExpandSection
=-1#_Section1" target="_self">
<img height="16" width="16" src="/icons/collapse.gif" border="0" alt="Hide 
details for Below is a section:"></a>
This is a section:
<ul>
1. section part 1<br>
2. section part2<br>
</ul>

The text in pink color is an example of HTML reference converted from a notes 
document. in this reference , it has two targets(please refer to the DATA 
structure HTMLAPIReference).One target is the name of the nsf database where 
the notes document locates in.The other target is the section's unid within the 
picture.nsf database.

2) You can use this API to change the text associated with a reference. For 
example, you can replace the reference above with null or something else, it 
depends on your business requirements.


**Parameters :**
Input :
hHTML  -  handle to the converter

Index  -  zero relative index of the reference to get the new text

pRefText  -  null terminated string -- the new reference text.

Output :
(routine)  -        NOERROR - Successful.
	ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
	  	STATUS rslt = NOERROR;
	   char* pszBinaryText = NULL;
	   FILE* PictureFile = NULL;
	   DWORD wTextLength;
	   HTMLHANDLE hHTML;
	   ......
	   rslt = HTMLGetProperty(hHTML, HTMLAPI_PROP_TEXTLENGTH, &wTextLength))
	   pszBinaryText = malloc(wTextLength);
	   if(rslt = HTMLGetText(hHTML, 0, &wTextLength, pszBinaryText))
	   {
	    PrintAPIError(rslt);
	    return rslt;
	   }
	   PictureFie = fopen(PictureName, "wb");
	   fwrite(pszBinaryText, 1, wTextLength, PictureFie);
	   fclose(PictureFie);
	   if(rslt = HTMLSetReferenceText(cvtr, refi, PictureName)) 
	   {
	    PrintAPIError(rslt);
	    return rslt;
	   }

	   free(pszBinaryText);
```
**See Also :**
[HTMLAPIReference](/reference/Data/HTMLAPIReference)
[HTMLGetReference](/reference/Func/HTMLGetReference)
[HTMLGetText](/reference/Func/HTMLGetText)
[HTMLHANDLE](/reference/Data/HTMLHANDLE)
---
