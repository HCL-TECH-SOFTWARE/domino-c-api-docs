




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




 


**Data Type : Composite Data; Rich
Text**



**CDCGMMETA** **-** Start of a
CGM Metafile Record


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG     Header;       /\* Signature and Length \*/  

   SWORD    mm;           /\* CGM mapping mode (see CGM\_MAPMODE\_xxx) \*/  

   SWORD    xExt,yExt;    /\* Extents, in world coordinates \*/  

   RECTSIZE OriginalSize; /\* Original display size, in twips \*/  

   /\* CGM Metafile bits follow (must be <= 64K bytes total) \*/  

} CDCGMMETA;


 


**Description :**



Identifies a
CGM metafile embedded in a rich text field.  This record must be preceded by a
CDGRAPHIC record.  A CDCGMMETA record may contain all or part of a CGM
metafile, and is limited to 65,536 bytes (64K).  

  

        Header                      Tag identifying this as a CDCGMMETA record  

        mm                              CGM mapping mode - currently must be
CGM\_MAPMODE\_ABSTRACT  

        xExt                             Width of drawing in world coordinates  

        yExt                             Height of drawing in world coordinates  

        OriginalSize             Original display size of metafile, measured in
"twips" (1/1440 inch)  

  

This header is followed by up to 64K of metafile data.


 **See Also :**


**[CDGRAPHIC](CDGRAPHIC.md)**


**[CGM\_MAPMODE\_xxx](CGM_MAPMODE_xxx.md)**


**[RECTSIZE](RECTSIZE.md)**



----------------------------------------------------------------------------------------------------------


 





