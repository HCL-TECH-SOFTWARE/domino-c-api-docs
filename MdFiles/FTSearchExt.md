




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 5.0**



**Function : Full Text Search**



**FTSearchExt** **- Extended
full text search**


**----------------------------------------------------------------------------------------------------------**



**#include <ft.h>**



STATUS
LNPUBLIC **FTSearchExt(**  

      DBHANDLE  hDB,  

      DHANDLE far \*phSearch,  

      HCOLLECTION  hColl,  

      char far \*Query,  

      DWORD  Options,  

      WORD  Limit,  

      DHANDLE  hIDTable,  

      DWORD far \*retNumDocs,  

      DHANDLE far \*Reserved,  

      DHANDLE far \*rethResults,  

      DWORD far \*retNumHits,  

      DWORD  Start,  

      WORD  Count,  

      WORD  Arg,  

      HANDLE  hNames**);**



**Description :**



FTSearchExt
is a superset of FTSearch.  Calling it with all new parameters and flags clear
will result in the same behavior as an FTSearch call.   In addition to the
function performed  by the FTSearch, it supports Domain search, and URL-style
and paged results.


 


For
efficiency, use the **Start**, **Count** and **Arg** parameters to
gain the paged results.  FtSearchExt will return a **Count** of results at a
time.  It is the application program's responsibility to execute FTSearchExt
multiple times by varying the **Start** value to read in all the hits.  If
the **Start** and **Count** are zero, FTSearchExt will turn off the
"paged result" feature.


 


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

  

Options  -  Search options (see FT\_SEARCH\_XXX).  Options may be or'd together.  

  

Limit  -  Maximum number of documents to return.  Use 0 to return the maximum
number of results for the search.  For more information about specifying the
maximum number of results in a full text search, see the Domino Administration
Help database.  

  

hIDTable  -  Handle to an ID table to further refine the search.  Use
NULLHANDLE if this is not required.  

  

Start  -  The starting document number for the paged result.  For the non-paged
result, set this item to 0.  For the paged result, set this item to a non-zero
number.  

  

Count  -  Number of documents to return for the paged result.  

  

Arg  -  Paged results additional argument.  

  

hNames  -  User's name list (NAMES\_LIST) or NULL  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_FT\_NOMATCHES - No documents were found by this search.  Arguments used in a
previous call to FTSearchExt remain valid.   

  

ERR\_xxx - Error returned by lower level C API functions. Call OSLoadString to
interpret the code.  

  

  

phSearch  -  This handle may be modified by the FTSearchExt API.  

  

retNumDocs  -  Number of documents returned in the results.  

  

If no documents are found, the function will return ERR\_FT\_NOMATCHES and
arguments used in a previous call to FTSearchExt remain valid.   

  

Reserved  -  Reserved for future use.  Pass in NULL for this parameter.  

  

rethResults  -  Pointer to returned handle to the search results.    

  

Depending on the options set in the Options argument, the search results are
either in an ID Table, or in an FT\_SEARCH\_RESULTS structure (see
FT\_RESULTS\_XXX):  

  

FT\_SEARCH\_SET\_COLL not set,  FT\_SEARCH\_RET\_IDTABLE not set:  

        An FT\_SEARCH\_RESULTS table  is allocated and returned to the caller in
\*rethResults.  

  

FT\_SEARCH\_SET\_COLL not set,  FT\_SEARCH\_RET\_IDTABLE set:  

        An ID Table is allocated and returned to the caller in \*rethResults.  

  

FT\_SEARCH\_SET\_COLL set,          FT\_SEARCH\_RET\_IDTABLE not set:  

        An FT\_SEARCH\_RESULTS table is returned through the collection.    

        NULLHANDLE is returned in \*rethResults.  

  

FT\_SEARCH\_SET\_COLL set,          FT\_SEARCH\_RET\_IDTABLE set:  

        An FT\_SEARCH\_RESULTS table is returned through the collection.    

        An ID Table is allocated and returned to the caller in \*rethResults.  

  

Except in the case where FT\_SEARCH\_SET\_COLL set, and FT\_SEARCH\_RET\_IDTABLE is
not set, rethResults will be NULLHANDLE if no documents are returned from
FTSearchExt.    

  

 When FTSearchExt returns a non-NULLHANDLE in \*rethResults, use OSLock to
obtain a pointer to the returned results.  After processing the returned
results, use OSUnlockObject to unlock the pointer and OSMemFree to free the
memory associated with this handle.  

  

retNumHits  -  Actual number of documents found for this search.  This number
may be greater than retNumDocs.  

Before any further processing, be sure to check the value of this field after
calling the API.  If no document is returned (retNumHits==0), do not lock the
rethResults because this handle will be a NULLHANDLE.  

  




 **Sample Usage :**


  /\* open a search
handle \*/


   if
(error = FTOpenSearch(&hSearch))


        goto
errorReturn;  

  


   /\*
Execute Domain search \*/


   /\* Let's
specify returning 20 documents per page \*/


   Start=1;


  
Count=20;


  
retNumHits=999;


   whilte (
Start <= retNumHits ) {  

      error = FTSearchExt (hDB,                 /\* database handle \*/  

                     &hSearch,                  /\* pointer to previously
allocated search handle \*/  

                     (HCOLLECTION) NULLHANDLE,  /\* no collection specified -
query all docs \*/  

                     Query,                     /\* query string \*/  

                     FT\_SEARCH\_EXT\_DOMAIN |     /\* Domain search \*/ 


                    
FT\_SEARCH\_EXT\_DATABASE |   /\* search databases     \*/


                    
FT\_SEARCH\_EXT\_FILESYSTEM | /\* search the file systems \*/  

                        FT\_SEARCH\_EXT\_RET\_URL ,    /\* return URL-format result
\*/  

                     0,                         /\* maximum number of docs to
return; 0 = unlimited \*/  

                     NULLHANDLE,                /\* no refining IDTABLE   \*/  

                     &dwRetDocs,                /\* returned number of docs
\*/  

                     NULL,                      /\* reserved \*/  

                     &hSearchResults,


                     &retNumHits,              
/\* number of total hits  \*/


                    
Start,                     /\* Starting document for the current paged result \*/


                    
Count,                     /\* number of hits to be returned for the current
page \*/


                    
Arg,NULL);     

      if (error)  

         goto CloseSearch;  

   


      if
(retNumHits == 0)   /\* no document returned \*/


        
goto CloseSearch;


  

      /\* obtain a pointer to the search results \*/  

      pSearchResults = OSLock (FT\_SEARCH\_RESULTS, hSearchResults);


 


      /\*
continue only if FT\_RESULTS\_URL flag is on. \*/  

      if (!(pSearchResults->Flags & FT\_RESULTS\_URL))  

           goto UnlockSearch;  

          


      /\*
calc. pointer to FT\_SEARCH\_URL\_RESULTS structure \*/   

      pSearchURLResults=(FT\_SEARCH\_URL\_RESULTS \*)(((char
\*)pSearchResults)+sizeof(FT\_SEARCH\_RESULTS));  

    


      /\*
calc. pointer to FT\_SEARCH\_URL\_RESULT\_ENTRY structure \*/     

      pSearchURLResultEntry=(FT\_SEARCH\_URL\_RESULT\_ENTRY \*)(((char
\*)pSearchURLResults)+sizeof(FT\_SEARCH\_URL\_RESULTS));


 


      /\*
calc. pointer to the start of the variable data following \*/


      /\*
FT\_SEARCH\_URL\_RESULT\_ENTRY.                               \*/ 


     
realData=(char \*) ((char \*)pSearchURLResultEntry+ (pSearchResults->NumHits\*sizeof(FT\_SEARCH\_URL\_RESULT\_ENTRY)));


 


      /\*
retrieve variable data.  After each loop, bump up pSearchURLResultEntry to
point \*/


      /\* to
the next occurrance of FT\_SEARCH\_URL\_RESULT\_ENTRY.  \*/


      


     
page++;


 


      for
(i=0;i<pSearchResults->NumHits;i++,pSearchURLResultEntry++)  

           {


           
printf("\*\* RESULT %d (of Page %d)...<%s>\n",i+1,page,


              
pSearchURLResultEntry->UrlLength?"filesystem":"Notes
document");


  

               if (pSearchURLResultEntry->UrlLength!=0)  /\* file system
result \*/  

               {  

                  printf("Name: ");


                
/\* print the variable data and advance realData to \*/


           /\*
point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData, pSearchURLResultEntry->UrlLength);



               }  

               if (pSearchURLResultEntry->ServerHintLength!=0)  

               {  

                  printf("Server: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->ServerHintLength);   

               }  

               if (pSearchURLResultEntry->DbTitleLength!=0)  

               {  

                  printf("DB Title: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->DbTitleLength);   

               }  

               if (pSearchURLResultEntry->DbCategoriesLength!=0)  

               {  

                  printf("DB Categories: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->DbCategoriesLength);   

               }  

               if (pSearchURLResultEntry->HeadingLength!=0)  

               {  

                  printf("Heading: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->HeadingLength);   

               }  

               if (pSearchURLResultEntry->DocSummaryLength!=0)  

               {  

                  printf("Summary: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->DocSummaryLength);   

               }  

               if (pSearchURLResultEntry->DocTitleLength!=0)  

               {  

                  printf("Doc Title: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/


                 
PrintString((char \*\*)&realData, pSearchURLResultEntry->DocTitleLength);   

               }  

               if (pSearchURLResultEntry->DocAuthorLength!=0)  

               {  

                  printf("Doc Author: ");


                 
/\* print the variable data and advance realData to \*/


                 
/\* point to the beginning of the next variable. \*/  

                  PrintString((char \*\*)&realData,
pSearchURLResultEntry->DocAuthorLength);   

               }  

        }  /\* for \*/  

        


UnlockSearch:


     
OSUnlockObject(hSearchResults);  

      OSMemFree (hSearchResults);


 


     
Start+=Count;      /\* proceed to the next page \*/


 


   }  /\*
while \*/


  

CloseSearch:


   error =
FTCloseSearch(hSearch);


 **See Also :**


**[FTCloseSearch](FTCloseSearch.md)**


**[FTOpenSearch](FTOpenSearch.md)**


**[FTSearch](FTSearch.md)**


**[FT\_SEARCH\_RESULTS](FT_SEARCH_RESULTS.md)**


**[FT\_SEARCH\_RESULT\_ENTRY](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/59F65E1E7DFF89A98525635F0080BA2A)**


**[FT\_SEARCH\_URL\_RESULTS](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/FF9018CF30C961948525667800511EC8)**


**[FT\_SEARCH\_URL\_RESULT\_ENTRY](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/96679A1594D788138525667800517309)**



----------------------------------------------------------------------------------------------------------


 





