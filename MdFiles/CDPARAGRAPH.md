




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



**CDPARAGRAPH** **-** Starts a new
paragraph.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

} CDPARAGRAPH;  

  




 


**Description :**



This
structure defines the start of a new paragraph within a rich-text field.  Each
paragraph in a rich text field may have different style attributes, such as
indentation and interline spacing. Use this structure when accessing a rich
text field at the level of the CD records.  

  

Note that rich text fields are items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.  

  

Rich text fields consist of a series of CD records. A typical rich text field
may have a series of CD records such as this:  

  

CDPABDEFINITION      

CDPABDEFINITION      

CDPABDEFINITION      

...  

CDPARAGRAPH        

CDPABREFERENCE  

CDTEXT  

text   

CDTEXT      

text  

CDTEXT      

text  

...  

CDPARAGRAPH        

CDPABREFERENCE  

CDTEXT  

text   

CDTEXT      

text  

...  

  




 **Sample Usage :**


    /\* Put a paragraph
header in the field. \*/  

      

    para.Header.Signature = SIG\_CD\_PARAGRAPH;  

    para.Header.Length = (BYTE) ODSLength( \_CDPARAGRAPH );  

  

    ODSWriteMemory( &buff\_ptr, \_CDPARAGRAPH, &para, 1 );  

    


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[CDPABREFERENCE](CDPABREFERENCE.md)**


**[CDTEXT](CDTEXT.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





