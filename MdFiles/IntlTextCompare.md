




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




**Initial Release 4.0**



**Function : International Character
Manipulation**



**IntlTextCompare** **- Compare
strings using international collation rules.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



int
LNPUBLIC **IntlTextCompare(**  

      const void far \*Str1,  

      WORD  Str1Len,  

      const void far \*Str2,  

      WORD  Str2Len,  

      DWORD  Flags**);**



**Description :**



The two
strings are compared using the international collation rules in the current
system collation table.  Collation options may be specified to for comparing
characters;  the options that may be specified are described in the entry
INTL\_xxx\_SENSITIVE.


 


**Parameters :**



Input :  

Str1  -  Pointer to first string to compare.  

  

Str1Len  -  Length of the first string, in bytes.  

  

Str2  -  Pointer to the second string to compare.  

  

Str2Len  -  Length of the second string, in bytes.  

  

Flags  -  Collation options.  The options that may be specified are described
in the entry INTL\_xxx\_SENSITIVE.  

  




Output :  

(routine)  -  0 if the strings are equal  

1 if Str1 follows Str2 in sorted order  

-1 if Str1 precedes Str2 in sorted order  

  

  




 **See Also :**


**[INTL\_xxx\_SENSITIVE](INTL_xxx_SENSITIVE.md)**



----------------------------------------------------------------------------------------------------------


 





