##### Function : Formula
##### NSFTranslateSpecial - Translate @Function Escape Sequences
---
##### #include <nsfdata.h>
STATUS LNPUBLIC **NSFTranslateSpecial(**

	void far *InputString,
	WORD  InputStringLength,
	void far *OutputString,
	WORD  OutputStringBufferLength,
	NOTEID  NoteID,
	void far *IndexPosition,
	INDEXSPECIALINFO far *IndexInfo,
	DHANDLE  hUnreadList,
	DHANDLE  hCollapsedList,
	char far *FileTitle,
	char far *ViewTitle,
	WORD far *retLength);
**Description :**
Some @Functions cannot be translated when the formula is evaluated.  Instead, 
the value must be obtained when the result is to be displayed or used.  These 
functions place a special escape sequence in the result string where the actual 
values is to be placed.  The routine NSFTranslateSpecial() substitutes the 
actual values for the escape sequence.

@Functions which generate these escape sequences are:

        @DocNumber
        @DocSiblings
        @DocChildren
        @DocDescendants
        @IsExpandable
        @DocLevel
        @IsCategory
        @DocParentNumber

**Parameters :**
Input :
InputString  -  Address of the input string to be translated.

InputStringLength  -  Length of the input string.

OutputStringBufferLength  -  Size of the output string buffer.

NoteID  -  ID of the note being translated.

IndexPosition  -  Address of a COLLECTIONPOSITION containing the index position.

IndexInfo  -  Address of an INDEXSPECIALINFO containing miscellaneous index information.

hUnreadList  -  Handle of the "Unread" note ID list.

hCollapsedList  -  Handle of the "Collapsed" note ID list.

FileTitle  -  Address of the null-terminated notefile title string.

ViewTitle  -  Address of the null-terminated view title string.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Operation succeeded.


OutputString  -  Address of the output string buffer.

retLength  -  Length of the output string

**See Also :**
[INDEXSPECIALINFO](D:/md_files/INDEXSPECIALINFO.md)
---
