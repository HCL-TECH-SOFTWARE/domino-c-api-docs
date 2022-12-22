




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




 


**Data Type : Rich Text; Composite
Data**



**CDGRAPHIC** **-** Graphic
combination object record


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   LSIG     Header;     /\* Signature and Length \*/  

   RECTSIZE DestSize;   /\* Destination Display size in TWIPS  

                           (1/1440 inch) \*/  

   RECTSIZE CropSize;   /\* Reserved \*/  

   CROPRECT CropOffset; /\* Reserved \*/  

   WORD     fResize;    /\* True if user resized object \*/  

   BYTE     Version;    /\* CDGRAPHIC\_VERSIONxxx \*/  

   BYTE     bFlags;     /\* Ignored before CDGRAPHIC\_VERSION3 \*/


      WORD    
wReserved;  

} CDGRAPHIC;


 


**Description :**



The
CDGRAPHIC record contains information used to control display of graphic
objects in a document.  This record marks the beginning of a composite graphic
object, and must be present for any graphic object to be loaded or displayed.  

  

A composite graphic object may be one or more of the following:  

  

  
CDCGMMETA  

   CDWINMETAHEADER  

   CDWINMETASEG  

   CDPMMETAHEADER  

   CDPMMETASEG  

   CDMACMETAHEADER  

   CDMACMETASEG  

   CDBITMAPHEADER  

   CDBITMAPSEGMENT


   CDCOLORTABLE


  

If more than one graphic object is present, Notes will only display one, using
the following precedence rules:  

  

      1)  If there is a CGM metafile object, display it  

      2)  If there is a native metafile object for this platform, display it  

      3)  If there is a bitmap, display it  

  

The fields in this record are:  

  

  
Header     Tag identifying this as a CDGRAPHIC record  

   DestSize   Destination display area, measured in "twips"


              (1/1440
of an inch) or in pixels.  

   CropSize   Reserved;  set all fields in this structure to 0  

   CropOffset Reserved; set all fields in this structure to 0  

   fResize    If the user resizes the graphic object, this field is


              set to
TRUE  

   Version    Version number of the Domino graphics driver


    bFlags        See
CDGRAPHIC\_FLAG\_xxx.


 **See Also :**


**[CDBITMAPHEADER](CDBITMAPHEADER.md)**


**[CDBITMAPSEGMENT](CDBITMAPSEGMENT.md)**


**[CDCGMMETA](CDCGMMETA.md)**


**[CDGRAPHIC\_FLAG\_xxx](CDGRAPHIC_FLAG_xxx.md)**


**[CDGRAPHIC\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E123A1E654110C13852562030071B820)**


**[CDMACMETAHEADER](CDMACMETAHEADER.md)**


**[CDMACMETASEG](CDMACMETASEG.md)**


**[CDPMMETAHEADER](CDPMMETAHEADER.md)**


**[CDPMMETASEG](CDPMMETASEG.md)**


**[CDWINMETAHEADER](CDWINMETAHEADER.md)**


**[CDWINMETASEG](CDWINMETASEG.md)**


**[CROPRECT](CROPRECT.md)**


**[RECTSIZE](RECTSIZE.md)**



----------------------------------------------------------------------------------------------------------


 





