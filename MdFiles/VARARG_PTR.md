




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



**Data Type : Extension Manager**



**VARARG\_PTR** **-** Pointer to a
variable argument list.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



#if defined(OSF) ||
(defined(NT) && defined(\_ALPHA\_))  

#include <stdarg.h>  

#define VARARG\_PTR   va\_list  

#elif defined(OS400)  

#include <stdarg.h>  

typedef struct {  

   char \* vaold;  

   char \* vanew;  

} VARARG\_PTR;  

#else  

typedef char \* VARARG\_PTR;  

#endif


 


**Description :**



The VARARG
macros support access to variable argument lists.  These argument lists appear
in the C API in two places, functions with "cdecl" argument lists and
in the Extension Manager facility.


 


VARARG\_PTR
is a type definition for a pointer into a variable argument list.  This pointer
is initialized by the VARARG\_START() macro.  The pointer is then used in the
VARARG\_GET(), and VARARG\_PEEK() macros to access elements of the argument list.


 **Sample Usage :**


void far cdecl
SampleRoutine (


    char \*String,


    WORD
LastNamedArgument, ...)  

{  

  DWORD temp1;  

  WORD  temp2;  

  VARARG\_PTR ap;


  

  VARARG\_START(ap,LastNamedArgument);


        /\* Start out
just past last named argument \*/  

  temp1 = VARARG\_GET(ap,DWORD);


        /\* Get next
DWORD into temp1 and advance \*/  

  temp2 = VARARG\_PEEK(ap,WORD);


        /\* Peek at next
WORD, but no advance \*/  

  temp2 = VARARG\_GET(ap,WORD);


        /\* Get next
WORD into temp2 and advance \*/  

}


 **See Also :**


**[VARARG\_GET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9DF5C6F757C150F852562420065DF69)**


**[VARARG\_PEEK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7585446D5184259C852562420066445B)**


**[VARARG\_START](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/48BF4EE617BE557C85256242005E8461)**



----------------------------------------------------------------------------------------------------------


 





