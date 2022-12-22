




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



**Function : Abstract**



**Abstract** **- Generate
automated abstract of text**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **Abstract(**  

      char far \*szKeywords,  

      char far \*szText,  

      DWORD  maxAbstract,  

      char far \*szAbstract,  

      DWORD far \*retSize**);**



**Description :**



Scan the
input text using the rules specified by commands in the szKeywords parameter,
and place the results in the szAbstract output buffer.  For more information,
please refer to the chapter "Automated Abstracts" in the *User
Guide*.  Symbolic values have been provided for the supported abstraction
engine commands;  see the entry ABS\_xxx for these commands.


 


**Parameters :**



Input :  

szKeywords  -  Null-terminated string containing commands and parameter
settings, separated by spaces.  See ABS\_xxx for the list of parameters and
commands.  

  

szText  -  The text to be processed by the abstraction engine.  

  

maxAbstract  -  Size of the output buffer.  

  




Output :  

(routine)  -  NOERROR - Abstract computation succeeded.  

ERR\_ABSTRACT\_INVALID\_SIZE - Size of the output buffer, specified by
maxAbstract, must be >= 0.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling  

  

  

szAbstract  -  Buffer where the output abstract will be written.  

  

retSize  -  Number of bytes in the output abstract.  

  




 **Sample Usage :**


STATUS ShrinkText(


   char \*pInput,


   int bufSize,


   char \*pOutput,


   int \*pOutputSize)


{


    /\* If you put
character strings one after the        \*/


    /\* other like this,
the C compiler will combine      \*/


    /\* them into a
single string.                        \*/


char       commandString
[] =


    ABS\_CHUNKSEP   /\*
Set the chunk separator to         \*/


    "cr "                  /\*
carriage return; note space!!      \*/


    ABS\_TRIMWHITE  /\*
Reduce whitespace                  \*/


    ABS\_TRIMPUNCT  /\*
Remove whitespace at punctuation   \*/


    ABS\_TEXTONLY   /\*
Copy only text strings             \*/


    ABS\_TRYFIT             /\*
See if that much fits              \*/


    ABS\_USEDICT            /\*
If not, use dictionary             \*/


    ABS\_KEEPVOWELS /\*
Leave vowels                              \*/


    ABS\_ABBREV             /\*
and abbreviate the text            \*/


    ABS\_TRYFIT;


 


/\* If you entered the
command string, it would be:              \*/


/\*  "ChunkSep=cr
ab-trimwhite ab-trimpunct textonly "    \*/


/\*  "tryfit
ab-usedict ab-dropvowels=0 abrev tryfit"     \*/


 


return (Abstract
(commandString, pInput, bufSize, pOutput,


    pOutputSize);


}


 **See Also :**


**[ABS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/90B13CCEB920157385256252006F1781)**



----------------------------------------------------------------------------------------------------------


 





