##### Function : Search
##### NSFSearchWithUserNameList - Scans database or directory, processing matching items.
---
##### #include <nsfsearc.h>
STATUS LNPUBLIC **NSFSearchWithUserNameList(**

	DBHANDLE  hDB,
	FORMULAHANDLE  hFormula,
	char far *ViewTitle,
	WORD  SearchFlags,
	WORD  NoteClassMask,
	TIMEDATE far *Since,
	NSFSEARCHPROC  EnumRoutine,
	void far *EnumRoutineParameter,
	TIMEDATE far *retUntil,
	DHANDLE  nameList);
**Description :**
This function scans all the notes in a database or files in a directory and 
allows for a NAMES_LIST structure UserName to provide authentication for 
trusted servers. Based on several search criteria, the function calls a 
user-supplied routine (an action routine) for every note or file that matches 
the criteria. NSFSearch is a powerful function that provides the general search 
mechanism for tasks that process all or some of the documents in a database or 
all or some of the databases in a directory.

Specify a formula argument to improve efficiency when processing a subset of 
the notes in a database. 

In addition, the formula argument can be used to return computed "on-the-fly" 
information.  To do this, you specify that a value returned from a formula is 
to be stored in a temporary field of each note.  This temporary field and its 
value is then accessible in the summary buffer received by the NSFSearch action 
routine without having to open the note.  For example, suppose you want the 
size of each note found by NSFSearch.  Do the following before the call to 
NSFSearch:
1.  Set up a scratch buffer with the following text:
char        szFormula[] = "DEFAULT dLength := @DocLength; @All";
By using the DEFAULT keyword, if the field, named dLength, exists, the current 
value is used.  If the field does not exist, the note is treated as if the 
field does exist and the dLength field contains the value from @DocLength.
2.  Compile the buffer with NSFFormulaCompile.
3.  Call NSFSearch  and specify the formula handle from NSFFormulaCompile for 
the hFormula argument and specify SEARCH_SUMMARY for the SearchFlags argument.
4.  In the action routine of NSFSearch, if you get a search match, look at the 
summary information.  The dLength field will be one of the items in the summary 
information buffer.

Specify a note class to restrict the search to certain classes of notes. 
Specify NOTE_CLASS_DOCUMENT to find documents. Specify the "since" argument to 
limit the search to notes created or modified in the database since a certain 
time/date. 

When used to search a database, NSFSearch searches the database file 
sequentially. If the search is not time-constrained (the "since" argument is 
NULL or specifies the TIMEDATE_WILDCARD, ANYDAY/ALLDAY), then NSFSearch may 
find a given note more than once during the same search. If a 
non-time-constrained search passes a certain note to the action routine, and 
that note is subsequently updated, then NSFSearch may find that note again and 
pass it to the action routine a second time during the same search. This may 
happen if Domino or Notes relocates the updated note to a position farther down 
in the file. If your algorithm requires processing each note once and only 
once, then use time-constrained searches. Alternatively, build an ID table as 
you search, avoid updating notes in the action routine, and process the ID 
table after the search completes. ID tables are guaranteed not to contain a 
given ID more than once.
**Parameters :**
Input :
hDB  -  The handle to the database or directory that you want to scan.

hFormula  -  A handle to a selection formula that is one of the match criteria for notes in the database. You must compile the formula with NSFFormulaCompile to get the handle. For the equivalent of "@All", specify NULLHANDLE for this argument.

ViewTitle  -  The address of a null-terminated string that contains a view name.  If the selection formula specified by the 2nd argument (hFormula) contains the @ViewTitle function, then Domino or Notes uses the view name specified by this argument (ViewTitle) to resolve this @ViewTitle function.  

If the selection formula specified by the 2nd argument (hFormula) does not contain the @ViewTitle function, or if you are not using a the selection formula (hFormula is NULLHANDLE), then set this argument (ViewTitle) to NULL. 


SearchFlags  -  Flags that control what items are searched and what information is returned. The flags are defined in SEARCH_xxx.  If using SEARCH_NOTIFYDELETIONS, the note must be opened to obtain the NOTE_CLASS_DEFAULT status. 

NoteClassMask  -  The types of notes or files that are matched. Note types are defined in NOTE_CLASS_xxx and file types are defined in FILE_xxx. Within NOTE_CLASS_xxx, the flags may be or'ed together to find more than one kind of note.  Within FILE_xxx, the flags may also be or'ed together.

Since  -  The date of the earliest modified note that is matched. The note's "Modified in this file" date is compared to this date.  Specify NULL if you do not wish any filtering by date.

NOTE: if this argument is specified, the flag SEARCH_ALL_VERSIONS will be automatically enabled, which returns deleted notes and non-matching notes modified since the specified date.  In this situation, you must check the "MatchesFormula" field of the SEARCH_MATCH structure (passed to the action routine) for the value SE_FMATCH in order to determine if the note is a matching note.

EnumRoutine  -  The routine, that you write, which is called once for each note that matches the search criteria.

The definition of NSFSEARCHPROC is:

typedef STATUS (LNCALLBACKPTR NSFSEARCHPROC)
                     (void far *EnumRoutineParameter,
                     SEARCH_MATCH far *SearchMatch,
                     ITEM_TABLE far *SummaryBuffer);

All action routines for NSFSearch must use this calling sequence.

The summary_buffer pointer will be NULL if the SEARCH_SUMMARY flag is not set in the search_flags parameter.

EnumRoutineParameter  -  An optional parameter to EnumRoutine. One common use for this parameter is to pass the handle of the database to EnumRoutine.  Without the database handle EnumRoutine only can access the summary information for the note, but cannot open the note.

nameList  -  May be NULLHANDLE or a HANDLE to a NAMES_LIST structure that contains a UserName that is used to provide authentication for trusted servers.  This causes the UserName's ACL permissions in the database to be enforced.  Please see NSFBuildNamesList for more information on building a NAMES_LIST structure.

Output :
(routine)  -  Return status from this call -- indicates either success or what the error is:

NOERROR - No errors occurred during the execution of NSFSearch or during any of the calls to the action routine.
ERR_xxx - Errors returned by lower level Notes functions.  There are so many possible causes, that It is best to use the code in a call to OSLoadString and display the error for the user.  Application specific error returns also may be generated by your own action routine that you supply to NSFSearch.


retUntil  -  The ending (current) time/date of this search.  Returned so that it can be used in a subsequent call to NSFSearch as the "Since" argument.

**See Also :**
[NSFFormulaCompile](D:/md_files/NSFFormulaCompile.md)
[NSFSearch](D:/md_files/NSFSearch.md)
[NSFSEARCHPROC](D:/md_files/NSFSEARCHPROC.md)
[SEARCH_xxx](D:/md_files/SEARCH_xxx.md)
---
