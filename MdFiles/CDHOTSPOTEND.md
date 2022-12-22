




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




 


**Data Type : Rich Text; Composite
Data**



**CDHOTSPOTEND** **-** Specifies
the end of a hotspot


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct  

    {  

    BSIG Header;   /\* Signature and length of this record \*/      

    } CDHOTSPOTEND;  

  




 


**Description :**



This
structure specifies the end of a hot region in a rich text field. There are
special cases for Release 4.x and Release 5.x hotspot records which have either
Lotus Script or Release 4.x (or 5.x) actions associated with them.  These
hotspots contain a CDHOTSPOTBEGIN record with the signature
SIG\_CD\_V4HOTSPOTBEGIN (or SIG\_CD\_V5HOTSPOTBEGIN), and a CDHOTSPOTEND record
with the signature SIG\_CD\_V4HOTSPOTEND (or SIG\_CD\_V5HOTSPOTEND).


  

Note that rich text fields are items of type TYPE\_COMPOSITE. Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





