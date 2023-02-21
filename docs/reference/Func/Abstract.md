##### Function : Abstract
##### Abstract - Generate automated abstract of text
---
```
#include <misc.h>
STATUS LNPUBLIC Abstract(

	char far *szKeywords,
	char far *szText,
	DWORD  maxAbstract,
	char far *szAbstract,
	DWORD far *retSize);
```
**Description :**

Scan the input text using the rules specified by commands in the szKeywords 
parameter, and place the results in the szAbstract output buffer.  For more 
information, please refer to the chapter "Automated Abstracts" in the User 
Guide.  Symbolic values have been provided for the supported abstraction engine 
commands;  see the entry ABS_xxx for these commands.

**Parameters :**
Input :
szKeywords  -  Null-terminated string containing commands and parameter settings, separated by spaces.  See ABS_xxx for the list of parameters and commands.

szText  -  The text to be processed by the abstraction engine.

maxAbstract  -  Size of the output buffer.

Output :
(routine)  -  NOERROR - Abstract computation succeeded.
ERR_ABSTRACT_INVALID_SIZE - Size of the output buffer, specified by maxAbstract, must be >= 0.
ERR_xxx - Errors returned by lower level functions: (memory management, file operations, network errors, etc.).  There are so many possible causes, that it is best to use the code in a call to OSLoadString and display/log the error for the user as your default error handling


szAbstract  -  Buffer where the output abstract will be written.

retSize  -  Number of bytes in the output abstract.


**Sample Usage :**
```
STATUS ShrinkText(
   char *pInput,
   int bufSize,
   char *pOutput,
   int *pOutputSize)
{
	/* If you put character strings one after the */
	/* other like this, the C compiler will combine */
	/* them into a single string.    */
char commandString [] =
	ABS_CHUNKSEP /* Set the chunk separator to  */
	"cr "   /* carriage return; note space!! */
	ABS_TRIMWHITE /* Reduce whitespace   */
	ABS_TRIMPUNCT /* Remove whitespace at punctuation */
	ABS_TEXTONLY /* Copy only text strings  */
	ABS_TRYFIT  /* See if that much fits  */
	ABS_USEDICT  /* If not, use dictionary  */
	ABS_KEEPVOWELS /* Leave vowels    */
	ABS_ABBREV  /* and abbreviate the text  */
	ABS_TRYFIT;

/* If you entered the command string, it would be:  */
/* "ChunkSep=cr ab-trimwhite ab-trimpunct textonly " */
/* "tryfit ab-usedict ab-dropvowels=0 abrev tryfit" */

return (Abstract (commandString, pInput, bufSize, pOutput,
	pOutputSize);
}
```
**See Also :**
[ABS_xxx](/domino-c-api-docs/reference/Symb/ABS_xxx)
---
