




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



**NOTESCALLBACKPTR** **-** \* OBSOLETE \*
Pointers to callback functions


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#define
NOTESCALLBACKPTR LNCALLBACKPTR


 


**Description :**



\*\*\*OBSOLETE
- Included for backward compatibility only\*\*\*


 


Different
compilers supported when using the mixed 32/16-bit model require the use of
different syntax to declare pointers to callback functions.  This macro
isolates these syntax differences.  Normally, this macro is only used in the
Notes API header files, and is not needed in application programs.  However, if
an application program will be manipulating pointers to callback functions,
this macro will simplify the pointer declarations.


 **Sample Usage :**


Callback pointer
declaration from nsfsearc.h:  

  

    typedef STATUS (NOTESCALLBACKPTR NSFSEARCHPROC) (  

        void          NOTESPTR EnumRoutineParameter,  

        SEARCH\_MATCH  NOTESPTR SearchMatch,  

        ITEM\_TABLE    NOTESPTR SummaryBuffer);


 **See Also :**


**[LNCALLBACK](LNCALLBACK.md)**


**[LNCALLBACKPTR](LNCALLBACKPTR.md)**


**[NOTESCALLBACK](NOTESCALLBACK.md)**



----------------------------------------------------------------------------------------------------------


 





