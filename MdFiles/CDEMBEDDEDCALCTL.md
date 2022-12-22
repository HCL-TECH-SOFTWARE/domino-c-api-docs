




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




**Initial Release 6**



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDCALCTL** **-** Defines
properties of an embedded calendar control (date picker).


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    WSIG           Header;                /\* Signature and length of this
record. \*/  

    DWORD          Flags;  

    COLOR\_VALUE    HeaderBkgnd;  

    COLOR\_VALUE    SelectionColor;  

    WORD           TargetFrameLength;  

    DWORD          Spare[10];                    /\* Reserved for future use -
must be zero \*/         


} CDEMBEDDEDCALCTL;


 


 


**Description :**



This CD
record defines properties of an embedded calendar control (date picker).   It
is preceded by CDHOTSPOTBEGIN and CDPLACEHOLDER and is followed by a
CDHOTSPOTEND of type HOTSPOTREC\_TYPE\_EMBEDDEDCALENDARCTL. The fields in this
structure are:


  

Header - Signature and length of this record.


Flags - See
EMBEDDEDCAL\_FLAG\_xxx 


HeaderBkgnd
- Header background color. Set Flags member to
EMBEDDEDCAL\_FLAG\_NON\_TRANSPARENT\_BKGND.


SelectionColor
- Control background color. Set Flags member to
EMBEDDEDCAL\_FLAG\_NON\_TRANSPARENT\_BKGND.


TargetFrameLength
- Target frame length. Set Flags member to EMBEDDEDCAL\_FLAG\_HASTARGETFRAME.  

Spare - Reserved for future use - must be zero.


 


These fields
may be followed by an optional target frame. If you plan to use it, you will
need to declare the variable and assign a value to its length.


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 **See Also :**


**[EMBEDDEDCAL\_FLAG\_xxx](EMBEDDEDCAL_FLAG_xxx.md)**


**[SIG\_CD\_xxx](SIG_CD_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





