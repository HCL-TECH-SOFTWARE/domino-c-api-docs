




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



**VARARG\_GET** **- Retrieve
an argument from a variable argument list.**


**----------------------------------------------------------------------------------------------------------**



**#include <global.h>**



<type> **VARARG\_GET(**  

      VARARG\_PTR  ap,  

      <type>  Type**);**



**Description :**



This
function is used to access the elements of a variable argument list to a
function or to access the arguments of an API function in a Extension Manager
callback.  This function is implemented as a macro.


 


A pointer
into a variable argument list is declared using the macro VARARG\_PTR and
initialized using the VARARG\_START() macro.  This pointer is used in the
VARARG\_GET() macro to obtain an argument value, and the VARARG\_PTR is updated
to point to the next argument value.  The argument type information is used to
determine how large the argument value is, and is used in a typecast to ensure
that assignment of the value is correct.


 


This macro
can be used, for example, to retrieve the arguments passed to the callback
procedure in the Extension Manager.  The Ap field in the EMRECORD structure
contains a VARARG\_PTR to the parameters passed to the core function.  By using
multiple calls to VARARG\_GET each of the function arguments can be retrieved.


 


**Parameters :**



Input :  

ap  -  Current pointer into the variable argument list.  

  

Type  -  This must be a valid elementary data type.  Some examples of
elementary data types are "int", "WORD", "char",
"DWORD", "char \*", or "BOOL".  

  




Output :  

(routine)  -  The type of the return value is specified by the "Type"
argument.  

  

  

ap  -  The variable argument list pointer is updated to point to the next
argument.  

  




 **Sample Usage :**


/\* Retrieving the
parameters to NSFDBOPENEXTENDED. \*/


 


/\* Declaration of the
function we're examining:  

    STATUS LNPUBLIC NSFDbOpenExtended (


           char far
\*PathName,  

           WORD Options,  

           HANDLE hNames,  

           TIMEDATE far \*ModifiedTime,  

           DBHANDLE far \*rethDB,  

           TIMEDATE far \*retDataModified,  

           TIMEDATE far \*retNonDataModified);  

  

If you only want the dbHandle, you still must retrieve all of the other
parameters first.  

\*/  

  DBHANDLE dbHandle;  

  VARARG\_PTR argPtr;              /\* Initialize pointer \*/  

  

  VARARG\_GET( argPtr, char FAR \* );      /\* Skip PathName \*/  

  VARARG\_GET( argPtr, WORD );            /\* Skip Options \*/  

  VARARG\_GET( argPtr, HANDLE );          /\* Skip hNames \*/  

  VARARG\_GET( argPtr, TIMEDATE FAR \* );/\* Skip ModifiedTime \*/   

  dbHandle = \*( DBHANDLE FAR \* )VARARG\_GET( argPtr, DBHANDLE FAR \*);  

  VARARG\_GET( argPtr, TIMEDATE FAR \* );  

  VARARG\_GET( argPtr, TIMEDATE FAR \* );


 **See Also :**


**[EMHANDLER](EMHANDLER.md)**


**[EMRECORD](EMRECORD.md)**


**[VARARG\_PEEK](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7585446D5184259C852562420066445B)**


**[VARARG\_PTR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F8B0E9C0C9F111F58525624200614B5E)**


**[VARARG\_START](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/48BF4EE617BE557C85256242005E8461)**



----------------------------------------------------------------------------------------------------------


 





