




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



**CDFONTTABLE** **-** Used in
creating a font table.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    WSIG    Header; /\* Tag and length \*/  

    WORD    Fonts;  /\* Number of CDFACEs following \*/  

} CDFONTTABLE;            /\* Now come the CDFACE records... \*/


 


**Description :**



This defines
part of the structure of a font table item in a note.  A font table item in a
note allows rich text in the note to be displayed using fonts other than those
defined in FONT\_FACE\_xxx.


  

Font table items are items with name $Fonts (ITEM\_NAME\_FONTS) and data type
TYPE\_COMPOSITE.  A font table consists of a CDFONTTABLE structure followed by
any number of CDFACE structures.  

  

Note that font tables are items of type TYPE\_COMPOSITE. Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CDFONTTABLE and CDFACE structures when accessing these records in
a font table item in a note.  

  

        Header        Tag identifying this as a CDFONTTABLE record  

        Fonts            Number of CDFACE records following this header record  

  




 **Sample Usage :**


typedef struct {  

   WSIG  Header;           /\* Tag and length \*/  

   WORD  Fonts;            /\* Number of CDFACEs following \*/  

} CDFONTTABLE;             /\* Now come the CDFACE records... \*/  

  




 **See Also :**


**[CDFACE](CDFACE.md)**



----------------------------------------------------------------------------------------------------------


 





