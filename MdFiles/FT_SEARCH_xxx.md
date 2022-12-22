




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




 


**Symbolic Value : Full Text Search**



**FT\_SEARCH\_xxx** **-** Full text
search options.


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**


 **Symbolic Values :**      FT\_SEARCH\_SET\_COLL     -  Associate an FT\_SEARCH\_RESULTS
table with the collection handle that is specified as the third argument in
FTSearch or FTSearchExt. Not applicable to searches done on a search site
database that has a multi-database index.  

  

      FT\_SEARCH\_RET\_IDTABLE            -  Return search results in an ID table.
A handle to the ID Table is returned in \*rethResults (the dereferenced tenth
parameter) of FTSearch or FTsearchExt. Not applicable to searches done on a
search site database that has a multi-database index.  

  

      FT\_SEARCH\_NUMDOCS\_ONLY      -  Return number of hits only, do not return
the documents. The number of hits is returned in \*retNumDocs (the dereferenced
eighth parameter) of FTSearch or FTSearchExt. The rethResults parameter of
FTSearch or FTSearchExt must be a valid address and will point to NULLHANDLE
after the API call. This option forces the FT\_SEARCH\_SCORES,
FT\_SEARCH\_RET\_IDTABLE, FT\_SEARCH\_SORT\_DATE, FT\_SEARCH\_SORT\_ASCEND, and
FT\_SEARCH\_EXT\_RET\_URL options to be ignored and therefore should not be or'd
with them.  

  

      FT\_SEARCH\_REFINE          -  Refine the query using the specified ID
Table.  

  

      FT\_SEARCH\_SCORES       -  Return document scores. This is analogous to
selecting the Sorted by Relevance option (the default) in the Notes user
interface, Search Options dialog box. Scores range from 0 to 100, with 100
being the most relevant. Not applicable to searches done on a search site
database that has a multi-database index.  

  

      FT\_SEARCH\_SORT\_DATE   -  Sort results by date in descending order.  

  

      FT\_SEARCH\_SORT\_ASCEND         -  Sort results in ascending order.  

  

      FT\_SEARCH\_TOP\_SCORES            -  Use Limit argument and return the
first Limit number of documents.  

  

      FT\_SEARCH\_STEM\_WORDS          -  Stem words in this query. Searching is
done on the query word and variants of the query word. For example, if the
query word is "print," documents that contain the words print,
prints, printed, printer, and printing are found. In order to use this option,
the full text search index must have been built with either the Notes user
interface or with an API program with the FT\_INDEX\_STEM\_INDEX option.  

  

      FT\_SEARCH\_THESAURUS\_WORDS           -  Thesaurus words in this query.  

  

      FT\_SEARCH\_FUZZY            -  Perform fuzzy search. By using this option,
users could find a document containing the misspelled word
"trasnpose" when doing the search query "transpose".  

  

      FT\_SEARCH\_EXT\_RET\_URL           -  Return url-based results. Supported by
the FTSearchExt only.  

  

      FT\_SEARCH\_SORT\_DATE\_CREATED        -  Sort by created date (default is to
sort by modified date).  

  

      FT\_SEARCH\_EXT\_DOMAIN             -  This is a domain search. Supported by
the FTSearchExt only.  

  

      FT\_SEARCH\_EXT\_FILESYSTEM     -  Search the filesystem index (Domain
Search only). This option is only supported by the FTSearchExt. It should be
used in conjunction with the FT\_SEARCH\_EXT\_DOMAIN option.  

  

      FT\_SEARCH\_EXT\_DATABASE        -  Search the database index (Domain Search
only). This option is only supported by the FTSearchExt. It should be used in
conjunction with the FT\_SEARCH\_EXT\_DOMAIN option.  

  




**Description :**



These values
define the options you may specify in the Options parameter to FTSearch or
FTSearchExt when performing a full text search in a database or the domain
search against a Domain catalog.  These options may be combined by
bitwise-ORing them together.


 **See Also :**


**[FTSearch](FTSearch.md)**


**[FTSearchExt](FTSearchExt.md)**



----------------------------------------------------------------------------------------------------------


 





