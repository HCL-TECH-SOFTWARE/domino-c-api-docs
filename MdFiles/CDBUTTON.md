




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



**CDBUTTON** **-** Defines the
appearance of a button in a rich text field.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct  

    {  

    WSIG    Header; /\* Signature and length of this record. \*/  

    WORD    Flags;    

    WORD    Width;  

    WORD    Height;  

    WORD    Lines;  

    FONTID FontID;  

    /\* Button Text Follows \*/  

    } CDBUTTON;  

  




 


**Description :**



This
structure defines the appearance of a button in a rich text field.   

  

Header:      Defines this composite data item as a CDBUTTON item.  

Flags:         Optional. See BUTTON\_xxx for optional values.   

Width:        Specifies the width of the button in TWIPS (see the symbolic
definition for ONEINCH for more information).  

Height:       Reserved.  Should be set to NULL.  

Lines:         Specifies the maximum number of lines of text to use to display
the button text.  

FontID:       Specifies the font, size, and color of the text on the face of
the button. See FONTIDFIELDS for the definition of FontID.  

  

Immediately following this structure is a packed string containing the text
that appears on the face of the button.


 


      For a
button with type information, the CDBUTTON record may be followed by a
CDDATAFLAGS structure.  

  

Note that CDBUTTON records reside in items of type TYPE\_COMPOSITE. Therefore,
API programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these
records in an item in a note.


 **See Also :**


**[BUTTON\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/01390CB3A24887F485256A2A006586B2)**


**[CDDATAFLAGS](CDDATAFLAGS.md)**


**[ONEINCH](ONEINCH.md)**



----------------------------------------------------------------------------------------------------------


 





