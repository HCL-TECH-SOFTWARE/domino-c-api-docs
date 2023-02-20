##### Function : Search
##### NSFQueryDBExt - Executes a Domino Query Language query and return results, parse or explain output
---
```
#include <dbmisc.h>
STATUS NSFQueryDBExt(

	DBHANDLE  hDB,
	char *Query,
	DWORD  Flags,
	DWORD  MaxDocsScanned,
	DWORD  MaxEntriesScanned,
	DWORD  MaxMsecs,
	DHANDLE *retResults,
	MEMHANDLE *retError,
	MEMHANDLE *retExplain,
	MEMHANDLE  hQArgs);
```
**Description :**

This function runs DQL queries.  Its inputs are a database handle, the query 
text and a set of flags.  Its outputs are the results, explain output and extra 
error output.

For Domino Query Language syntax, please see the relevant documentation for 
your current release.

**Parameters :**
Input :
hDB  -  The handle to the database providing context for the DQL query.  Queries can reference other query output and that output can reside in a number of databases, in which case the hDB will provide the database to use in executing the query and the residence of any results.

Query  -  The DQL query to be executed, explained or parsed.  Syntax is documented in the Domino Query Language documentation.  A query can be up to 64K in size.

Flags  -  Flags passed in to govern DQL processing for the query.  The relevant settings reside in dbmisc.h with the prefix QUEP_xxx with the following available settings:

QUEP_VIEWREFRESH	       /* refresh all views when they are opened(default is NO_UPDATE) */
QUEP_PARSEONLY                    /* to check for syntax only - stops short of planning */
QUEP_EXPLAIN	                      /* Produce Explain output */
QUEP_NOVIEWS	                      /* Use NSF scans only  - can cause failure if syntax demands view or full text index access */
QUEP_FT_REFRESH	      /* For the 1st FT search, update the index */
QUEP_DSGNCATREFRESH   /* before running the query, build/refresh the design catalog */
QUEP_DSGNCATREBUILD     /* before running the query, rebuild the design catalog */

MaxDocsScanned  -  Specifies the maximum total number of documents scanned to execute or explain the query.  Overrides the default limit (500000) and that set via the QUERY_MAX_DOCS_SCANNED notes.ini setting.  Pass in 0 to not override.

MaxEntriesScanned  -  Specifies the maximum total number of view entries scanned to execute or explain the query.  Overrides the default limit (200000) and that set via the QUERY_MAX_VIEW_ENTRIES_SCANNED notes.ini setting.  Pass in 0 to not override.

MaxMsecs  -  Specifies the maximum milliseconds a query can take to execute or explain.  Overrides the default limit (300000 - 5 minutes) and that set via the QUERY_MAX_MSECS_TOTAL notes.ini setting.  The value is not checked every millisecond but at specific points in query term execution.  Pass in 0 to not override.

hQArgs  -  Passes in values to be bound to DQL substitution values.  Constructed by calling NSFQueryDBAddArgs.  It is the responsibility of the caller to free the MEMHANDLE once processing is complete.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is:

NOERROR - No errors occurred during the execution, parsing or explaining of the specified Domino Query Language query.
ERR_xxx - Errors returned by lower level Notes functions.  There are many possible causes and it is best to use the code in a call to OSLoadString and display the error for the user.   Additional error text is provided dereferencing the output retError MEMHANDLE.


retResults  -  Returns the results from a DQL execute or explain.  Depending upon the flags passed in, the results will either be an IDTable or a Queue of data values.  It is the responsibility of the caller to free the DHANDLE once processing is complete.

retError  -  Returns additional text when DQL processing encounters an error state.   It is the responsibility of the caller to free the MEMHANDLE once processing is complete.

retExplain  -  Returns explain text when requested via flag setting.   It is the responsibility of the caller to free the MEMHANDLE once processing is complete.


**See Also :**
---
