




<!--
 /\* Font Definitions \*/
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




**Initial Release 5.0.1**



**Data Type : Composite Data; Rich
Text**



**CDFRAMESET** **-** Used to
specify an HTML FRAMESET element


**----------------------------------------------------------------------------------------------------------**



**#include
<fsods.h>**



**Definition :**



typedef
struct


            {


            WSIG
Header;


            DWORD
Flags;                                                 /\* fFSxxxxxxx as defined
below. Unused bits must be set to 0 \*/


#define
fFSBorderEnable                                   0x00000001      /\* Set if
BorderEnable is specified \*/


#define
fFSFrameBorderDims               0x00000004      /\* Set if FrameBorderWidth is
specified \*/


#define
fFSFrameSpacingDims             0x00000008      /\* Set if FrameSpacingWidth is
specified \*/


#define
fFSFrameBorderColor               0x00000040      /\* Set if FrameBorderColor is
specified \*/


            BYTE 
BorderEnable;                                       /\* Specifies the HTML
FRAMEBORDER attribute for this frameset element \*/


            BYTE 
byAvail1;                                                          /\* Reserved
for future use, must be 0 \*/


            WORD
Reserved1;                                                       /\* Reserved
for future use, must be 0 \*/


            WORD
Reserved2;                                                       /\* Reserved
for future use, must be 0 \*/


            WORD
FrameBorderWidth;                               /\* Specifies the HTML BORDER
attribute for this frameset element \*/


            WORD
Reserved3;                                                       /\* Reserved
for future use, must be 0 \*/


            WORD
FrameSpacingWidth;                             /\* Specifies the HTML
FRAMESPACING attribute for this frameset element \*/


            WORD
Reserved4;                                                       /\* Reserved
for future use, must be 0 \*/


            COLOR\_VALUE
ReservedColor1;                     /\* Reserved for future use, must be 0 \*/


            COLOR\_VALUE
ReservedColor2;                     /\* Reserved for future use, must be 0 \*/


/\*
RowQty and ColQty specify the number of FRAMESETLENGTH structures that follow


 \*
in the variable length data area.  Only one of these values can be non-zero,


 \*
meaning that a frameset will consist of all rows or all columns but never both.
\*/


            WORD 
RowQty; 


            WORD 
ColQty;


            WORD 
Reserved5;                                         /\* Reserved for future use,
must be 0 \*/


            WORD 
Reserved6;                                         /\* Reserved for future use,
must be 0 \*/


            COLOR\_VALUE
FrameBorderColor;      /\* Used to specify the BORDERCOLOR attribute for this
frameset element \*/


            BYTE 
ThemeSetting;                                      /\* Theme Setting \*/


            BYTE 
Reserved7;                                          /\* Reserved for future use,
must be 0 \*/


            /\*
Variable length data follows (strings not null terminated)


             \*         -
Row FRAMESETLENGTH structures (count equals RowQty)


             \*         -
Col FRAMESETLENGTH structures (count equals ColQty) \*/


            }           CDFRAMESET;


 


 


**Description :**



Header


Flags                                  see
fFSxxx


BorderEnable                      HTML
FRAMEBORDER attribute


byAvail1                             reserved,
must be 0


Reserved1                          reserved,
must be 0


FrameBorderWidth              HTML
BORDER attribute


Reserved3                          reserved,
must be 0


FrameSpacingWidth            HTML
FRAMESPACING attribute


Reserved4                          reserved,
must be 0


ReservedColor1                  reserved
for future use


ReservedColor2                  reserved
for future use


RowQty                              The
number of FRAMESETLENGTH structures defining row information.


ColQty                                The
number of FRAMESETLENGTH structures defining column information.


Reserved5                          reserved,
must be 0


Reserved6                          reserved,
must be 0


FrameBorderColor              HTML
BORDERCOLOR attribute, see COLOR\_VALUE


Reserved7[2]                      reserved,
must be 0


 


A
FRAMESETLENGTH structure will follow depending on the value found in either
RowQty or ColQty.  There could be multiple FRAMESETLENGTH structures defining
the RowQty and ColQty values.


 **See Also :**


**[CDFRAME](CDFRAME.md)**


**[CDFRAMESETHEADER](CDFRAMESETHEADER.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[fFSxxx](fFSxxx.md)**


**[FRAMESETLENGTH](FRAMESETLENGTH.md)**



----------------------------------------------------------------------------------------------------------


 





