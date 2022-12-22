




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



**Data Type : Composite Data; Rich
Text**



**CDBOXSIZE** **-** Defines size
information for a layer box. 


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      BSIG Header;  

      LENGTH\_VALUE Width;  

      LENGTH\_VALUE Height;  

      LENGTH\_VALUE Reserved[4];  /\* reserved for future use \*/  

      DWORD dwReserved[4];           /\* reserved for future use \*/  

      } CDBOXSIZE;


 


**Description :**



This CD
record contains size information for a layer box. The units (pixels, twips,
etc.) for the Width and Height are set in the "Units" members of the
"Top", "Left", "Bottom" and "Right"
members of the CDPOSITIONING structure. The fields in this record are:


 


Header             Signature
and Length of this CD record.


Width               The
width of the box. 


Height              The
height of the box. 


Reserved          Reserved
for future use. 


dwReserved     Reserved
for future use.


 **See Also :**


**[CDLAYER](CDLAYER.md)**


**[CDPOSITIONING](CDPOSITIONING.md)**



----------------------------------------------------------------------------------------------------------


 





