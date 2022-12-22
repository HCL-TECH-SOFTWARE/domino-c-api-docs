




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




**Initial Release 4.0**



**Data Type : Standard**



**LNCALLBACKPTR** **-** Pointer to a
callback routine.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#if !defined(OS2)


 


   #define
LNCALLBACKPTR LNCALLBACK FAR \*


 


#else


 


   /\* OS/2 requires a
separate macro because the ordering of function


      modifiers for
function pointers is different.  This prevents us


      from inserting
\_System in a uniform place (e.g. a replacement


      for PASCAL). \*/


 


   #define
LNCALLBACKPTR \* \_System


 


#endif


 


**Description :**



Pointer to a
callback routine.


 **Sample Usage :**


Callback pointer
declaration from nsfsearc.h:  

  

typedef STATUS (LNCALLBACKPTR NSFSEARCHPROC) (  

   void          far \* EnumRoutineParameter,  

   SEARCH\_MATCH  far \* SearchMatch,  

   ITEM\_TABLE    far \* SummaryBuffer);


 **See Also :**


**[LNCALLBACK](LNCALLBACK.md)**


**[LNCALLBACKPTR](LNCALLBACKPTR.md)**


**[NOTESCALLBACK](NOTESCALLBACK.md)**


**[NOTESCALLBACKPTR](NOTESCALLBACKPTR.md)**



----------------------------------------------------------------------------------------------------------


 





