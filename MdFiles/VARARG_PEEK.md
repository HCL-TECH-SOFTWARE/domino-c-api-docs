




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



**Function : Extension Manager**



**VARARG\_PEEK** **- Peek at
an argument from a variable argument list (no advance).**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



<type> **VARARG\_PEEK(**  

      VARARG\_PTR  ap,  

      <type>  Type**);**



**Description :**



Retrieve a
value from a variable argument list, but do not advance the argument list
pointer.  This function is implemented as a macro.


 


A pointer
into a variable argument list is declared using the macro VARARG\_PTR and
initialized using the VARARG\_START() macro.  Retrieving data from the variable
argument list with VARARG\_GET() will update the argument list pointer to point
to the next argument, while retrieving the value using VARARG\_PEEK() will
obtain the value without updating the argument list pointer.  The argument type
information is used to determine how large the argument value is, and is used
in a typecast to ensure that assignment of the value is correct.


 


**Parameters :**



Input :  

ap  -  Current pointer into the variable argument list.  

  

Type  -  This must be a valid elementary data type.  Some examples of
elementary data types are "int", "WORD", "char",
"DWORD", "char \*", or "BOOL".  

  




Output :  

(routine)  -  The type of the return value is specified by the "Type"
argument.  

  

  




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


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[VARARG\_GET](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C9DF5C6F757C150F852562420065DF69)**


**[VARARG\_PTR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8B0E9C0C9F111F58525624200614B5E)**


**[VARARG\_START](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/48BF4EE617BE557C85256242005E8461)**



----------------------------------------------------------------------------------------------------------


 





