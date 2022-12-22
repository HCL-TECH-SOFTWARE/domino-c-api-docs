




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




**Initial Release 5.0.1**



**Data Type : Edit Fax**



**EPBCONTEXT** **-** Data
structure used by the EditorPrintNoteToBitmap Editfax API.


**----------------------------------------------------------------------------------------------------------**



**#include
<editfax.h>**



**Definition :**



typedef struct {


   EPBPROC 
Proc;         /\* Callback procedure \*/


   HPAINT  
hPaint;       /\* hPS that the bitmap can be selected


                            
into \*/


   HBITMAP 
hBitmap;      /\* Bitmap to paint into \*/


   RECTSIZE
BitmapSize;   /\* Size of the bitmap \*/


   RECT    
PaintRect;    /\* Rectangle within the bitmap into which


                            
to paint \*/


   WORD    
cxPaperTwips; /\* Width of the paper, in TWIPS \*/


   WORD    
cyPaperTwips; /\* Height of the paper, in TWIPS \*/


} EPBCONTEXT;


 


**Description :**



This data
structure contains the name of the callback routine, and other information
which are passed to the callback routine by the EditorPrintNoteToBitmap Editfax
API.


 


 **Sample Usage :**


    


EPBCONTEXT
EPBContext;


.


.


.


 


error =
EditorPrintNoteToBitmap(hSourceDB,


                               
SourceNoteID,


                               
&EPBContext);


 


 **See Also :**


**[EditorPrintNoteToBitmap](EditorPrintNoteToBitmap.md)**


**[HPAINT](HPAINT.md)**


**[RECTSIZE](RECTSIZE.md)**



----------------------------------------------------------------------------------------------------------


 





