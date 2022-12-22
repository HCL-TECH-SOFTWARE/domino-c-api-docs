




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"MS Mincho";
 panose-1:2 2 6 9 4 2 5 8 3 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
@font-face
 {font-family:"\@MS Mincho";
 panose-1:2 2 6 9 4 2 5 8 3 4;}
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




**Initial Release 8.5.2**



**Function : Dir**



**DirCtxSearchPersonsByName** **- Get one
or more person entries by name.**


**----------------------------------------------------------------------------------------------------------**



**#include <dirctx.h>**



STATUS
LNPUBLIC **DirCtxSearchPersonsByName(**  

      DIRCTX  hCtx,  

      const char \*name,  

      const char \*items,  

      WORD  numItems,  

      DIRCOLLECTION \*hCollection**);**



**Description :**



Get one or
more person entries by name.


 


**Parameters :**



Input :  

hCtx  -  Directory context for this operation.  

  

name  -  Name of person(s) to search for. This may be the Notes distinguished
name, abbreviated name, common name, firstname, lastname, shortname, or
internet address of the person desired. Must not be NULL  

  

items  -  A list of specific items, separated by a null character, to be
returned. Or, if all items are desired the caller may specify
DIR\_ITEMS\_ALL\_DOMINO. If NULL is specified then only the Notes DN is returned
for each match in hCollection, and the number of matches are returned in
numMatches.   

The order of the items in the list determines the index position that is
specified in subsequent calls to DirEntryGetItem() in order to get the values
of the items.   

Note that Domino ad hoc items must be asked for specifically. This is so that
the existing buffer management code does not have to change significantly. For
efficiency and speed this code depends on knowing all the items to be placed in
the buffer when the first match is added. This is difficult or at least
inefficient if there are multiple matches and the ad-hoc attributes differ
between some/all the matches.  

  

numItems  -  The number of items in the list of items to be returned. Specify 1
if one of the DIR\_ITEMS\_ values is specified. Specify 0 if items is NULL.  

  




Output :  

(routine)  -  Status code:   

NOERROR on success.   

An ERR status on failure indicating the problem.   

  

  

hCollection  -  Handle to an allocated collection of entries that match the
search criteria. If there are no matching entries (i.e. GetNumEntries()==0)
then the return value for hCollection is NULLDIRCOLLECTION.   

Callers must not call DirEntryFree() on the returned directory entry objects!
They will be indirectly freed by calling DirCollectionFree().  

  




 **See Also :**


**[DirCtxSearchByName](DirCtxSearchByName.md)**


**[DirCtxSearchDominoGroupsByName](DirCtxSearchDominoGroupsByName.md)**


**[DirCtxSearchDominoPersonsByName](DirCtxSearchDominoPersonsByName.md)**


**[DirCtxSearchGroupsByName](DirCtxSearchGroupsByName.md)**



----------------------------------------------------------------------------------------------------------


 





