




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



**CDAREAELEMENT** **-** Structure
defining an HTML AREA element.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD Flags;        /\* reserved for future use \*/  

   WORD  Shape;        /\* one of AREA\_SHAPE\_xxx \*/  

   WORD  TabIndex;  

   WORD  AccessKey;  

   BYTE  Reserved[16];


  

/\* variable length items follow:  

 \* If Shape == rect  

 \*   CDRECT  

 \* else if Shape == circle


 \*   NOTE: points for
the rect the circle is drawn in CDRECT  

 \* else if Shape == polygon  

 \*    WORD  numPts  

 \*    CDPOINT 1  

 \*    CDPOINT 2  

 \*    ...  

 \*    CDPOINT n  

 \* else if Shape == default  

 \*   No points  

 \*/  

} CDAREAELEMENT;


 


**Description :**



An AREA
element defines the shape and coordinates of a region within a client side
image MAP. 


 


Header                   Identifies
the record as a CDAREAELEMENT


Flags                      Reserved
for future use


Shape                     Shape
of area (see AREA\_SHAPE\_xxx)


TabIndex                Tab
selection order


AccessKey             The
accelerator key for the object


Reserved[16]          Reserved


 


This
structure is followed by the description of the shape.  If AREA\_SHAPE\_xxx
equals AREA\_SHAPE\_RECT then we are dealing with a rectangle whose area is
defined in CDRECT.  If AREA\_SHAPE\_xxx equals AREA\_SHAPE\_CIRCLE then we are
dealing with a circle whose area is defined in CDRECT.  If AREA\_SHAPE\_xxx
equals AREA\_SHAPE\_POLYGON then we are dealing with a polygon whose area is
defined with CDBPOINT.


 


 **See Also :**


**[AREA\_SHAPE\_xxx](AREA_SHAPE_xxx.md)**


**[CDAREAELEMENT\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1D58C473E2DDA6B485256678004D4DA2)**


**[CDMAPELEMENT](CDMAPELEMENT.md)**


**[CDPOINT](CDPOINT.md)**


**[CDRECT](CDRECT.md)**



----------------------------------------------------------------------------------------------------------


 





