##### Symbolic Value : Abstract
##### ABS_xxx - Abstraction commands.
---
```
#include <misc.h>
```
**Description :**

These symbolic values are strings that may be combined and passed to the 
Abstract() routine to control conversion of the text.  Abstraction commands may 
be combined by placing them together in a single null-terminated string, 
separated by spaces.

**Sample Usage :**
```
STATUS ShrinkText ( char *pInput, int bufSize, char *pOutput,
int *pOutputSize )
{
	/* If you put character strings one after the */
	/* other like this, the C compiler will combine */
	/* them into a single string.    */
char commandString =
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
/* "tryfit ab-usedict ab-dropvowels=0 abbrev tryfit" */

return (Abstract (commandString, pInput, bufSize, pOutput,
	pOutputSize);
}

```
**See Also :**
[Abstract](/domino-c-api-docs/reference/Func/Abstract)
---
