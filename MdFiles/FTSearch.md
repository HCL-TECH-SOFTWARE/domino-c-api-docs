




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Full Text Search**



**FTSearch** **- Performs
a full text search.**


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**



STATUS
LNPUBLIC **FTSearch(**  

      DBHANDLE  hDB,  

      DHANDLE far \*phSearch,  

      HCOLLECTION  hColl,  

      char far \*Query,  

      DWORD  Options,  

      WORD  Limit,  

      DHANDLE  hIDTable,  

      DWORD far \*retNumDocs,  

      DHANDLE far \*Reserved,  

      DHANDLE far \*rethResults**);**



**Description :**



This
function returns the result of a full text search.   

  

The first argument of FTSearch is the handle to the database that is to be
searched.  

  

The second argument is a pointer to a handle to a full text search.  You must
first call FTOpenSearch to obtain this handle and allocate resources for it. 
Once the search is completed, use FTCloseSearch to close the full text search
handle and deallocate the memory associated with it.  Please note that this
handle may be modified by the FTSearch.  

  

The third argument is a collection handle.  Use NULLHANDLE if you want to
search all documents in the database.  Use a collection handle (obtained from
NIFOpenCollection) in conjunction with the FT\_SEARCH\_SET\_COLL Option argument
in order to find documents in a particular view that match the query.  The
FT\_SEARCH\_SET\_COLL option will associate an FT\_SEARCH\_RESULTS table with the
collection handle.  You may then obtain the results of the search by performing
NIFReadEntries on this collection using one of the NAVIGATE\_xxx\_HIT flags (see
Symbolic Values, NAVIGATE\_xxx, NAVIGATE\_xxx [NEXTxxx], NAVIGATE\_xxx [PREVxxx]).  

    

The fourth argument is a pointer to a query string.  The rule for the query
syntax is documented in "To use operators to refine a search," in the
"Searching for Information" section of the *Notes  Help*
database.  

  

The fifth argument is a bit mask of search options.  These options may be
combined by bitwise OR-ing them together.  See FT\_SEARCH\_xxx for a list of
these options.  

  

The sixth argument is the maximum number of documents to be returned.  You may
pass in 0 to obtain the maximum number of results for the search.  

  

The set of documents that are to be searched may be further restricted by
providing a handle to an ID Table as the seventh argument.  You must fill the
ID Table with references to the documents you want searched.  

  

The returned results of the full text search is in one of four specified formats. 
Use the FT\_SEARCH\_xxx options to specify one of four formats for the result. 
See the description of the rethResults argument below for an explanation of
each of the result formats.  In addition, if the FT\_SEARCH\_SET\_COLL option is
specified, then the collection handle used as the third argument to FTSearch
will internally be associated with an FT\_SEARCH\_RESULTS table.  In this case,
you may obtain the results of the search by performing NIFReadEntries on this
collection using one of the NAVIGATE\_xxx\_HIT flags (see Symbolic Values,
NAVIGATE\_xxx, NAVIGATE\_xxx [NEXTxxx], NAVIGATE\_xxx [PREVxxx]).  When using the
FT\_SEARCH\_SET\_COLL option, you can access each entry's search score, by using
the FT\_SEARCH\_SCORES search option in FTSearch and setting the READ\_MASK\_SCORE
ReadFlag in NIFReadEntries.


 


**Parameters :**



Input :  

hDB  -  The handle to the open database to be searched.  

  

phSearch  -  Pointer to the search handle previous allocated in FTOpenSearch.  

  

hColl  -  Collection handle of view that is to receive an FT\_SEARCH\_RESULTS
table if the FT\_SEARCH\_SET\_COL option is specified.  Use NULLHANDLE to search
all documents in the database.  

  

Query  -  Pointer to a string containing a query.  Follow the syntax rules as
described in "To use operators to refine a search," in the
"Searching for Information" section of the Notes 5 Help database.  

  

Options  -  Search options (see FT\_SEARCH\_xxx).  Options may be or'd together.  

  

Limit  -  Maximum number of documents to return.  Use 0 to return the maximum
number of results for the search. For more information about specifying the
maximum number of results in a full text search, see the Domino Administration
Help database.  

  

hIDTable  -  Handle to an ID table to further refine the search.  Use
NULLHANDLE if this is not required.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_FT\_NOMATCHES - No documents were found by this search.  Arguments used in a
previous call to FTSearch remain valid.   

  

ERR\_xxx - Error returned by lower level C API functions. Call OSLoadString to
interpret the code.  

  

  

phSearch  -  This handle may be modified by the FTSearch API.  

  

retNumDocs  -  Pointer to the returned number of documents found.   

  

Before any further processing, be sure to check the value of this field after
calling the API.  If no document is returned (retNumDocs==0), do not lock the
rethResults because this handle will be a NULLHANDLE.  

  

Reserved  -  Reserved for future use.  Pass in NULL for this parameter.  

  

rethResults  -  Pointer to returned handle to the search results.  The search
results are either in an ID Table or in an FT\_SEARCH\_RESULTS structure,
depending on whether FT\_SEARCH\_SET\_COLL and/or FT\_SEARCH\_RET\_IDTABLE were set
in the Options argument.  

  

FT\_SEARCH\_SET\_COLL not set,  FT\_SEARCH\_RET\_IDTABLE not set:  

An FT\_SEARCH\_RESULTS table  is allocated and returned to the caller in \*rethResults.  

  

FT\_SEARCH\_SET\_COLL not set,  FT\_SEARCH\_RET\_IDTABLE set:  

An ID Table is allocated and returned to the caller in \*rethResults.  

  

FT\_SEARCH\_SET\_COLL set,          FT\_SEARCH\_RET\_IDTABLE not set:  

An FT\_SEARCH\_RESULTS table is set in the collection.  NULLHANDLE is returned in
\*rethResults.  

  

FT\_SEARCH\_SET\_COLL set,          FT\_SEARCH\_RET\_IDTABLE set:  

An FT\_SEARCH\_RESULTS table is set in the collection.  An ID Table is allocated
and returned to the caller in \*rethResults.  

  

Except in the case where FT\_SEARCH\_SET\_COLL set, and FT\_SEARCH\_RET\_IDTABLE is
not set, rethResults will be NULLHANDLE if no documents are returned from
FTSearch.   

   

If FTSearch returns a non-NULLHANDLE in \*rethResults, then use OSLock to obtain
a pointer to the returned results.  After processing the returned results, use
OSUnlockObject to unlock the pointer and OSMemFree to free the memory
associated with this handle.  

  




 **See Also :**


**[FTCloseSearch](FTCloseSearch.md)**


**[FTOpenSearch](FTOpenSearch.md)**


**[FT\_SEARCH\_RESULTS](FT_SEARCH_RESULTS.md)**


**[FT\_SEARCH\_RESULT\_ENTRY](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/59F65E1E7DFF89A98525635F0080BA2A)**



----------------------------------------------------------------------------------------------------------


 





