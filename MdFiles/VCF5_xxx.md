




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




**Initial Release 6.5**



**Symbolic Value : Constants; Views**



**VCF5\_xxx** **-** VIEW\_COLUMN\_FORMAT5
- dwFlags


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VCF5\_S\_IS\_NAME   -  (Shift) Column contains a name.  

  

      VCF5\_M\_IS\_NAME   -  (Mask) Column contains a name.  

  

      VCF5\_S\_SHOW\_IM\_STATUS           -  (Shift) Show IM online status in this
column.  

  

      VCF5\_M\_SHOW\_IM\_STATUS          -  (Mask) Show IM online status in this
column.        

  

      VCF5\_S\_VERT\_ORIENT\_TOP         -  (Shift) Vertically show the icon on top
line.  

  

      VCF5\_M\_VERT\_ORIENT\_TOP         -  (Mask) Vertically show the icon on top
line.  

  

      VCF5\_S\_VERT\_ORIENT\_MID          -  (Shift) Vertically middle of the line
entry.  

  

      VCF5\_M\_VERT\_ORIENT\_MID          -  (Mask) Vertically middle of the line
entry.  

  

      VCF5\_S\_VERT\_ORIENT\_BOTTOM   -  (Shift) Show icon on the last line.  

  

      VCF5\_M\_VERT\_ORIENT\_BOTTOM             -  (Mask) Show icon on the last
line.  

  




**Description :**



The dwFlags
field of the VIEW\_COLUMN\_FORMAT5 structure is a DWORD bit field of view
attributes.  The Shift flags specify the first bit position for a specific
attribute.  The Mask flags specify the bit mask (which bits are used) for a
specific attribute.


 **See Also :**


**[VIEW\_COLUMN\_FORMAT5](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3887B983CA0E056185256D5600674531)**



----------------------------------------------------------------------------------------------------------


 





