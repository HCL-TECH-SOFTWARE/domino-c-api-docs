




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




 


**Data Type : Mixed 32/16-bit Model**



**NOTESBOOL** **-** \* OBSOLETE \*
Mixed 32/16-bit Boolean parameter


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#define NOTESBOOL BOOL


 


**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


The
"value" of a logical expression in the C language is defined to be an
integer value where 0 indicates false and a non-zero value indicates true.  The
size of an integer varies between platforms, which implies that the size of a
Boolean argument to a function will also vary.  To ensure that the size of
Boolean arguments passed to Notes API functions are the correct size, the
parameters are declared in the API header files with the type
"NOTESBOOL".  In the mixed 32/16-bit model, this type is defined to
be an "unsigned short" value (16 bits long).  On all other platforms,
this type is defined to be an "unsigned int" (16 or 32 bits,
depending on the target platform).


 




----------------------------------------------------------------------------------------------------------


 





