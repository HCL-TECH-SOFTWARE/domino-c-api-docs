




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




**Initial Release 6**



**Symbolic Value : Composite Data;
Constants; Rich Text**



**INLINE\_FLAG\_xxx** **-** Values for
the dwFlags member of CDINLINE. 


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      INLINE\_FLAG\_UNKNOWN   -  If flag is set, resource is of
unknown type.  

  

      INLINE\_FLAG\_SCRIPT\_LIB              -  If flag is set, resource is a
JavaScript library.  

  

      INLINE\_FLAG\_STYLE\_SHEET         -  If flag is set, resource is a style
sheet.  

  

      INLINE\_FLAG\_HTML            -  If flag is set, resource is HTML  

  

      INLINE\_FLAG\_HTMLFILERES          -  If flag is set, resource is an HTML
file.  

  

      INLINE\_FLAG\_TYPES\_MASK           -  Mask for the INLINE flags.  

  




**Description :**



These flags
are values for the dwFlags member of CDINLINE.  A CDINLINE record may be
preceded by a CDBEGINRECORD and followed by a CDRESOURCE and then a
CDENDRECORD.  


 **See Also :**


**[CDINLINE](CDINLINE.md)**


**[CDRESOURCE](CDRESOURCE.md)**



----------------------------------------------------------------------------------------------------------


 





