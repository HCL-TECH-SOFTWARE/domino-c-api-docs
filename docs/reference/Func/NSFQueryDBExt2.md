##### Function : Search
##### NSFQueryDBExt2 - Run Domino Query Language (DQL) queries.
---
```
#include <dbmisc.h>
STATUS NSFQueryDBExt2(

	DBHANDLE  dbhandle,
	char *query,
	DWORD  Qlen,
	DWORD  Flags,
	DWORD  MaxDocsScanned,
	DWORD  MaxEntriesScanned,
	DWORD  MaxMsecs,
	MEMHANDLE *retResults,
	MEMHANDLE *retError,
	MEMHANDLE *retExplain,
	MEMHANDLE  hQArgList);
```
**Description :**

Run DQL queries. Its inputs are a database handle, the query text, length of 
query text, and a set of flags. Returns explanation of output and extra error 
output.

**Parameters :**
Input :
dbhandle  -  The handle to the database providing context for the DQL query.

query  -  The DQL query to be executed, explained or parsed. The text of the query must be translated into LMBCS prior to execution using OSTranslate or OSTranslate32.

Qlen  -  Length of query string. Maximum length is 64K.

Flags  -  Flags passed that govern query processing. Refer to QUEP_xxx for allowed flag inputs.

MaxDocsScanned  -  The maximum number of documents scanned to execute or explain the query.

MaxEntriesScanned  -  The maximum number of view entries scanned to execute or explain the query.

MaxMsecs  -  The maximum time in milliseconds a query can take to execute or explain.

hQArgList  -  Values passed to be bound to DQL substitution values. The caller must free the MEMHANDLE once processing is complete.  Substitution arguments are supplied through calls to NSFQueryDBAddArgs.

Output :
(routine)  -  Returns status from the call, either success or an error. 
   The return codes include: 
    NOERROR - On success. 
    ERR_MISC_INVALID_ARGS - Invalid arguments.


retResults  -  Returns the results from a DQL execute or explain.  Depending upon the flags passed in, the results will either be an IDTable or a queue of data values.  It is the responsibility of the caller to free the DHANDLE once processing is complete.

retError  -  Returns additional text when DQL processing encounters an error state.  It is the responsibility of the caller to free the MEMHANDLE once processing is complete.

retExplain  -  Returns explain text when requested via flag setting. It is the responsibility of the caller to free the MEMHANDLE once processing is complete.


**Sample Usage :**
```
	/* To Execute or explain DQL Queries:
 
	hDb is a DBHANDLE from a previously opened database.
	pQuery is a LMBCS-translated query using OSTranslate.
	Len is length of the pQuery in bytes.
	MaxDocsScanned is maximum number of documents to be scanned.
	MaxEntriesScanned is maximum number of view entries to be scanned.
	MaxMsecs is maximum time in milliseconds.
	hQargList is either NULLMEMHANDLE or the output from a call or calls to 
NSFQueryDBAddArgs. */

	if (err = NSFQueryDBExt2(hDb, 
	 pQuery, 
	 Len, 
	 Flags, 
	 MaxDocsScanned, 
	 MaxEntriesScanned,  
	 MaxMsecs, 
	 &retResults,  
	 &retError, 
	 &retExplain, 
	 hQargList))
	{
	 goto errout;
	}
```
**See Also :**
---
