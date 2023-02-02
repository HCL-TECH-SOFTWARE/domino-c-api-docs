##### Function : Full Text Search
##### FTSearchExt - Extended full text search
---
##### #include <ft.h>
STATUS LNPUBLIC **FTSearchExt(**

	DBHANDLE  hDB,
	DHANDLE far *phSearch,
	HCOLLECTION  hColl,
	char far *Query,
	DWORD  Options,
	WORD  Limit,
	DHANDLE  hIDTable,
	DWORD far *retNumDocs,
	DHANDLE far *Reserved,
	DHANDLE far *rethResults,
	DWORD far *retNumHits,
	DWORD  Start,
	WORD  Count,
	WORD  Arg,
	HANDLE  hNames);
**Description :**
FTSearchExt is a superset of FTSearch.  Calling it with all new parameters and 
flags clear will result in the same behavior as an FTSearch call.   In addition 
to the function performed  by the FTSearch, it supports Domain search, and 
URL-style and paged results.

For efficiency, use the Start, Count and Arg parameters to gain the paged 
results.  FtSearchExt will return a Count of results at a time.  It is the 
application program's responsibility to execute FTSearchExt multiple times by 
varying the Start value to read in all the hits.  If the Start and Count are 
zero, FTSearchExt will turn off the "paged result" feature.
**Parameters :**
Input :
hDB  -  The handle to the open database to be searched.

phSearch  -  Pointer to the search handle previous allocated in FTOpenSearch.  

hColl  -  Collection handle of view that is to receive an FT_SEARCH_RESULTS table if the FT_SEARCH_SET_COL option is specified.  Use NULLHANDLE to search all documents in the database.

Query  -  Pointer to a string containing a query.  Follow the syntax rules as described in "To use operators to refine a search," in the "Searching for Information" section of the Notes 5 Help database.

Options  -  Search options (see FT_SEARCH_XXX).  Options may be or'd together.

Limit  -  Maximum number of documents to return.  Use 0 to return the maximum number of results for the search.  For more information about specifying the maximum number of results in a full text search, see the Domino Administration Help database.

hIDTable  -  Handle to an ID table to further refine the search.  Use NULLHANDLE if this is not required.

Start  -  The starting document number for the paged result.  For the non-paged result, set this item to 0.  For the paged result, set this item to a non-zero number.

Count  -  Number of documents to return for the paged result.

Arg  -  Paged results additional argument.

hNames  -  User's name list (NAMES_LIST) or NULL

Output :
(routine)  -  Return status of the call - indicates either success or what the error is. The return codes include:

NOERROR

ERR_FT_NOMATCHES - No documents were found by this search.  Arguments used in a previous call to FTSearchExt remain valid. 

ERR_xxx - Error returned by lower level C API functions. Call OSLoadString to interpret the code.


phSearch  -  This handle may be modified by the FTSearchExt API.

retNumDocs  -  Number of documents returned in the results.

If no documents are found, the function will return ERR_FT_NOMATCHES and arguments used in a previous call to FTSearchExt remain valid. 

Reserved  -  Reserved for future use.  Pass in NULL for this parameter.

rethResults  -  Pointer to returned handle to the search results.  

Depending on the options set in the Options argument, the search results are either in an ID Table, or in an FT_SEARCH_RESULTS structure (see FT_RESULTS_XXX):

FT_SEARCH_SET_COLL not set,  FT_SEARCH_RET_IDTABLE not set:
        An FT_SEARCH_RESULTS table  is allocated and returned to the caller in *rethResults.

FT_SEARCH_SET_COLL not set,  FT_SEARCH_RET_IDTABLE set:
        An ID Table is allocated and returned to the caller in *rethResults.

FT_SEARCH_SET_COLL set,          FT_SEARCH_RET_IDTABLE not set:
        An FT_SEARCH_RESULTS table is returned through the collection.  
        NULLHANDLE is returned in *rethResults.

FT_SEARCH_SET_COLL set,          FT_SEARCH_RET_IDTABLE set:
        An FT_SEARCH_RESULTS table is returned through the collection.  
        An ID Table is allocated and returned to the caller in *rethResults.

Except in the case where FT_SEARCH_SET_COLL set, and FT_SEARCH_RET_IDTABLE is not set, rethResults will be NULLHANDLE if no documents are returned from FTSearchExt.  

 When FTSearchExt returns a non-NULLHANDLE in *rethResults, use OSLock to obtain a pointer to the returned results.  After processing the returned results, use OSUnlockObject to unlock the pointer and OSMemFree to free the memory associated with this handle.

retNumHits  -  Actual number of documents found for this search.  This number may be greater than retNumDocs.
Before any further processing, be sure to check the value of this field after calling the API.  If no document is returned (retNumHits==0), do not lock the rethResults because this handle will be a NULLHANDLE.

**Sample Usage :**
```
  /* open a search handle */
   if (error = FTOpenSearch(&hSearch))
	goto errorReturn;
  
   /* Execute Domain search */
   /* Let's specify returning 20 documents per page */
   Start=1;
   Count=20;
   retNumHits=999;
   whilte ( Start <= retNumHits ) {
      error = FTSearchExt (hDB,                 /* database handle */
                     &hSearch,                  /* pointer to previously 
allocated search handle */
                     (HCOLLECTION) NULLHANDLE,  /* no collection specified - 
query all docs */
                     Query,                     /* query string */
                     FT_SEARCH_EXT_DOMAIN |     /* Domain search */  
                     FT_SEARCH_EXT_DATABASE |   /* search databases     */
                     FT_SEARCH_EXT_FILESYSTEM | /* search the file systems */
           FT_SEARCH_EXT_RET_URL ,    /* return URL-format result */
                     0,                         /* maximum number of docs to 
return; 0 = unlimited */
                     NULLHANDLE,                /* no refining IDTABLE   */
                     &dwRetDocs,                /* returned number of docs */
                     NULL,                      /* reserved */
                     &hSearchResults,
                     &retNumHits,               /* number of total hits  */
                     Start,                     /* Starting document for the 
current paged result */
                     Count,                     /* number of hits to be 
returned for the current page */
                     Arg,NULL);   
      if (error)
         goto CloseSearch;
   
      if (retNumHits == 0)   /* no document returned */
         goto CloseSearch;

      /* obtain a pointer to the search results */
      pSearchResults = OSLock (FT_SEARCH_RESULTS, hSearchResults);

      /* continue only if FT_RESULTS_URL flag is on. */
      if (!(pSearchResults->Flags & FT_RESULTS_URL))
    goto UnlockSearch;
      
      /* calc. pointer to FT_SEARCH_URL_RESULTS structure */ 
      pSearchURLResults=(FT_SEARCH_URL_RESULTS *)(((char 
*)pSearchResults)+sizeof(FT_SEARCH_RESULTS));
    
      /* calc. pointer to FT_SEARCH_URL_RESULT_ENTRY structure */   
      pSearchURLResultEntry=(FT_SEARCH_URL_RESULT_ENTRY *)(((char 
*)pSearchURLResults)+sizeof(FT_SEARCH_URL_RESULTS));

      /* calc. pointer to the start of the variable data following */
      /* FT_SEARCH_URL_RESULT_ENTRY.                               */ 
      realData=(char *) ((char *)pSearchURLResultEntry+ 
(pSearchResults->NumHits*sizeof(FT_SEARCH_URL_RESULT_ENTRY)));

      /* retrieve variable data.  After each loop, bump up 
pSearchURLResultEntry to point */
      /* to the next occurrance of FT_SEARCH_URL_RESULT_ENTRY.  */
      
      page++;

      for (i=0;i<pSearchResults->NumHits;i++,pSearchURLResultEntry++)
     {
            printf("** RESULT %d (of Page %d)...<%s>\n",i+1,page,
               pSearchURLResultEntry->UrlLength?"filesystem":"Notes document");

  if (pSearchURLResultEntry->UrlLength!=0)  /* file system result */
  {
     printf("Name: ");
	         /* print the variable data and advance realData to */
          /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->UrlLength); 
	 }
  if (pSearchURLResultEntry->ServerHintLength!=0)
  {
     printf("Server: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->ServerHintLength); 
  }
  if (pSearchURLResultEntry->DbTitleLength!=0)
  {
     printf("DB Title: ");
      /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->DbTitleLength); 
  }
  if (pSearchURLResultEntry->DbCategoriesLength!=0)
  {
     printf("DB Categories: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, 
pSearchURLResultEntry->DbCategoriesLength); 
  }
  if (pSearchURLResultEntry->HeadingLength!=0)
  {
     printf("Heading: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->HeadingLength); 
  }
  if (pSearchURLResultEntry->DocSummaryLength!=0)
  {
     printf("Summary: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->DocSummaryLength); 
  }
  if (pSearchURLResultEntry->DocTitleLength!=0)
  {
     printf("Doc Title: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
	    PrintString((char **)&realData, 
pSearchURLResultEntry->DocTitleLength); 
  }
  if (pSearchURLResultEntry->DocAuthorLength!=0)
  {
     printf("Doc Author: ");
	    /* print the variable data and advance realData to */
	    /* point to the beginning of the next variable. */
     PrintString((char **)&realData, pSearchURLResultEntry->DocAuthorLength); 
  }
 }  /* for */
        
UnlockSearch:
      OSUnlockObject(hSearchResults);
      OSMemFree (hSearchResults);

      Start+=Count;      /* proceed to the next page */

   }  /* while */

CloseSearch:
   error = FTCloseSearch(hSearch);
```
**See Also :**
[FTCloseSearch](D:/md_files/FTCloseSearch.md)
[FTOpenSearch](D:/md_files/FTOpenSearch.md)
[FTSearch](D:/md_files/FTSearch.md)
[FT_SEARCH_RESULTS](D:/md_files/FT_SEARCH_RESULTS.md)
[FT_SEARCH_RESULT_ENTRY](D:/md_files/FT_SEARCH_RESULT_ENTRY.md)
[FT_SEARCH_URL_RESULTS](D:/md_files/FT_SEARCH_URL_RESULTS.md)
[FT_SEARCH_URL_RESULT_ENTRY](D:/md_files/FT_SEARCH_URL_RESULT_ENTRY.md)
---
