




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




 


**Data Type : Views**



**FORMNAME\_ARRAY** **-** Structure of
the data block of form names.


**----------------------------------------------------------------------------------------------------------**



**#include
<ixview.h>**



**Definition :**



typedef struct {  

   /\* The following array is intended to be the maximum name length  

      for a form.  This used to use DESIGN\_NAME\_MAX (from names.h)  

      but the  value of DESIGN\_LEVEL\_MAX (which DESIGN\_NAME\_MAX is derived  

      from) was doubled from V3.0 to V3.0J to allow for longer Japanese  

      design names.  The hardcoded value below is based on the V3.0 value  

      and will allow API programs to be backward and forward compatible.  

   \*/  

   char Name[66];  

} FORMNAME\_ARRAY;


 


**Description :**



VIEWIXDATA,
the data structure passed from Notes to view import/export modules, contains a
handle to an array of form names (hFormNames).  The handle specifies an array
of FORMNAME\_ARRAY structures.


 **See Also :**


**[VIEWIXDATA](VIEWIXDATA.md)**



----------------------------------------------------------------------------------------------------------


 





