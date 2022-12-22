




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Import/Export**



**IMPKG\_xxx** **-** Offsets
within PKG\_IMPORT for imports.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**


 **Symbolic Values :**      IMPKG\_IFL   -  Offset for CGM image import facility.  

  

      IMPKG\_IPCX            -  Offset for PCX image import facility.  

  

      IMPKG\_IPIC             -  Offset for Lotus PIC import facility.  

  

      IMPKG\_IRTF            -  Offset for RTF import facility.  

  

      IMPKG\_ISTF            -  Offset for STF import facility.  

  

      IMPKG\_ISTR            -  Offset for Structured Text import facility  

  

      IMPKG\_ITAB            -  Offset for Tabular Text export facility.  

  

      IMPKG\_ITARGA       -  Offset for TARGA import facility.  

  

      IMPKG\_ITEXT          -  Offset for Text import facility.  

  

      IMPKG\_ITIFF           -  Offset for TIFF Image import facility.  

  

      IMPKG\_IW4W          -  Offset for Word for Windows import facility.  

  

      IMPKG\_IWKSE         -  Offset for Lotus 1-2-3 import facility, view level
import.  

  

      IMPKG\_IWKSV         -  Offset for Lotus 1-2-3 import facility, edit level
import.  

  

      IMPKG\_IWMF          -  Offset for WMF import facility.  

  

      IMPKG\_IBMP           -  Offset for BMP import facility.  

  

      IMPKG\_IGIF             -  Offset for GIF image import facility.  

  

      IMPKG\_ISTRNGS    -  Offset for Binary with Text import facility.  

  

      IMPKG\_IJPEG          -  Offset for JPEG image import facility.  

  

      IMPKG\_ALL              -  Offset for 20 common strings shared by all
Notes import/export modules  

  




**Description :**



On the Mac,
since all ixports are compiled into Notes, their strings must have unique IDs,
we avoid using a separate PKG for each by defining the offset of each ixport's
first string.  Under Windows and PM, since each ixport is a separate DLL with
separate DS space, all offsets are set to 0.  

  

NOTE:  W4W and WMF are not to be ported to the Mac, therefore no offsets are
provided for them.


 **See Also :**


**[EXPKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/93F9DB3D742BE6C48525623F005687E9)**



----------------------------------------------------------------------------------------------------------


 





