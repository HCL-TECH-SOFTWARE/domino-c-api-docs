##### Function : Canonical Format Conversion
##### ODSReadMemory - Convert a structure from canonical format to machine-specific format.
---
##### #include <ods.h>
void LNPUBLIC **ODSReadMemory(**

	void far *ppSrc,
	WORD  type,
	void far *pDest,
	WORD  iterations);
**Description :**
This function converts Domino data structures from Domino canonical format to 
machine-specific (host) format. This writes the result into a variable or 
memory buffer provided by the caller.

You must convert data structures to host format before accessing the members of 
the structure if (1) your API program runs on non-Intel architecture machines, 
and (2) your API program is reading a Domino data item of one of the data types 
listed below:

    TYPE_COMPOSITE
    TYPE_COLLATION
    TYPE_OBJECT
    TYPE_VIEW_FORMAT
    TYPE_ICON
    TYPE_SIGNATURE
    TYPE_SEAL
    TYPE_SEALDATA
    TYPE_SEAL_LIST
    TYPE_WORKSHEET_DATA
    TYPE_USERDATA
    TYPE_QUERY
    TYPE_ACTION
    TYPE_ASSISTANT_INFO
    TYPE_VIEWMAP_DATASET
    TYPE_VIEWMAP_LAYOUT
    TYPE_CALENDAR_FORMAT

For example, if your API program runs under UNIX and reads a CDFONTTABLE 
structure from an item of type TYPE_COMPOSITE, you must use ODSReadMemory() to 
convert the CDFONTTABLE to machine-specific format before you access the 
members of the CDFONTTABLE structure.

If your API program runs under Windows, then ODSReadMemory() is not necessary, 
but will do no harm. Therefore, code that uses ODSReadMemory() properly is 
portable across platforms.

For items of any data type other than those listed above, and for Domino data 
structures in general, you must not use ODSReadMemory() because Domino and 
Notes automatically convert such data to host format for you. Therefore, your 
API program should directly access non-item data (e.g. note header data) and 
data of other data types (such as TYPE_TIME).

Note that the data type word at the beginning of an item data value is almost 
always in host format. When using functions such as NSFItemInfo() to read an 
item value, the item value begins with a data type WORD. Domino and Notes 
convert this data type WORD to host format for you, even if the rest of the 
item data is in canonical format.  

There is an exception with Domino database hook drivers and extension manager 
API programs.  A Domino database hook driver or an extension manager API 
program may receive all note item data, including the data type WORD in 
canonical format.  A Domino hook driver or an extension manager that accesses 
note item data over a network in which the note was not opened by the hook 
driver or extension manager itself, must check the OpenFlags parameter in the 
NoteOpen callback function (if the program is a database hook driver) or in the 
callback function for EM_NSFNOTEOPEN or EM_NSFNOTEOPENBYUNID (if the program is 
an extension manager) to see whether this flag is set. If this flag is set, use 
ODSReadMemory to convert any note item data to host format.

**Parameters :**
Input :
ppSrc  -  Address of a void pointer that points to the source memory buffer.  ODSReadMemory reads the Domino canonical form data structure(s) from this buffer.

type  -  ODS type word - identifies the Domino data structure.  The ODS type symbol is the underscore character followed by the Domino data structure name. For example,  _CDPARAGRAPH identifies a CDPARAGRAPH data structure.  See Symbolic Value _xxx (ODS Types) for a list of the valid ODS type words.

iterations  -  Specifies the number of structures at the address specified by pDest.

Output :
ppSrc  -  ODSReadMemory changes the specified void pointer to point to the next byte after the canonical form of the Domino structure read from the buffer.  This facilitates reading a sequence of structures in canonical form from a buffer by making a sequence of calls to ODSReadMemory.

pDest  -  Pointer to the variable or buffer to receive data in machine-specific format.  Normally, this is the address of a variable of a type identified by the type argument.  If iterations > 1, pDest specifies an array of structures of that type.  The caller is responsible for ensuring that the specified buffer has sufficient space to hold the data.

**Sample Usage :**
```

    void           *pItemValue;
    CDFONTTABLE     cdFontTab;
    CDFACE          cdFace;
    WORD            wIndex;

   /* RecordPtr points to the first byte of the item value after the
      datatype word. The item value is in Domino canonical format. It
      starts with a CDFONTTABLE structure. Call ODSReadMemory() to
      convert this CDFONTTABLE to host format and store it in
      cdFontTab. ODSReadMemory() increments pItemValue to point to
      the next byte in the input buffer after the CDFONTTABLE.
    */

    pItemValue = RecordPtr;
    ODSReadMemory( &pItemValue, _CDFONTTABLE, &cdFontTab, 1 );

    for (wIndex = 0; wIndex < cdFontTab.Fonts; wIndex++)
    {
        ODSReadMemory( &pItemValue, _CDFACE, &cdFace, 1 );
        printf( "    Font %d:\n", wIndex );
        printf( "       Face    = %d\n", cdFace.Face );
        printf( "       Family  = %d\n", cdFace.Family );
        printf( "       Name    = %s\n", cdFace.Name );
    }
```
**See Also :**
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[NSFItemInfo](D:/md_files/NSFItemInfo.md)
[ODSLength](D:/md_files/ODSLength.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
[_xxx (ODS Types)](D:/md_files/_xxx (ODS Types).md)
---
