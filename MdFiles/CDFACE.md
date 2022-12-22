




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




 


**Data Type : Composite Data; Rich
Text**



**CDFACE** **-** Used in
creating a font table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BYTE Face;              /\* ID number of face \*/  

   BYTE Family;            /\* Font Family \*/  

   char Name[MAXFACESIZE];  

} CDFACE;


 


**Description :**



This defines
part of the structure of a font table item in a note.  A font table item in a
note allows rich text in the note to be displayed using fonts other than those
defined in FONT\_FACE\_xxx.  

  

Font table items are items with name $FONT (ITEM\_NAME\_FONTS) and data type
TYPE\_COMPOSITE. a font table consists of a CDFONTTABLE structure followed by
any number of CDFACE structures.  Each CDFACE entry in the font table defines
one font face.  

  

Note that font tables are items of type TYPE\_COMPOSITE. Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CDFACE structures when accessing these records in a font table
item in a note.  

  

The Face member of the CDFACE structure is an application assigned byte,
greater than or equal to STATIC\_FONT\_FACES (5).     

  

The Family member of the CDFACE structure is a bit mask byte.  The two low
order bits (0-1) specify the pitch of the font.  The four high-order bits (4-7)
specify the font family.  Bit 2 is set for Microsoft TrueType fonts.  For
Windows 32-bit, bit 3 is set for monospaced fonts.  

  

/\* Family member values of the CDTEXT structure \*/  

/\* The Family member (a BYTE) is a bit mask \*/  

/\* These definitions are in WINDOWS.H \*/   

  




/\* TrueType
flag (bit 2) \*/


#define
TRUETYPE\_FONTTYPE   0x004  

  

/\* "pitch" values (low 2 bits) \*/  

#define DEFAULT\_PITCH    0x00  

#define FIXED\_PITCH            0x01  

#define VARIABLE\_PITCH   0x02


#if(WINVER
>= 0x0400)  

#define MONO\_FONT               8         /\* Monospace flag (bit 3) \*/  

#endif /\* WINVER >= 0x0400 \*/


  

/\* "family" values (high 4 bits) \*/  

#define FF\_DONTCARE      0x00  

#define FF\_ROMAN               0x10  

#define FF\_SWISS                 0x20  

#define FF\_MODERN           0x30  

#define FF\_SCRIPT               0x40  

#define FF\_DECORATIVE  0x50  

  

The Name member of the CDFACE structure is the IfFaceName member of the LOGFONT
structure in Windows.  

  

To use a font from the font table in a rich text field run of text, set the Face
member of the FONTIDFIELDS structure of the FontID member of the CDTEXT
structure to the font table's application assigned byte in the Face member of
the CDFACE structure.  

  




 **See Also :**


**[CDFONTTABLE](CDFONTTABLE.md)**


**[CDTEXT](CDTEXT.md)**


**[FONTIDFIELDS](FONTIDFIELDS.md)**



----------------------------------------------------------------------------------------------------------


 





