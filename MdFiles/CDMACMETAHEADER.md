




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



**CDMACMETAHEADER** **-** Start of a
Macintosh Metafile Record


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG    Header;        /\* Signature and Length \*/  

   RECTSIZE OriginalDisplaySize; /\* Original disp. size, in twips \*/  

   DWORD   MetafileSize;  /\* Total size of metafile, in bytes \*/  

   WORD    SegCount;              /\* Number of CDMACMETASEG records \*/  

    /\*      Metafile segments Follow \*/  

} CDMACMETAHEADER;


 


**Description :**



Identifies a
Macintosh metafile embedded in a rich text field.  This record must be preceded
by a CDGRAPHIC record.  Since metafiles can be large, but Domino and Notes has
an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be
divided into segments of up to 64kB;  each segment must be preceded by a
CDMACMETASEG record.  

  

        Header                          Tag identifying this as a
CDMACMETAHEADER record  

        OriginalDisplaySize  Original display size of metafile, measured in
"twips" (1/1440 inch)  

        MetafileSize                 Total size of metafile data in bytes  

        SegCount                     Number of CDMACMETASEG records  

  

This header is followed by the segments of metafile data.


 **See Also :**


**[CDGRAPHIC](CDGRAPHIC.md)**


**[CDMACMETASEG](CDMACMETASEG.md)**



----------------------------------------------------------------------------------------------------------


 





