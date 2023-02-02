##### Symbolic Value : Rich Text
##### CDTC_xxx_V42_xxx - Field mask and shift symbols for table cell border width in Domino Release 4.5 and above.
---
##### #include <editods.h>
**Description :**
The border width for a Domino Release 4.5 or later table cell is stored in the 
v42Border field of the CDTABLECELL record.  The information for each of the 4 
borders of the cell is stored in a separate 4-bit field.  These symbols are 
used to acess the individual fields;  the values stored in these fields range 
from 0 to 10 (0x0000 to 0x1010).

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

    if (CDTABLECELL_USE_V42BORDERS & cdTableCell.Flags)
    {
         /* Print the extended border widths */
      Border = cdTableCell.v42Border;

      LeftBorder  = ( (WORD)(Border & CDTC_M_V42_Left  ) >> CDTC_S_V42_Left  );
      RightBorder = ( (WORD)(Border & CDTC_M_V42_Right ) >> CDTC_S_V42_Right );
      TopBorder   = ( (WORD)(Border & CDTC_M_V42_Top   ) >> CDTC_S_V42_Top );
      BottomBorder= ( (WORD)(Border & CDTC_M_V42_Bottom) >> CDTC_S_V42_Bottom );
      fprintf( dumpfile, "        Left Border width   = %d\n", LeftBorder );
      fprintf( dumpfile, "        Right Border width  = %d\n", RightBorder );
      fprintf( dumpfile, "        Top Border width    = %d\n", TopBorder );
      fprintf( dumpfile, "        Bottom Border width = %d\n", BottomBorder );
    }
    /* ... */
}
```
**See Also :**
[CDTABLECELL](D:/md_files/CDTABLECELL.md)
---
