




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDPRETABLEBEGIN** **-** Specifies
additional table properties.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG        Header;


   DWORD       Flags;


   BYTE        Rows;


   BYTE        Columns;


   DWORD      
ColumnSizingBits1;


   DWORD      
ColumnSizingBits2;


   BYTE       
ViewerType;


   BYTE        Spare;


   WORD       
MinRowHeight;


   WORD       
Spares[1];


   DWORD      
StyleColor1;


   DWORD      
StyleColor2;


   COLOR\_VALUE
InnerBorderColor;


   WORD       
NameLength;


        /\*
NOTE:       The following lengths can not be used.  Previous versions of Notes


                       are
not setup to deal with any length beyond the name length.


                       Hang
will occur if they are used and you try to open the document


                       on
a previous version of Notes.  In the same light, this sturcture's


                       size
can not be changed, no additional items of variable length


                       can
be added.


 


                       The
words could simply be used as word storage.  They just can


                       not
be useds as lengths.


        \*/


   WORD       
ImagePacketLength;


   WORD       
RowLabelDataLength;


} CDPRETABLEBEGIN;


 


**Description :**



This CD
record provides additional table properties, expanding the information provided
in CDTABLEBEGIN.  It will only be recognized in Domino versions 5.0 and
greater.  This record will be ignored in pre 5.0 versions.


 


            WSIG                           Header                         Signature
and length of this record


            DWORD                       Flags                            See
CDPRETABLE\_xxx flags


            BYTE                           Rows                            Number
of rows


            BYTE                           Columns                       Number
of columns


            DWORD                       ColumnSizingBits1        Keep
track of variable or fixed length columns


            DWORD                       ColumnSizingBits2        Keep
track of variable or fixed length columns


            BYTE                           ViewerType                  Special
table row display values.  SeeCDTABLEVIEWER\_xxx flags            


            BYTE                           Spare                           Not
currently used.  Set to 0.


            WORD                         MinRowHeight              Minimum
row height


            WORD                         Spares[1]                      Not
currently used.  Set to 0.


            DWORD                       StyleColor1                   First
color in table/cell background color scheme


            DWORD                       StyleColor2                   Second
color in table/cell background color scheme


            COLOR\_VALUE            InnerBorderColor          Inner
border color


            WORD                         NameLength                 HTML
Tag Name/ID Length       


            WORD                         ImagePacketLength      Image
Packet Length


            WORD                         RowLabelDataLength    Row
Label Data Length


 


If
the NameLength member of this structure is greater than 0, then the table's
HTML Tag Name/ID immediately follows this structure.  This is then followed by
the Image Packet data (if ImagePacketLength is greater than 0), followed by the
Row Label data (if RowLabelDataLength is greater than 0).


 


The
SyleColor1 and StyleColor2 members of this structure are each stored as a
3-byte RGB value:  Red (byte 0), Green (byte 1), and Blue (byte 2).  Each byte
is a color value in the range 0 to 0xff.  For example, 0xff0000 specifies blue,
0x00ff00 specifies green, and 0x0000ff specifies red.  The Flags setting in the
CDTABLEBEGIN structure determines how StyleColor1 and StyleColor2 are used by
the Notes client.  For example, if you specify CDTABLE\_ALTERNATINGROWS in the
Flags member of the CDTABLEBEGIN structure, then StyleColor1 and StyleColor2
specify the two alternating background colors of the rows.


 


 


  


 **See Also :**


**[CDPRETABLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5AA21676B377ED6A85256677006DDC29)**


**[CDTABLEVIEWER\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4E3B71C1BAAEE2EF85256A2A0062F83A)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[CDTABLEBEGIN](CDTABLEBEGIN.md)**


**[CDTABLE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/493D6766D913CEA28525667800467FEB)**



----------------------------------------------------------------------------------------------------------


 





