##### Function : Data Manipulation
##### NSFNoteContract - Compress range/list types in a note to simple data types.
---
##### #include <nsfnote.h>
STATUS LNPUBLIC **NSFNoteContract(**

	NOTEHANDLE  hNote);
**Description :**
This function will compress data in a note to simple data types.  If the 
following types have a length of 1, NSFNoteContract will convert the type into 
the corresponding simple data type.

Type: TYPE_TEXT_LIST   Length: 1 Simple Data Type:TYPE_TEXT
Type: TYPE_NUMBER_RANGE  Length:1 Simple Data Type: TYPE_NUMBER
Type: TYPE_TIME_RANGE  Length:1 Simple Data Type: TYPE_TIME
**Parameters :**
Input :
hNote  -  A NOTEHANDLE to an existing note.

Output :
(routine)  -  Return status from this call -- indicates either sucess or what the error is. The return codes include:

NOERROR - Note successfully copied.
ERR_xxx - STATUS returned from a lower level Notes function.  This value can be passed to OSLoadString to obtain a text string that can be presented in a dialog box or log entry.


**See Also :**
[TYPE_xxx](D:/md_files/TYPE_xxx.md)
---
