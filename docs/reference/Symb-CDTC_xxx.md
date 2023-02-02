##### Symbolic Value : Rich Text
##### CDTC_xxx - Field mask and shift symbols for table cell border information.
---
##### #include <editods.h>
**Description :**
The border information for a table cell is stored in the Border field of the 
CDTABLECELL record.  The information for each of the 4 borders of the cell is 
stored in a separate 2-bit field.  These symbols are used to acess the 
individual fields;  the values stored in these fields are defined in the entry 
for TABLE_BORDER_xxx.
**Sample Usage :**
```
void  LNPUBLIC   DumpCDTablecell( char * RecordPtr, DWORD RecordLength )
{
    void     far    *p = (void *)RecordPtr;
    CDTABLECELL     cdTableCell;
    WORD            Border;
    WORD            LeftBorder;
    WORD            RightBorder;
    WORD            TopBorder;
    WORD            BottomBorder;
    static  char    *pachBorders[4] = {"NONE", "SINGLE", "DOUBLE", "Unknown 
(3)"};

    ODSReadMemory( &p, _CDTABLECELL, &cdTableCell, 1 );
    Border = (WORD)cdTableCell.Border;

    LeftBorder  = ( (WORD)(Border & CDTC_M_Left  ) >> CDTC_S_Left  );
    RightBorder = ( (WORD)(Border & CDTC_M_Right ) >> CDTC_S_Right );
    TopBorder   = ( (WORD)(Border & CDTC_M_Top   ) >> CDTC_S_Top );
    BottomBorder= ( (WORD)(Border & CDTC_M_Bottom) >> CDTC_S_Bottom );

    fprintf( dumpfile, "        Left Border     = %s\n",
                    pachBorders[LeftBorder] );

    fprintf( dumpfile, "        Right Border    = %s\n",
                    pachBorders[RightBorder] );

    fprintf( dumpfile, "        Top Border      = %s\n",
                    pachBorders[TopBorder] );

    fprintf( dumpfile, "        Bottom Border   = %s\n",
                    pachBorders[BottomBorder] );
    /* ... */
}
```
**See Also :**
[CDTABLECELL](D:/md_files/CDTABLECELL.md)
[TABLE_BORDER_xxx](D:/md_files/TABLE_BORDER_xxx.md)
---
