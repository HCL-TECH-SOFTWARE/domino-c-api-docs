




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



**NOTESPTR** **-** \* OBSOLETE \*
Mixed 32/16-bit pointer declaration


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#define NOTESPTR FAR \*


 


**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


This macro
isolates the different syntax for pointer declarations required by different
compilers when using the mixed 32/16-bit model to build 32-bit applications for
OS/2 2.1.


 **Sample Usage :**


#include
<global.h>  

  

    /\* Subroutine to increment a long integer \*/  

NOTESPTR IncrementLong (long NOTESPTR longPtr)  

{  

    (\*longPtr)++;  

    return (longPtr);  

}  

  

int main (void)  

{  

    long    myValue = 0;  

    long    \*flatPointer = &myValue;  /\* 32-bit pointer to data \*/  

  

        /\* Illustrate the pedantically correct typecasts \*/  

    flatPointer = (long \*) IncrementLong ((long NOTESPTR) (&myValue));  

  

    return ((int) \*flatPointer);  

}


 




----------------------------------------------------------------------------------------------------------


 





