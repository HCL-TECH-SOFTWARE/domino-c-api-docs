




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 4.5**



**Symbolic Value : Rich Text**



**CDTC\_xxx\_V42\_xxx** **-** Field mask
and shift symbols for table cell border width in Domino Release 4.5 and above.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      CDTC\_S\_V42\_Left    -  Number of bits to shift for the left
border field.  

  

      CDTC\_M\_V42\_Left   -  Bit mask for the left border field.  

  

      CDTC\_S\_V42\_Right             -  Number of bits to shift for the right
border field.  

  

      CDTC\_M\_V42\_Right             -  Bit mask for the right border field.  

  

      CDTC\_S\_V42\_Top   -  Number of bits to shift for the top border field.  

  

      CDTC\_M\_V42\_Top   -  Bit mask for the top border field.  

  

      CDTC\_S\_V42\_Bottom           -  Number of bits to shift for the bottom
border field.  

  

      CDTC\_M\_V42\_Bottom          -  Bit mask for the bottom border field.  

  




**Description :**



The border
width for a Domino Release 4.5 or later table cell is stored in the v42Border
field of the CDTABLECELL record.  The information for each of the 4 borders of
the cell is stored in a separate 4-bit field.  These symbols are used to acess
the individual fields;  the values stored in these fields range from 0 to 10
(0x0000 to 0x1010).


 


 **Sample Usage :**


void  LNPUBLIC  
DumpCDTablecell( char \* RecordPtr, DWORD RecordLength )


{


    void     far    \*p
= (void \*)RecordPtr;  

 CDTABLECELL     cdTableCell;  

 WORD            Border;  

 WORD            LeftBorder;  

 WORD            RightBorder;  

 WORD            TopBorder;  

 WORD            BottomBorder;


 


    if
(CDTABLECELL\_USE\_V42BORDERS & cdTableCell.Flags)  

    {  

         /\* Print the extended border widths \*/  

      Border = cdTableCell.v42Border;


 


     
LeftBorder  = ( (WORD)(Border & CDTC\_M\_V42\_Left  ) >>
CDTC\_S\_V42\_Left  );  

      RightBorder = ( (WORD)(Border & CDTC\_M\_V42\_Right ) >>
CDTC\_S\_V42\_Right );  

      TopBorder   = ( (WORD)(Border & CDTC\_M\_V42\_Top   ) >>
CDTC\_S\_V42\_Top );  

      BottomBorder= ( (WORD)(Border & CDTC\_M\_V42\_Bottom) >>
CDTC\_S\_V42\_Bottom );


     
fprintf( dumpfile, "        Left Border width   = %d\n", LeftBorder
);


     
fprintf( dumpfile, "        Right Border width  = %d\n", RightBorder
);


     
fprintf( dumpfile, "        Top Border width    = %d\n", TopBorder );


     
fprintf( dumpfile, "        Bottom Border width = %d\n", BottomBorder
);  

    }


    /\* ...
\*/


}


 **See Also :**


**[CDTABLECELL](CDTABLECELL.md)**



----------------------------------------------------------------------------------------------------------


 





