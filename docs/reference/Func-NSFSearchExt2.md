##### Function : Database
##### NSFSearchExt2 - Uses an associated timer to control the duration of the database search operation.
---
##### #include <nsfsearc.h>
STATUS **NSFSearchExt2(**

	DBHANDLE  hDB,
	FORMULAHANDLE  hFormula,
	DHANDLE  hFilter,
	DWORD  FilterFlags,
	char *ViewTitle,
	DWORD  SearchFlags,
	DWORD  SearchFlags1,
	WORD  NoteClassMask,
	TIMEDATE *Since,
	STATUS(far PASCAL *)  EnumRoutine,
	void *EnumRoutineParameter,
	DWORD  dwSecsToSearch,
	TIMEDATE *retUntil);
**Description :**
You can use this routine to sequentially search an entire Notes database and 
gain access to many of the fields enumerated in each note. For each note found 
in the database, the caller's action routine is called to process the note. In 
addition, the routine has a parameter "dwSecsToSearch" that is the number of 
seconds that you specify for the call to execute the search without any 
hindrance, after which the search will terminate.

Set a value greater than 0 if you want to use this feature. Also there is an 
upper limit (dwMaxSecsToSearch) for the "dwSecsToSearch" value. This limit 
comes from the  NSF_MAX_SEARCH_API_SECS notes.ini, if set; otherwise the 
default value 
of NSFSEARCH4_DEFAULT_MAX_MSECS is used - see nsf/nsfdata.c

NOTE: NSFSEARCH4_THRESHOLD_BYTES (1024 * 1024) is the maximum byte-threshold
limit. Once this limit is reached in the current search, the routine no longer 
counts bytes and simply proceeds with checking for the timeout seconds.
**Parameters :**
Input :
hDB  -  Handle to database (from NSFDbOpen) 

hFormula  -  Handle to optional formula (from NSFFormulaCompile)
(if NULLHANDLE, searches ALL notes in database).

hFilter  -  Handle to the search filter.

FilterFlags  -  filter Flags.

ViewTitle  -  Address of view title string used for @ViewTitle function or NULL if not needed (or if no formula is being used)

SearchFlags  -  SEARCH_xxx flags (see "nsfsearc.h")

SearchFlags1  -  Optional SearchFlags.

NoteClassMask  -  Mask of NOTE_CLASS_xxx flags (see "nsfnote.h")

Since  -  Starting time/date for search.
(if NULL, searches ALL notes in database)

EnumRoutine  -  Address of routine to be called for each note found.

EnumRoutineParameter  -  Parameter to be passed to routine.

dwSecsToSearch  -  Number of seconds user wishes to specify for the call to execute without any hindrance,after which, the search will terminate.

Output :
(routine)  -  On failure, it returns related and relevant error codes (like : error related to namelist assosiated with user performing the database operation, error releated to database, queue and the timer related to time limit set for search e.g. 
ERR_TIMEOUT_CANNOT_BE_ZERO),
On successful search, it returns NOERROR.


retUntil  -  Address of TIMEDATE to recieve the ending time of the search
or NULL if ending time is not desired.

**Sample Usage :**
```
if (error = NSFDbOpen (db_filename, &db_handle))
{
PrintAPIError (error);
NotesTerm();
return (1);
}

if (error = NSFSearchExt2 (
db_handle, /* database handle */
NULL, /* selection formula */
NULLHANDLE, /* handle to the filter */
SEARCH_FILTER_NONE, /* filter flags */
NULL, /* title of view in selection formula */
0, /* search flags (unused) */
0, /* search flags (unused) */
NOTE_CLASS_DOCUMENT,/* note class to find */
NULL, /* starting date (unused) */
print_fields, /* call for each note found */
&db_handle, /* argument to print_fields */
NULL, /* returned ending date (unused) */
5)) /* timeout seconds. if = "0" then, NO timeout */
{
NSFDbClose (db_handle);
PrintAPIError (error); 
NotesTerm();
return (1);
}


```
**See Also :**
[](D:/md_files/.md)
---
