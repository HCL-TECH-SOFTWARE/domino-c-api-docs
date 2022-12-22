




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
@font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




 


**Symbolic Value : Rich Text**



**CDTC\_xxx** **-** Field mask
and shift symbols for table cell border information.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDTC\_S\_Left           -  Number of bits to shift for the
left border field.  

  

      CDTC\_M\_Left           -  Bit mask for the left border field.  

  

      CDTC\_S\_Right         -  Number of bits to shift for the right border
field.  

  

      CDTC\_M\_Right        -  Bit mask for the right border field.  

  

      CDTC\_S\_Top           -  Number of bits to shift for the top border field.  

  

      CDTC\_M\_Top          -  Bit mask for the top border field.  

  

      CDTC\_S\_Bottom      -  Number of bits to shift for the bottom border
field.  

  

      CDTC\_M\_Bottom      -  Bit mask for the bottom border field.  

  




**Description :**



The border
information for a table cell is stored in the Border field of the CDTABLECELL
record.  The information for each of the 4 borders of the cell is stored in a
separate 2-bit field.  These symbols are used to acess the individual fields; 
the values stored in these fields are defined in the entry for
TABLE\_BORDER\_xxx.


 **Sample Usage :**


void  LNPUBLIC  
DumpCDTablecell( char \* RecordPtr, DWORD RecordLength )  

{  

    void     far    \*p = (void \*)RecordPtr;  

    CDTABLECELL     cdTableCell;  

    WORD            Border;  

    WORD            LeftBorder;  

    WORD            RightBorder;  

    WORD            TopBorder;  

    WORD            BottomBorder;  

    static  char    \*pachBorders[4] = {"NONE", "SINGLE",
"DOUBLE", "Unknown (3)"};


 


   
ODSReadMemory( &p, \_CDTABLECELL, &cdTableCell, 1 );


    Border
= (WORD)cdTableCell.Border;


 


   
LeftBorder  = ( (WORD)(Border & CDTC\_M\_Left  ) >> CDTC\_S\_Left  );  

    RightBorder = ( (WORD)(Border & CDTC\_M\_Right ) >> CDTC\_S\_Right );  

    TopBorder   = ( (WORD)(Border & CDTC\_M\_Top   ) >> CDTC\_S\_Top );  

    BottomBorder= ( (WORD)(Border & CDTC\_M\_Bottom) >> CDTC\_S\_Bottom
);


 


   
fprintf( dumpfile, "        Left Border     = %s\n",  

                    pachBorders[LeftBorder] );


 


   
fprintf( dumpfile, "        Right Border    = %s\n",  

                    pachBorders[RightBorder] );


 


   
fprintf( dumpfile, "        Top Border      = %s\n",  

                    pachBorders[TopBorder] );


 


   
fprintf( dumpfile, "        Bottom Border   = %s\n",  

                    pachBorders[BottomBorder] );


    /\* ...
\*/


}


 **See Also :**


**[CDTABLECELL](CDTABLECELL.md)**


**[TABLE\_BORDER\_xxx](TABLE_BORDER_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





