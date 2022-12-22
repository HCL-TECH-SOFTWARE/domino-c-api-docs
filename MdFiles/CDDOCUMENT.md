




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




 


**Data Type : Composite Data; Form;
Rich Text**



**CDDOCUMENT** **-** Defines the
attributes of a form.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

   WORD PaperColor;                      /\* Color of the paper being used \*/  

   WORD FormFlags;                /\* Form Flags \*/  

   WORD NotePrivileges;           /\* Privs for notes created when


                                   
using form \*/


/\*


   WARNING!!! Fields
below this comment were not zeroed in builds  

   prior to 100.  A mechanism has been set up to use them however.  

   dload checks the TPL\_FLAG\_SPARESOK bit in the flags word.  If it  

   is not set, all of the storage after this comment is zeroed.  On  

   save, dsave makes sure the unused storage is zero and sets the bit.


\*/


   WORD
FormFlags2;             /\* more Form Flags \*/  

   WORD InherFieldNameLength;   /\* Length of the name, which follows


                                  
this struct \*/


 


   WORD
PaperColorExt;          /\* Palette Color of the paper being


                                  
used. Index into 240 color table.


                                          
New in V4. \*/  

    COLOR\_VALUE PaperColorValue; /\* Paper Color: As of v5.0 stored as


                             
     RGB, other formats possible \*/  

    WORD FormFlags3;


        WORD
Spare[1];


  

/\* ... now the Inherit Field Name string \*/  

/\* ... now the Text Field Name string indicating which field to


       append version
number to \*/  

} CDDOCUMENT;


 


**Description :**



This defines
the structure of the document information field in a form note. A document
information field is an item with name $INFO (ITEM\_NAME\_DOCUMENT) and data type
TYPE\_COMPOSITE. The document information field defines attributes of documents
created with that form.  

  

Header:      Defines this composite data item as a CDDOCUMENT item.  

PaperColor: Background color of document:


                                          0                black


                                          1                white


                                          2                gray


                                          3                lt.
green


                                          4                green


                                          5                lt.
yellow


                                          6                yellow


                                          7                cyan


                                          8                lt.
cyan


                                          9                red


                                          10              green


                                          11              blue


                                          12              magenta


                                          13              yellow


                                          14              cyan


                                          15              dk
read


                                          16              dk
green


                                          17
             dk blue 


                                          18
             dk magenta


                                          19              dk
yellow


                                          20              dk
cyan


                                          21
- 240      palette color table index


 


FormFlags:                         Defines
various attributes.  See TPL\_FLAG\_xxx for details.  

NotePrivileges:                   Privileges for notes created with this form.


FormFlags2:                       Defines
various attributes.  See TPL\_FLAG\_xxx for details.


InherFieldNameLength:  

PaperColorExt:                   PaperColor value overrides PaperColorExt. 


PaperColorValue:                RGB
3 Component Color value (Please see COLOR\_VALUE).


FormFlags3:                       Defines
various attributes.  See TPL\_FLAG\_xxx for details.  

  




Since this
field is of type TYPE\_COMPOSITE, API programs that run on non-Intel
architecture platforms must perform host/canonical conversion when accessing a
CDDOCUMENT structure in a document information field item.


 **See Also :**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[TPL\_FLAG\_xxx](TPL_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





