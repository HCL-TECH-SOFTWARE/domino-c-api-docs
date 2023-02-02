##### Function : Canonical Format Conversion
##### ODSLength - Get the length of a data structure in Domino canonical format
---
##### #include <ods.h>
WORD LNPUBLIC **ODSLength(**

	WORD  type);
**Description :**
This function returns the length, in bytes, of a data structure in Domino 
canonical format.  Use this function when calculating the buffer size needed to 
contain data structures converted to Domino canonical format.

Domino canonical format is defined as Intel-architecture byte ordering with no 
pad bytes.  All data in Domino database files is stored in canonical format. On 
Intel-architecture machines, the ODS length of a data structure is the same as 
the sizeof() that data structure.  

Normally, on Intel-architecture machines, data types need not be aligned to 
addresses which are multiples of the data type size.  On non-Intel systems, 
however, a data type is normally aligned on an address which is a multiple of 
the data type size.  This means that on non-Intel systems, many data structures 
contain unused bytes.  Therefore, the overall length of a data structure in 
memory (machine specific format) may be greater than when stored in a Domino 
database file on disk (canonical format).  The ODSLength function provides a 
way for API programs to determine the size of a data structure when converted 
to Domino canonical format.
**Parameters :**
Input :
type  -  ODS type word - identifies the Domino data structure.  The ODS type symbol is the underscore character followed by the Domino data structure name. For example,  _CDPARAGRAPH identifies a CDPARAGRAPH data structure. See Symbolic Value _xxx (ODS Types) for a list of the valid ODS type words.

Output :
(routine)  -  Length of the data structure in Domino canonical format


**Sample Usage :**
```
	/*
 * Create the $VIEWFORMAT item (also known as "View Table Format item"). The 
$VIEWFORMAT 
 * item is an item of TYPE_VIEW_FORMAT with name VIEW_VIEW_FORMAT_ITEM.
 *
 * The $VIEWFORMAT item for this view will consist of the following 
 * series of structures converted to Domino canonical format and packed 
together:
 *
 *          VIEW_TABLE_FORMAT
 *          VIEW_COLUMN_FORMAT (for column 1)
 *          VIEW_COLUMN_FORMAT (for column 2)
 *          VIEW_COLUMN_FORMAT (for column 3)
 *          Item Name for column 1
 *          formula for column 1
 *          Item Name for column 2
 *          Title for column 2
 *          formula for column 2
 *          Item Name for column 3
 *          Title for column 3
 *          formula for column 3
 *          VIEW_TABLE_FORMAT2
	 *
 *
 * First, allocate a buffer, pViewFormatBuffer, that will contain the 
 * entire $VIEWFORMAT item. 
 */
      

    wViewFormatBufLen = ODSLength( _VIEW_TABLE_FORMAT )   +
                        ODSLength( _VIEW_COLUMN_FORMAT )  +
                        ODSLength( _VIEW_COLUMN_FORMAT )  +
                        ODSLength( _VIEW_COLUMN_FORMAT )  +
                        wItemName_1_Len                   +
                        wFormula_1_Len                    +
                        wItemName_2_Len                   +
                        wTitle_2_Len                      +
                        wFormula_2_Len                    +
                        wItemName_3_Len                   +
                        wTitle_3_Len                      +
                        wFormula_3_Len                    +
                        ODSLength( _VIEW_TABLE_FORMAT2 )  ;
  

    if (sError = OSMemAlloc( 0, wViewFormatBufLen, &hViewFormatBuffer ))
    {
         printf("Error: unable to allocate %d bytes memory.\n", 
            wViewFormatBufLen);
         goto Exit3;
    }
```
**See Also :**
[ODSReadMemory](D:/md_files/ODSReadMemory.md)
[ODSWriteMemory](D:/md_files/ODSWriteMemory.md)
[_xxx (ODS Types)](D:/md_files/_xxx (ODS Types).md)
---
