




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



**CDTARGET** **-** Defines a
TARGET area for a resource link hotspot.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   WORD  TargetLength;  

   WORD  Flags;  

   DWORD Reserved;  

    } CDTARGET;


 


**Description :**



WSIG         Header             Signature
and length of record


WORD       TargetLength    length
of the data following this record 


WORD       Flags                see
FLAG\_TARGET\_xxx


DWORD     Reserved


 


The name of
the target frame follows.


 


The CDTARGET
structure specifies the target (ie:  the frame) where a resource link hotspot
is to be displayed.


It is
followed by variable length data whose length is specified in the TargetLength
member.  This variable length data specifies the target frame.  The format of
the variable length data is specified by the Flags member of the CDTARGET
structure.  If no flags are specified, then the data following the CDTARGET
record is a character string containing the name of the target frame.


 **See Also :**


**[FLAG\_TARGET\_xxx](FLAG_TARGET_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





