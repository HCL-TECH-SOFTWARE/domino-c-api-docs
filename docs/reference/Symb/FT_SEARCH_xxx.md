##### Symbolic Value : Full Text Search
##### FT_SEARCH_xxx - Full text search options.
---
```
#include <ft.h>
```

**Symbolic Values :**

	FT_SEARCH_SET_COLL	  -  Associate an FT_SEARCH_RESULTS table with the collection handle that is specified as the third argument in FTSearch or FTSearchExt. Not applicable to searches done on a search site database that has a multi-database index.

	FT_SEARCH_RET_IDTABLE	  -  Return search results in an ID table. A handle to the ID Table is returned in *rethResults (the dereferenced tenth parameter) of FTSearch or FTsearchExt. Not applicable to searches done on a search site database that has a multi-database index.

	FT_SEARCH_NUMDOCS_ONLY	  -  Return number of hits only, do not return the documents. The number of hits is returned in *retNumDocs (the dereferenced eighth parameter) of FTSearch or FTSearchExt. The rethResults parameter of FTSearch or FTSearchExt must be a valid address and will point to NULLHANDLE after the API call. This option forces the FT_SEARCH_SCORES, FT_SEARCH_RET_IDTABLE, FT_SEARCH_SORT_DATE, FT_SEARCH_SORT_ASCEND, and FT_SEARCH_EXT_RET_URL options to be ignored and therefore should not be or'd with them.

	FT_SEARCH_REFINE	  -  Refine the query using the specified ID Table.

	FT_SEARCH_SCORES	  -  Return document scores. This is analogous to selecting the Sorted by Relevance option (the default) in the Notes user interface, Search Options dialog box. Scores range from 0 to 100, with 100 being the most relevant. Not applicable to searches done on a search site database that has a multi-database index.

	FT_SEARCH_SORT_DATE	  -  Sort results by date in descending order.

	FT_SEARCH_SORT_ASCEND	  -  Sort results in ascending order.

	FT_SEARCH_TOP_SCORES	  -  Use Limit argument and return the first Limit number of documents.

	FT_SEARCH_STEM_WORDS	  -  Stem words in this query. Searching is done on the query word and variants of the query word. For example, if the query word is "print," documents that contain the words print, prints, printed, printer, and printing are found. In order to use this option, the full text search index must have been built with either the Notes user interface or with an API program with the FT_INDEX_STEM_INDEX option.

	FT_SEARCH_THESAURUS_WORDS	  -  Thesaurus words in this query.

	FT_SEARCH_FUZZY	  -  Perform fuzzy search. By using this option, users could find a document containing the misspelled word "trasnpose" when doing the search query "transpose".

	FT_SEARCH_EXT_RET_URL	  -  Return url-based results. Supported by the FTSearchExt only.

	FT_SEARCH_SORT_DATE_CREATED	  -  Sort by created date (default is to sort by modified date).

	FT_SEARCH_EXT_DOMAIN	  -  This is a domain search. Supported by the FTSearchExt only.

	FT_SEARCH_EXT_FILESYSTEM	  -  Search the filesystem index (Domain Search only). This option is only supported by the FTSearchExt. It should be used in conjunction with the FT_SEARCH_EXT_DOMAIN option.

	FT_SEARCH_EXT_DATABASE	  -  Search the database index (Domain Search only). This option is only supported by the FTSearchExt. It should be used in conjunction with the FT_SEARCH_EXT_DOMAIN option.


**Description :**

These values define the options you may specify in the Options parameter to FTSearch or FTSearchExt when performing a full text search in a database or the domain search against a Domain catalog.  These options may be combined by bitwise-ORing them together.


**See Also :**
[FTSearch](/domino-c-api-docs/reference/Func/FTSearch)
[FTSearchExt](/domino-c-api-docs/reference/Func/FTSearchExt)
---
