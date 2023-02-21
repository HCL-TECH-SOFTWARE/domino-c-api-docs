##### Function : HTML
##### HTMLConvertItem - Convert a specific item within a note.
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLConvertItem(

	HTMLHANDLE  hHTML,
	DBHANDLE  hDB,
	NOTEHANDLE  hNote,
	char *pszItemName);
```
**Description :**

1) This function is used to convert note item to HTML.  The results of the 
routine is retained in the converter object (until the next "convert") and are 
retrieved with GetText().
2) Only items of type RichText or MIME can be converted.  If the item is of a 
different type, ERR_HTMLAPI_NOT_SUPPORTED is returned.

**Parameters :**
Input :
hHTML  -  handle to the converter

hDB  -  handle to open database

hNote  -   handle to note containing item

pszItemName  -  refers to an item within the note indicated by hNote.  The first item found with name pszItemName is converted.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is. The return codes include:

NOERROR - action successful



**Sample Usage :**
```
	   
	rslt = NSFNoteOpen(m_DBHandle, NoteID, OPEN_EXPAND, &nt_handle);
	if(NSFItemIsPresent(nt_handle,ItemName ,strlen(ItemName)))
	{
		if(nstat = HTMLCreateConverter(&cvtr))
	 {
	  cerr << "Error in Creating HTMLConverter" << endl;
	  return FALSE;
	 }
	
	 printf("%s%s\n", "**Converting Item: ", ItemName);
	
	 nstat = HTMLConvertItem(cvtr, m_DBHandle, hNote, ItemName);
	
	 if (nstat) {
	  cprintf(%s%s\n", "E: Error converting item ",ItemName);
	  char szErrorString[BuufferSize];
	  OSLoadString(NULL, ERR(nstat), szErrorString, BuufferSize-1);
	  return FALSE;
	 }  
	}
	fprintf(flog, "\nthe Events Item does not present!\n");
	NSFNoteClose(nt_handle);
```
**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLConvertElement](/domino-c-api-docs/reference/Func/HTMLConvertElement)
[HTMLConvertImage](/domino-c-api-docs/reference/Func/HTMLConvertImage)
[HTMLConvertItem](/domino-c-api-docs/reference/Func/HTMLConvertItem)
[HTMLConvertNote](/domino-c-api-docs/reference/Func/HTMLConvertNote)
[HTMLCreateConverter](/domino-c-api-docs/reference/Func/HTMLCreateConverter)
[HTMLGetReference](/domino-c-api-docs/reference/Func/HTMLGetReference)
[HTMLGetText](/domino-c-api-docs/reference/Func/HTMLGetText)
[HTMLHANDLE](/domino-c-api-docs/reference/Data/HTMLHANDLE)
---
