##### Symbolic Value : Abstract
##### ABS_xxx - Abstraction commands.
---
```
#include <misc.h>
```

**Symbolic Values :**

	ABS_TEXTONLY	  -  Delete all non-text chunks from the input.

	ABS_COUNTWORDS	  -  Compute significance values for the words in the text.

	ABS_SAVE	  -  Save the state of the abstraction engine on an internal stack.

	ABS_RESTORE	  -  Restore the last saved state of the abstraction engine.

	ABS_TRYFIT	  -  If the output text will fit into the output buffer, place the results in the output buffer and return.

	ABS_ABBREV	  -  Apply the abbreviation rules to the input text.

	ABS_SORTCHUNKS	  -  Sort the chunks according to chunk significance values.

	ABS_NOSTOPLIST	  -  Do not use the stop list; include insignificant words when copying text from the input to the output.

	ABS_NOSIGLIST	  -  Do not use the significant words list when copying text from the input to the output.

	ABS_USEDICT	  -  Set the ab-usedict parameter to True.

	ABS_NODICT	  -  Set the ab-usedict parameter to False.

	ABS_DROPVOWELS	  -  Set the ab-dropvowels parameter to True.

	ABS_KEEPVOWELS	  -  Set the ab-dropvowels parameter to False.

	ABS_TRIMWHITE	  -  Set the ab-trimwhite parameter to True.

	ABS_NOTRIMWHITE	  -  Set the ab-trimwhite parameter to False.

	ABS_TRIMPUNCT	  -  Set the ab-trimpunct parameter to True.

	ABS_NOTRIMPUNCT	  -  Set the ab-trimpunct parameter to False.

	ABS_DROPFIRSTVOWEL	  -  Set the ab-dropfirstvowels parameter to True.

	ABS_KEEPFIRSTVOWEL	  -  Set the ab-dropfirstvowels parameter to False.

	ABS_CHUNKBEGIN	  -  Set the output buffer start string parameter. Follow this string with the characters to insert at the start of the output buffer.

	ABS_CHUNKSEP	  -  Set the output chunk separator string parameter. Follow this string with the characters to insert between chunks, or one of the special values "space", "cr", or "crlf".

	ABS_CHUNKEND	  -  Set the output buffer end string parameter. Follow this string with the characters to append to the end of the output buffer.


**Description :**

These symbolic values are strings that may be combined and passed to the Abstract() routine to control conversion of the text.  Abstraction commands may be combined by placing them together in a single null-terminated string, separated by spaces.


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
