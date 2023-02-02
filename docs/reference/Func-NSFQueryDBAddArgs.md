##### Function : Database
##### NSFQueryDBAddArgs - Build a list of values to input into a Domino Query Language (DQL) query.
---
##### #include <dbmisc.h>
STATUS  **NSFQueryDBAddArgs(**

	QUEP_ARGVAL *pArg,
	MEMHANDLE *phQargList);
**Description :**
Build a lists of values to input into a DQL query, specifying arguments through 
QUEP_ARGVAL structure. Validates QUEP_ARGVAL structure and compares to stored 
values. Returns NOERROR and MEMHANDLE (phQargList) if successful. If errors are 
found in parsing arguments or if validation fails, returns 
ERR_MISC_INVALID_ARGS. If memory errors are found, returns ERR_MEMORY.
**Parameters :**
Input :
pArg  -  A value, ordinal, or name for the argument to build. 

Output :
(routine)  -  Returns status from the call, either success or an error. 
   The return codes include: 
    NOERROR - On success. 
    ERR_MISC_INVALID_ARGS - Invalid arguments. 
    ERR_MEMORY - Memory failure.


phQargList  -  Set of QUEP_ARGVALs that were built.

**Sample Usage :**
```
	/* To build argument list for DQL 
	pArg is pointer to a QUEP_ARGVAL struct built prior to this call. */
  QUEP_ARGVAL pArg = {0};
	MEMHANDLE phQArgList = NULLMEMHANDLE;
	pArg.type = TYPE_TEXT;
	strncpy(pArg.Value, "\'This is another line of simple text.\'", 
sizeof(pArg.Value));
	pArg.length = strlen(pArg.Value);
	pArg.bBinaryForm = FALSE;
	if (err = NSFQueryDBAddArgs(&pArg, &phQArgList))
   goto errout; 
	... 
	if (err = NSFQueryDBExt2(..., phQArgList)) 
	 goto errout;
```
**See Also :**
[](D:/md_files/.md)
---
