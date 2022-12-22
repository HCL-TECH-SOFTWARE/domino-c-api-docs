




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




 


**Symbolic Value : DDE**



**DDEFORMAT\_xxx** **-** DDE
clipboard format.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      DDEFORMAT\_TEXT            -  CF\_TEXT  

  

      DDEFORMAT\_METAFILE     -  CF\_METAFILE or CF\_METAFILEPICT  

  

      DDEFORMAT\_BITMAP        -  CF\_BITMAP  

  

      DDEFORMAT\_RTF   -  Rich Text Format  

  

      DDEFORMAT\_OWNERLINK             -  OLE Ownerlink (never saved in CD\_DDE
or CD\_OLE: used at run time).  

  

      DDEFORMAT\_OBJECTLINK            -  OLE Objectlink (never saved in CD\_DDE
or CD\_OLE: used at run time).  

  

      DDEFORMAT\_NATIVE         -  OLE Native (never saved in CD\_DDE or CD\_OLE:
used at run time).  

  

      DDEFORMAT\_ICON             -  Program Icon for embedded object  

  

      DDEFORMAT\_TYPES          -  Total number of DDE format types supported
(Only relevant to persistent, on-disk stored types).  

  




**Description :**



These values
specify the DDE clipboard format with which data should be rendered.  They are
used in the CDDDEBEGIN structure and in the CDOLEBEGIN structure.


 **See Also :**


**[CDDDEBEGIN](CDDDEBEGIN.md)**


**[CDOLEBEGIN](CDOLEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





