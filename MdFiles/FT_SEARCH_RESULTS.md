




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Data Type : Full Text Search**



**FT\_SEARCH\_RESULTS** **-** Search
results returned from FTSearch or FTSearchExt.


**----------------------------------------------------------------------------------------------------------**



**#include
<ft.h>**



**Definition :**



typedef struct {  

   DWORD NumHits;   /\* Number of search hits following \*/  

   WORD  Flags;     /\* see FT\_RESULTS\_xxx \*/  

   WORD  VarLength; /\* Length of variable strings after


                      
FT\_SEARCH\_RESULT\_ENTRY array, or


                      
FT\_SEARCH\_URL\_RESULT\_ENTRY entries \*/


  

/\* Followed by an array of 


       NoteIDs, 


      
FT\_SEARCH\_RESULT\_ENTRY's, OR


      
FT\_SEARCH\_URL\_RESULTS and FT\_SEARCH\_URL\_RESULT\_ENTRY's \*/


  

/\* Followed by a BYTE array of scores (optional)


   OR in the case of
catalog index search (searches done on a search 


   site database that
has a multi-database index), the following are the


   Server, Title,
Categories, Heading and Summary string fields \*/


  

} FT\_SEARCH\_RESULTS;


 


**Description :**



This
structure contains the results of a full text search that is returned from
FTSearch or FTSearchExt.


 


If the Flags
member of this structure has the FT\_RESULTS\_EXPANDED bit set, then an array of
FT\_SEARCH\_RESULT\_ENTRY structures will follow the FT\_SEARCH\_RESULTS structure.


 


If the Flags
memer of this structure has the FT\_RESULTS\_URL bit set, then the returned
results consist of one FT\_SEARCH\_RESULTS structure, one FT\_SEARCH\_URL\_RESULTS
structure and an array of FT\_SEARCH\_URL\_RESULT\_ENTRY structures.  This is only
supported by the FTSearchExt API.  

  

If the Flags member of this strucuture has the  FT\_RESULTS\_SCORES bit set, then
an array of bytes containing the relevancy scores will follow the array of
NoteIDs and be parallel to it.  Relevancy scores range from 0 to 100, with 100
being the most relevant.  Otherwise, relevancy scores are not returned.


 **See Also :**


**[FTSearch](FTSearch.md)**


**[FTSearchExt](FTSearchExt.md)**


**[FT\_RESULTS\_xxx](FT_RESULTS_xxx.md)**


**[FT\_SEARCH\_RESULT\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/59F65E1E7DFF89A98525635F0080BA2A)**


**[FT\_SEARCH\_URL\_RESULTS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FF9018CF30C961948525667800511EC8)**


**[FT\_SEARCH\_URL\_RESULT\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/96679A1594D788138525667800517309)**



----------------------------------------------------------------------------------------------------------


 





