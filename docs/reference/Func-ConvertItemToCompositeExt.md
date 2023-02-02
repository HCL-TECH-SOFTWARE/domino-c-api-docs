##### Function : Item Conversion
##### ConvertItemToCompositeExt - Converts text item to composite item, allowing use of NLS_INFO structure.
---
##### #include <ods.h>
STATUS LNPUBLIC **ConvertItemToCompositeExt(**

	BLOCKID  ItemValue,
	DWORD  ItemValueLength,
	FONTID  CompositeFont,
	char far *LineDelimiter,
	WORD  ParaDelimiterFlags,
	DHANDLE far *rethBuffer,
	DWORD far *retBufferLength,
	NLS_PINFO  pInfo,
	int  CDFileFD,
	BOOL  fAppendToFile);
**Description :**
This function converts an item of TYPE_TEXT to an item of TYPE_COMPOSITE, 
allowing the use of the NLS_INFO structure.  It takes as input a text item, its 
length, a font style, a line delimiter, and a paragraph marker.  The function 
returns as output a HANDLE to the composite item and the length of the 
composite item.

This function is very useful in Import/Export Dynamic Link Libraries (DLLs) and 
E-Mail Gateways where plain text or data with imbedded control characters must 
be converted to Rich Text.

Note:  Your program is responsible for freeing any memory associated with a 
valid handle returned in argument 6.
**Parameters :**
Input :
ItemValue  -  BLOCKID of the TYPE_TEXT item's value.

ItemValueLength  -  DWORD containing size of item's value.

CompositeFont  -   FONTID to use in conversion.  Structure contains font typeface, size, color and attribute.  Use DEFAULT_FONT_ID for 10 point, plain, black, Helvetica (also known as Swiss).  These are defined in fontid.h.

LineDelimiter  -   A pointer to a null-terminated string containing character(s) used to separate input lines.  Common delimeters include "", "\r\n", and "\n".  The delimiter string is used to parse each logical line in the input item into "paragraphs", and then it is stripped from the text stream and never included in the resulting composite item.

ParaDelimiterFlags  -   WORD describing method to be used for recognizing input paragraphs and how the resulting paragraphs are to be displayed in Notes. These are defined in PARADELIM_xxx.

pInfo  -  A pointer to an NLS_INFO struct, which contains all of the tables and attributes of the current character set. The NLS_INFO struct should have been initialized by a previous call to OSGetLMBCSCLS().  (NULL if text item already in the Lotus Multibyte Character Set (LMBCS)).

CDFileFD  -  For internal use only - specify 0 (ZERO).

fAppendToFile  -  For internal use only - specifiy FALSE.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR  - upon successful conversion 

ERR_DATATYPE - if item argument was not TYPE_TEXT  

ERR_ODS_TEXT_TOOBIG - if the item argument was greater than 60K.

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that It is best to use the code in a call to 

OSLoadString and display/log the error for the user as your default error handling.


rethBuffer  -  Address of a HANDLE in which the handle to the completed composite buffer will be returned.  Your program is responsible for disposing of this memory object when it is done via OSMemFree().

retBufferLength  -   Address of a DWORD in which the length of completed composite buffer will be returned.

**Sample Usage :**
```
/* Convert the Text to CD and copy ret'd Block to temp CD file   */

usError = ConvertItemToCompositeExt(
               ImpTextBID,   /* BLOCKID of TEXT ITEM just fabricated*/
               dwTextLen,                    /* Length of TEXT ITEM */
               EditorData->FontID, /* Use FontID provided by Editor */
               szEOL,             /* using "\r\n" as line delimiter */
               ParaDelimiters, /* using ANYBLANKLINE para delimiter */
               &hCDBuf,            /* ret'd handle to CD buffer     */
               &dwCDItemLen,         /* ret'd len of composite item */
               NULL,            
               0,                                 /* Reserved */
               FALSE);                            /* Reserved */

if (usError)
  goto Exit;
else
  wCleanUp |= FREE_HCDBUF;

```
**See Also :**
[EnumCompositeBuffer](D:/md_files/EnumCompositeBuffer.md)
[ConvertItemToText](D:/md_files/ConvertItemToText.md)
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[NSFItemConvertToText](D:/md_files/NSFItemConvertToText.md)
[NSFItemConvertValueToText](D:/md_files/NSFItemConvertValueToText.md)
[NSFItemInfo](D:/md_files/NSFItemInfo.md)
[NSFNoteClose](D:/md_files/NSFNoteClose.md)
[NSFNoteOpen](D:/md_files/NSFNoteOpen.md)
[NSFNoteUpdate](D:/md_files/NSFNoteUpdate.md)
[OSMemFree](D:/md_files/OSMemFree.md)
---
