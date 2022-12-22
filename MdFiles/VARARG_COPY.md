




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




**Initial Release 6.5**



**Function : Extension Manager**



**VARARG\_COPY** **-  Copy a
variable argument list.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



<type> **VARARG\_COPY(**  

      VARARG\_PTR  dest,  

      <type>  src**);**



**Description :**



This
function is used to copy the variable argument list of an API function in a
Extension Manager callback.  This function is implemented as a macro.


 


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

dest  -  Variable argument list pointer.  

  

src  -  Pointer to the argument list provided to the core function.  The format
of the argument list depends on the actual function.  

  




Output :  

(routine)  -  The type of the return value is specified by the "Type"
argument.  

  

  

dest  -  Variable argument list pointer, now pointing to the source argument
list.  

  




 **Sample Usage :**


        if
(EM\_GETPASSWORD != data->EId)


               
return (ERR\_EM\_CONTINUE);


 


              
/\* Fetch the arguments \*/


            
VARARG\_COPY(pArgs, data->Ap);


 


           
MaxPwdLen = VARARG\_GET (pArgs, DWORD);


            retLength
= VARARG\_GET (pArgs, DWORD far \*);


         
retPassword = VARARG\_GET (pArgs, char far \*);


            
FileName = VARARG\_GET (pArgs, char far \*);


           
OwnerName = VARARG\_GET (pArgs, char far \*);


             
DataLen = VARARG\_GET (pArgs, DWORD);


                
Data = VARARG\_GET (pArgs, BYTE far \*);


 **See Also :**


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[VARARG\_ADDR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BBF28257119202E085256D5600612FC1)**


**[VARARG\_DEREF](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FDF95241DE331DF385256D560061B22F)**


**[VARARG\_GET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9DF5C6F757C150F852562420065DF69)**


**[VARARG\_PEEK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7585446D5184259C852562420066445B)**


**[VARARG\_PTR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8B0E9C0C9F111F58525624200614B5E)**


**[VARARG\_PTR\_P](VARARG_PTR_P.md)**


**[VARARG\_START](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/48BF4EE617BE557C85256242005E8461)**



----------------------------------------------------------------------------------------------------------


 





