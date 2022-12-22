




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




 


**Data Type : Rich Text**



**FONTIDFIELDS ( FONTID )** **-** Component
elements of a FONTID.


**----------------------------------------------------------------------------------------------------------**



**#include
<fontid.h>**



**Definition :**



typedef struct {  

#ifdef LITTLE\_ENDIAN\_ORDER  

    BYTE Face;             /\* Font face (FONT\_FACE\_xxx) \*/  

    BYTE Attrib;           /\* Attributes (ISBOLD,etc) \*/  

    BYTE Color;            /\* Color index (NOTES\_COLOR\_xxx) \*/  

    BYTE PointSize;        /\* Size of font in points \*/  

#else  

    BYTE PointSize;        /\* Size of font in points \*/  

    BYTE Color;            /\* Color index (NOTES\_COLOR\_xxx) \*/  

    BYTE Attrib;           /\* Attributes (ISBOLD,etc) \*/  

    BYTE Face;             /\* Font face (FONT\_FACE\_xxx) \*/  

#endif  

} FONTIDFIELDS;


 


**Description :**



This
structure allows access to the fields within a FONTID. Overlay this structure
onto the FontID field to set or read the font information for the rich text field,
or more preferably, use the FontSetxxx macros using a FONTID directly.  

  

The Face member of the FONTIDFIELDS structure may be one of three standard font
faces - - FONT\_FACE\_ROMAN, FONT\_FACE\_SWISS, or FONT\_FACE\_TYPEWRITER - - or a
font ID resolved by a font table.  A Face member value greater than or equal to
STATIC\_FONT\_FACES (5) refers to an entry in a font table.  

  

To resolve a non standard font face, the note must contain a font table.  A
font table is an item with name $FONT (ITEM\_NAME\_FONTS) and data type
TYPE\_COMPOSITE. A font table consists of a CDFONTTABLE structure followed by
any number of CDFACE structures.  If the Face member value is greater than or
equal to STATIC\_FONT\_FACES, then it must identify one of the CDFACE entries in
the font table.


 **Sample Usage :**


    CDTEXT         
cdtext;     /\* rich-text text header \*/  

    FONTIDFIELDS   \*pFontID;    /\* font definitions in text header \*/  

    char            szString1[] = "Hello world... ";  

    WORD            wString1Len = strlen( szString1 );  

  

    wString1Len += (wString1Len%2);  

  

    /\* ... steps missing ... \*/  

  

    cdtext.Header.Signature = SIG\_CD\_TEXT;  

    cdtext.Header.Length = ODSLength( \_CDTEXT ) + wString1Len ;  

  

    pFontID = (FONTIDFIELDS \*) &(cdtext.FontID);  

      

    pFontID->Face = FONT\_FACE\_SWISS;  

    pFontID->Attrib = ISBOLD;  

    pFontID->Color = NOTES\_COLOR\_BLUE;  

    pFontID->PointSize = 24;  

  

    ODSWriteMemory( &buff\_ptr, \_CDTEXT, &cdtext, 1 );


 **See Also :**


**[CDFACE](CDFACE.md)**


**[CDFONTTABLE](CDFONTTABLE.md)**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[CDPABREFERENCE](CDPABREFERENCE.md)**


**[CDPARAGRAPH](CDPARAGRAPH.md)**


**[CDTEXT](CDTEXT.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**


**[ISxxx](ISxxx.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**


**[xxx\_FONT\_ID](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5026A4E5153414BF85256258005EA4EA)**



----------------------------------------------------------------------------------------------------------


 





