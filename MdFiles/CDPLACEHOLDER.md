




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDPLACEHOLDER** **-** Additional
information for an embedded element.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct


        {


        WSIG
          Header; /\* Signature and length of this record. \*/


        WORD           Type;


        DWORD
  Flags;  


        WORD
          Width;


        WORD
          Height;


        FONTID 
       FontID;


        WORD           Characters;


        WORD           SpaceBetween;


        WORD           TextAlignment;


        WORD           SpaceWord;


        FONTID  SubFontID[2];


        WORD
          DataLength;


        COLOR\_VALUE
BackgroundColor;


        COLOR\_VALUE
ColorRGB;


        WORD           SpareWord;


        DWORD          Spare[3];


        }
CDPLACEHOLDER;


 


**Description :**



A
CDPLACEHOLDER record stores additional information about various embedded type
CD records, such as CDEMBEDDEDCTL, CDEMBEDDEDOUTLINE and other embedded CD
record types defined in HOTSPOTREC\_TYPE\_xxx.


 


WSIG                           Header                         Signature
and length


WORD                         Type                            see
HOTSPOTREC\_TYPE\_xxx (Note: only the HOTSPOTREC\_TYPE\_EMBEDDEDxxx)


DWORD                       Flags                            see
PLACEHOLDER\_FLAG\_xxx


WORD                         Width                           Width
of embedded element


WORD                         Height                          Height
of embedded element


FONTID                       FontID                          Font
information of embedded element


WORD                         Characters


WORD                         SpaceBetween              Space
between


WORD                         TextAlignment              see
PLACEHOLDER\_ALIGN\_xxx


WORD                         SpaceWord


FONTID                       SubFontID[2]                Sub
Font information of embedded element


WORD                         DataLength                   Data
Length


COLOR\_VALUE            BackgroundColor          Background
Color


COLOR\_VALUE            ColorRGB                     Color    


WORD                         SpareWord


DWORD                       Spare[3]


 


 


 **See Also :**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[FONTID](FONTID.md)**


**[HOTSPOTREC\_TYPE\_xxx](HOTSPOTREC_TYPE_xxx.md)**


**[PLACEHOLDER\_ALIGN\_xxx](PLACEHOLDER_ALIGN_xxx.md)**


**[PLACEHOLDER\_FLAG\_xxx](PLACEHOLDER_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





