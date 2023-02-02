##### Function : Canonical Format Conversion
##### ODSWriteMemory - Convert a structure from machine-specific format to canonical format.
---
##### #include <ods.h>
void LNPUBLIC **ODSWriteMemory(**

	void far *ppDest,
	WORD  type,
	const void far *pSrc,
	WORD  iterations);
**Description :**
This function converts Domino data structures from machine-specific (host) 
format to Domino canonical format.  It writes the result into a memory buffer 
provided by the caller.

You must convert data structures to Domino canonical format before appending 
them to a note if (1) your API program runs on non-Intel architecture machines, 
and (2) your API program is writing a Domino data item of one of the data types 
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

For example, if your API program runs under UNIX, after initializing a data 
structure of type CDPARAGRAPH, you must use ODSWriteMemory() to convert the 
structure to Domino canonical format and write the canonical format data to a 
buffer before calling NSFItemAppend to append the buffer as an item of 
TYPE_COMPOSITE to a note.

If your API program runs only under Windows, then ODSWriteMemory() is not 
necessary, but will do no harm.  Proper use of ODSWriteMemory() makes your code 
portable across platforms.

Do not use OSDWriteMemory() for Domino data types other than those listed 
above.  Domino and Notes convert non-item data (such as note header data) and 
item data of other types to canonical format automatically.
**Parameters :**
Input :
ppDest  -  Address of a void pointer that points to the destination memory buffer.  ODSWriteMemory writes the canonical form of the Domino structure to this buffer.  The caller is responsible for ensuring that the specified buffer has sufficient space to hold the data.

type  -  ODS type - identifies the Domino data structure.  The ODS type symbol is the underscore character followed by the Domino data structure name. For example,  _CDPARAGRAPH identifies a CDPARAGRAPH data structure.  See Symbolic Value _xxx (ODS Types) for a list of all valid ODS types.

pSrc  -  Pointer to the Domino data structure in machine-specific (host) format.  Normally, this is the address of a variable of the type identified by the type argument. If iterations > 1, pSrc specifies an array of structures of this type.

iterations  -  Specifies the number of data structures located at the address specified by pSrc.

Output :
ppDest  -  After writing the canonical form of the Domino structure to the buffer, ODSWriteMemory advances the specified void pointer to point to the next byte after the structure written.

**Sample Usage :**
```

void               *pCBuf;
COLLATION           Collation;
COLLATE_DESCRIPTOR  CollateDesc;
COLLATE_DESCRIPTOR  CollateDesc2;

/* 
 * Initialize pCBuf. Keep pCollationBuffer pointing to the top 
 * of the buffer, and pCBuf pointing to the next available byte.
 */
    pCBuf = (void *)pCollationBuffer;

/* Initialize the Collation structure. */

    Collation.Items = 1;
    Collation.Flags = NIF_STAT_NONE;
    Collation.signature = COLLATION_SIGNATURE;
    Collation.BufferSize = wCollationBufLen;
/*
 * Convert the Collation structure to Domino canonical format and
 * store it in the ODS buffer.
 */

    ODSWriteMemory( &pCBuf, _COLLATION, &Collation, 1 );
    
/*
 *  Initialize the collation descriptor for the first column. The
 *  first column is a category.
 */

    CollateDesc.Flags = 0;   
    CollateDesc.signature = COLLATE_DESCRIPTOR_SIGNATURE;
    CollateDesc.keytype = COLLATE_TYPE_CATEGORY;
    CollateDesc.NameOffset = 0;
    CollateDesc.NameLength = wItemName_1_Len;

/*
 * Convert the collation descriptor for the first column to Domino 
 * canonical format, and store it in the buffer.
 */

    ODSWriteMemory( &pCBuf, _COLLATE_DESCRIPTOR, &CollateDesc, 1 );

/*
 * Initialize the collation descriptor for the second column. The
 * second column is sorted.
 */

    CollateDesc2.Flags = 0;
    CollateDesc2.signature = COLLATE_DESCRIPTOR_SIGNATURE;
    CollateDesc2.keytype = COLLATE_TYPE_KEY;
    CollateDesc2.NameOffset =  wItemName_1_Len;
    CollateDesc2.NameLength = wItemName_2_Len;

/*
 * Convert the collation descriptor for the second column to Domino 
 * canonical format, and store it in the buffer.
 */

    ODSWriteMemory( &pCBuf, _COLLATE_DESCRIPTOR, &CollateDesc2, 1 );

/*  Append the column 1 item name to the buffer. */
    
    memcpy( pCBuf, szItemName_1, wItemName_1_Len );
    pCBuf += wItemName_1_Len;

/*  Append the column 2 item name to the buffer. */
    
    memcpy( pCBuf, szItemName_2, wItemName_2_Len );
    pCBuf += wItemName_2_Len;

/*  Now append the $COLLATION item to the note. */
    
    sError = NSFItemAppend( hNote,
                            ITEM_SUMMARY,
                            VIEW_COLLATION_ITEM,
                            sizeof(VIEW_COLLATION_ITEM) - 1,
                            TYPE_COLLATION,
                            pCollationBuffer,
                            (DWORD) wCollationBufLen );

    OSUnlockObject( hCollationBuffer);
    OSMemFree( hCollationBuffer );
```
**See Also :**
[NSFItemAppend](D:/md_files/NSFItemAppend.md)
[NSFItemInfo](D:/md_files/NSFItemInfo.md)
[ODSLength](D:/md_files/ODSLength.md)
[ODSReadMemory](D:/md_files/ODSReadMemory.md)
[_xxx (ODS Types)](D:/md_files/_xxx (ODS Types).md)
---
