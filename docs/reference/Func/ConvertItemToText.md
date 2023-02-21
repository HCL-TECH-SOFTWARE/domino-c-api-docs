##### Function : Item Conversion
##### ConvertItemToText - Convert composite or text item to character text.
---
```
#include <ods.h>
STATUS LNPUBLIC ConvertItemToText(

	BLOCKID  ItemValue,
	DWORD  ItemValueLength,
	const char far *LineDelimiter,
	WORD  CharsPerLine,
	DHANDLE far *rethBuffer,
	DWORD far *retBufferLength,
	BOOL  fStripTabs);
```
**Description :**

This function formats an item of either TYPE_COMPOSITE or TYPE_TEXT into a 
character text buffer.  It takes as input a composite or text item,  its 
length, number of characters desired per output line, the desired output line 
delimiter(s), and whether or not tabs should be stripped. The function returns 
as output a buffer containing character text and embedded "new line" characters 
and also returns the length of the text buffer.

If line_delimiter = "", then each output line in the returned text buffer would 
end in '\0'.  Note: a '\0' anywhere in an item of TYPE_TEXT forces Notes to 
display a new line.  If line_delimiter = "\r\n", then each output line would 
end with a return-newline pair.

Note: Some degree of experimentation with the original Rich Text is required, 
before you can be assured that its basic appearance (tabs and line lengths) 
will be maintained during the conversion.  If there are embedded tabs in the 
original item, their contribution to the converted line length is always taken 
as eight (8) spaces.  Example: The original Rich Text may be setup with tabs at 
.5"  intervals(about 4 spaces for 8 point plain Courier), but their value in 
equivalent spaces is ignored. If there are 4 tabs embedded in a line of Rich 
Text, they will account for 32 characters in the output line length calculation.

This function is very useful in E-Mail Gateways where Domino Rich Text must be 
converted to plain character text.  It can also be used to reformat existing 
Domino Text Items to new margins and/or to strip tabs from the item.

Note: the returned buffer must be deallocated by the caller via OSMemFree().

**Parameters :**
Input :
ItemValue  -  BLOCKID for value of item, including the data type WORD.

ItemValueLength  -  Length of item's value, including data type WORD.

LineDelimiter  -  A pointer to a null-terminated string containing characters to be appended to the end of each output line.  If "" is specified, then each line will be delimited with a '\0'.

CharsPerLine  -  Desired length of output line(s).

fStripTabs  -  Flag indicating whether or not to strip tabs during conversion. TRUE = strip tabs and FALSE = do not strip tabs during conversion.

Output :
(routine)  -  Return indicates either success or what the error is. The return codes include:

NOERROR - upon successful conversion

ERR_DATATYPE - if item is not of TYPE_COMPOSITE or TYPE_TEXT

ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling.


rethBuffer  -  The address of a HANDLE in which a handle to a buffer containing the converted text will be returned.  This handle must be deallocated by the caller via OSMemFree().

retBufferLength  -  The address of a DWORD in which the length of the converted text buffer will be returned.


**Sample Usage :**
```

   /* Convert the Object associated with the BID to a plain text  */
   /* buffer. ConvertItemToText throws away CD Records that don't */
   /* map to text: Document Links, DDE Links, Graphics, etc.      */
 
  if (Error_Status = ConvertItemToText (bidTmpCD, TmpCDLen,
                                        LineDelimiter, CharsPerLine,
                                        &hExpBuffer, &ExpBufferLength,
                                        fStripTabs))
   {
       goto Exit;
   }
   else
       CleanUp_State += FREE_EXPBUFFER;

```
**See Also :**
[ConvertItemToCompositeExt](/domino-c-api-docs/reference/Func/ConvertItemToCompositeExt)
[EnumCompositeBuffer](/domino-c-api-docs/reference/Func/EnumCompositeBuffer)
[NSFItemAppend](/domino-c-api-docs/reference/Func/NSFItemAppend)
[NSFItemConvertToText](/domino-c-api-docs/reference/Func/NSFItemConvertToText)
[NSFItemConvertValueToText](/domino-c-api-docs/reference/Func/NSFItemConvertValueToText)
[NSFItemInfo](/domino-c-api-docs/reference/Func/NSFItemInfo)
[NSFNoteClose](/domino-c-api-docs/reference/Func/NSFNoteClose)
[NSFNoteOpen](/domino-c-api-docs/reference/Func/NSFNoteOpen)
[NSFNoteUpdate](/domino-c-api-docs/reference/Func/NSFNoteUpdate)
[OSMemFree](/domino-c-api-docs/reference/Func/OSMemFree)
---
