




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



**CDPMMETASEG** **-** Segment of
Presentation Manager GPI Metafile Data


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG    Header; /\* Signature and Length \*/  

   WORD    DataSize;      /\* Actual Size of metafile, in bytes  

                                  (ignoring any filler) \*/  

   WORD    SegSize;       /\* Size of segment, in bytes \*/  

    /\* PM Metafile Bits for this segment. Each segment  

           must be <= 64K bytes. \*/  

} CDPMMETASEG;


 


**Description :**



A portion of
a Presentation Manager GPI metafile.  This record must be preceded by a
CDPMMETAHEADER record.  Since metafiles can be large, but Domino and Notes have
an internal limit of 65,536 bytes (64kB) for a segment, a metafile may be
divided into segments of up to 64kB;  each segment must be preceded by a CDPMMETASEG
record.  

  

        Header           Tag identifying this as a CDPMMETASEG record  

        DataSize        Actual size of metafile, in bytes  

        SegSize         Size of segment  

  

The segment size may actually be larger than the size of the metafile;  if the
metafile is an odd number of bytes in length, a byte will be added to align
data on a word boundary.


 **See Also :**


**[CDGRAPHIC](CDGRAPHIC.md)**


**[CDPMMETAHEADER](CDPMMETAHEADER.md)**



----------------------------------------------------------------------------------------------------------


 





