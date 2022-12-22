




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



**Function : Extension Manager**



**VARARG\_ADDR** **-  Pass
elements of a variable argument list by reference.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



<type> **VARARG\_ADDR(**  

      VARARG\_PTR  aap**);**



**Description :**



This
function is used to pass elements of a variable argument list of an API
function in a Extension Manager callback by reference.  This function is
implemented as a macro.


 


Platforms
that strictly comply to the C standard do not allow passing of variable
argument lists by reference using '&' and '\*' operators because the
standard states that you may get undetermined results.  However, you are
allowed to pass a variable argument list without these operators.  On Linux for
zSeries, whenever you pass a variable argument list the contents will always be
modified upon returning from the function passing it in as a parameter
(assuming some function below accesses the list.)  For these types of
platforms, the following macros are defined to just pass the list without using
the '&' operator.  All platforms can still use a variable argument list as
a pointer by simply using the VARARG\_PTR\_P type.


 


#if
defined(ZLINUX)


typedef
VARARG\_PTR VARARG\_PTR\_P;


#define
VARARG\_ADDR(\_AAP) \_AAP


#define
VARARG\_DEREF(\_AAP) \_AAP


#define
VARARG\_COPY \_\_va\_copy


#else


typedef
VARARG\_PTR \* VARARG\_PTR\_P;


#define
VARARG\_ADDR(\_AAP) &\_AAP


#define
VARARG\_DEREF(\_AAP) \*\_AAP


#define
VARARG\_COPY(dest, src) (dest)=(src)


#endif


 


 


**Parameters :**



Input :  

aap  -   Pointer into a variable argument list.  

  




Output :  

(routine)  -  The type of element passed by reference.   

  

  

aap  -  The address of the variable argument list element.  

  




 **See Also :**


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[VARARG\_COPY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8D61EB9D291ABF985256D560061D268)**


**[VARARG\_DEREF](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FDF95241DE331DF385256D560061B22F)**


**[VARARG\_GET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9DF5C6F757C150F852562420065DF69)**


**[VARARG\_PEEK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7585446D5184259C852562420066445B)**


**[VARARG\_PTR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8B0E9C0C9F111F58525624200614B5E)**


**[VARARG\_PTR\_P](VARARG_PTR_P.md)**


**[VARARG\_START](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/48BF4EE617BE557C85256242005E8461)**



----------------------------------------------------------------------------------------------------------


 





