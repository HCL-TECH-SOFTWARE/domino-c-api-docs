##### Function : HTML
##### HTMLGetReference - Get reference from the HTML converter
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLGetReference(

	HTMLHANDLE  hHTML,
	DWORD  Index,
	MEMHANDLE  phRef);
```
**Description :**

 1) A reference is a HTML reference in the notes generated HTML output. For 
example, if there exist a section in the notes document. The section is as 
below:


 section part 1
 section part 2

  The HTML output generated from this section will be like as below:

<a name="_Section1"></a><a 
href="/picture.nsf/0/64a510cea327672d48257146001bfdac?OpenDocument&Ex
pandSection=-1#_Section1" target="_self">
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

 2) This API will get all the references from the HTML converter. From the 
reference, you can get the other informations which are releated with the 
reference(please refer to the     data structure HTMLAPIReference) and then 
parse them and deal with them.

 3) Call HTMLLockAndFixupReference on 'phRef' in order to access the reference 
data.

**Parameters :**
Input :
hHTML  -  handle to the converter

Index  -  zero relative index of the reference in the list of references

Output :
(routine)  -  NOERROR - Successful.
 ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


phRef  -  memory handle of reference.  The handle is to a COPY of the reference information.Caller is responsible for freeing the memory. 


**Sample Usage :**
```
	DWORD retval = 0;
        MEMHANDLE hRef = 0;
        HTMLAPIReference *pRef = 0;
	const char* newRefText = getenv("HAPI_NewRefText"); 
	char *temp = NULL;
        STATUS rslt;
	rslt = HTMLGetProperty(cvtr, HTMLAPI_PROP_NUMREFS, &retval);
	cerr << "<HAPI:RefList count=" << retval << endl;
	for ( int refi = 0 ; refi < retval; refi++ )
	{
        rslt = HTMLGetReference(cvtr, refi, &hRef);
	 
	 if(rslt)
	 {
	  PrintAPIError(rslt);
	  return rslt;
	 }
	 rslt = HTMLLockAndFixupReference(hRef, &pRef);
	 if(rslt)
	 {
	  PrintAPIError(rslt);
	  return rslt;
	 }
        }
```
**See Also :**
[HTMLAPIReference](/reference/Data/HTMLAPIReference)
[HTMLAPI_REF_TYPE](/reference/Data/HTMLAPI_REF_TYPE)
[HTMLHANDLE](/reference/Data/HTMLHANDLE)
[HTMLLockAndFixupReference](/reference/Func/HTMLLockAndFixupReference)
[HTMLSetReferenceText](/reference/Func/HTMLSetReferenceText)
---
