




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



**EXPKG\_xxx** **-** Offsets
within PKG\_EXPORT for exports.


**----------------------------------------------------------------------------------------------------------**



**#include <globerr.h>**


 **Symbolic Values :**      EXPKG\_XCGM         -  Offset for CGM image export facility.  

  

      EXPKG\_XRTF          -  Offset for RTF export facility.  

  

      EXPKG\_XSTF          -  Offset for STF export facility.  

  

      EXPKG\_XSTR          -  Offset for Structured Text export facility  

  

      EXPKG\_XTAB          -  Offset for Tabular Text export facility.  

  

      EXPKG\_XTEXT        -  Offset for Text export facility.  

  

      EXPKG\_XTIFF         -  Offset for TIFF Image export facility.  

  

      EXPKG\_XW4W        -  Offset for Word for Windows export facility.  

  

      EXPKG\_XWKS         -  Offset for Lotus 1-2-3 export facility.  

  

      EXPKG\_ALL             -  Offset for 20 common strings shared by all Notes
import/export modules  

  




**Description :**



On the Mac,
since all ixports are compiled into Notes, their strings must have unique IDs,
we avoid using a separate PKG for each by defining the offset of each ixport's
first string.  Under Windows and PM, since each ixport is a separate DLL with
separate DS space, all offsets are set to 0.  

  

NOTE:  TARGA, and WMF are not to be ported to the Mac, therefore no offsets are
provided for them.


 **See Also :**


**[IMPKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/4644749EF57C69508525623F00596658)**



----------------------------------------------------------------------------------------------------------


 





