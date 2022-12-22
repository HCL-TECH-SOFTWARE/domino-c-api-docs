




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




**Initial Release 4.6**



**Data Type : Composite Data; Rich
Text**



**CDANCHOR** **-** Target for
anchor hotlink.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;     /\* Header info \*/  

   WORD  Datalength;      /\* Length of anchor text string \*/  

   DWORD Reserved; /\* Must be 0 \*/  

/\* Actual anchor text follows. \*/  

} CDANCHOR;


 


**Description :**



An anchor
hotlink points to a specific location in a rich text field of a document.  That
target location is identified by a CDANCHOR record containing a specified text
string.  When the anchor hotlink is selected by a user, Notes displays the
anchor location in the target document.  The fields in this record are:


 


Header             Identifies
this record as a CDANCHOR record.


Datalength        Number
of bytes in the anchor text string.


Reserved          Must
be set to 0.


 


This record
is followed by the anchor text string.


 **See Also :**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





