




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



**Symbolic Value : Abstract**



**ABS\_xxx** **-** Abstraction
commands.


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**


 **Symbolic Values :**      ABS\_TEXTONLY      -  Delete all non-text chunks from the
input.  

  

      ABS\_COUNTWORDS           -  Compute significance values for the words in
the text.  

  

      ABS\_SAVE   -  Save the state of the abstraction engine on an internal
stack.  

  

      ABS\_RESTORE       -  Restore the last saved state of the abstraction
engine.  

  

      ABS\_TRYFIT            -  If the output text will fit into the output
buffer, place the results in the output buffer and return.  

  

      ABS\_ABBREV          -  Apply the abbreviation rules to the input text.  

  

      ABS\_SORTCHUNKS            -  Sort the chunks according to chunk
significance values.  

  

      ABS\_NOSTOPLIST   -  Do not use the stop list; include insignificant words
when copying text from the input to the output.  

  

      ABS\_NOSIGLIST      -  Do not use the significant words list when copying
text from the input to the output.  

  

      ABS\_USEDICT         -  Set the ab-usedict parameter to True.  

  

      ABS\_NODICT           -  Set the ab-usedict parameter to False.  

  

      ABS\_DROPVOWELS            -  Set the ab-dropvowels parameter to True.  

  

      ABS\_KEEPVOWELS             -  Set the ab-dropvowels parameter to False.  

  

      ABS\_TRIMWHITE    -  Set the ab-trimwhite parameter to True.  

  

      ABS\_NOTRIMWHITE           -  Set the ab-trimwhite parameter to False.  

  

      ABS\_TRIMPUNCT    -  Set the ab-trimpunct parameter to True.  

  

      ABS\_NOTRIMPUNCT           -  Set the ab-trimpunct parameter to False.  

  

      ABS\_DROPFIRSTVOWEL    -  Set the ab-dropfirstvowels parameter to True.  

  

      ABS\_KEEPFIRSTVOWEL     -  Set the ab-dropfirstvowels parameter to False.  

  

      ABS\_CHUNKBEGIN             -  Set the output buffer start string
parameter. Follow this string with the characters to insert at the start of the
output buffer.  

  

      ABS\_CHUNKSEP     -  Set the output chunk separator string parameter. Follow
this string with the characters to insert between chunks, or one of the special
values "space", "cr", or "crlf".  

  

      ABS\_CHUNKEND     -  Set the output buffer end string parameter. Follow
this string with the characters to append to the end of the output buffer.  

  




**Description :**



These
symbolic values are strings that may be combined and passed to the Abstract()
routine to control conversion of the text.  Abstraction commands may be
combined by placing them together in a single null-terminated string, separated
by spaces.


 **Sample Usage :**


STATUS ShrinkText (
char \*pInput, int bufSize, char \*pOutput,


int \*pOutputSize )


{


        /\* If you put
character strings one after the        \*/


        /\* other like
this, the C compiler will combine      \*/


        /\* them into a
single string.                        \*/


char    commandString =


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
command string, it would be:          \*/


/\*      "ChunkSep=cr
ab-trimwhite ab-trimpunct textonly "    \*/


/\*      "tryfit
ab-usedict ab-dropvowels=0 abbrev tryfit"    \*/


 


return (Abstract
(commandString, pInput, bufSize, pOutput,


        pOutputSize);


}


 


 **See Also :**


**[Abstract](Abstract.md)**



----------------------------------------------------------------------------------------------------------


 





