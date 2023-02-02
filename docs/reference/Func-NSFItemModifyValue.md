##### Function : Database
##### NSFItemModifyValue - Modify the value of an item in an opened note.
---
##### #include <nsfnote.h>
STATUS **NSFItemModifyValue(**

	DHANDLE  hnote,
	BLOCKID  bhItem,
	WORD  ItemFlags,
	WORD  DataType,
	const void *Value,
	DWORD  ValueLength);
**Description :**
Modify the value of an item in an opened note according to parameters provided 
as an argument.
**Parameters :**
Input :
hnote  -  An open Note handle.

bhItem  -  Block ID of item with value to be modified.

ItemFlags  -  New item flags for the item, ITEM_xxx is the symbol value that can be used in this argument.

DataType  -  New data type of value that need to be modified in the existing item value. Refer TYPE_xxx symbols for possible types.

Value  -  ADDRESS of item new value that modifies existing.

ValueLength  -  Length of new item value.

Output :
(routine)  -  Return status from the call either success or an error. 
              NOERROR, on success.


**Sample Usage :**
```
	WORD m_wItemflags = ITEM_SUMMARY; 
	WORD m_wItemtype = TYPE_TEXT; 
	char m_szItemname[MAX_STRING]; 
   STATUS error = NOERROR; 
   /* hNote is a NOTEHANDLE for an open document. */ 

	Cstrcpy(m_szItemname,"TextItem"); 

	if (error = NSFItemInfo(hNote, m_szItemname, Cstrlen(m_szItemname), 
&bhItem, NULL, NULL, NULL)) 
	{ 
	 printf("Error returned from NSFItemInfo = %e\n ", error); 
	 return error; 
	} 
	if(error = NSFItemModifyValue(hNote, bhItem, ITEM_SUMMARY, m_wItemtype, 
m_szExpValue, Cstrlen(m_szExpValue))) 
	{ 
	 printf("Error returned from NSFItemModifyValue = %e", error); 
	 return error; 
	}
```
**See Also :**
[](D:/md_files/.md)
---
