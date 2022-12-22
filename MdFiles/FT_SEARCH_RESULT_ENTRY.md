




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




**Initial Release 4.5**



**Data Type : Full Text Search**



**FT\_SEARCH\_RESULT\_ENTRY** **-** Search
results that may be returned from FTSearch.


**----------------------------------------------------------------------------------------------------------**



**#include
<ft.h>**



**Definition :**



typedef struct {  

   DBID     ReplicaID;  

   UNID     Unid;  

   UNID     ViewUnid;       

   TIMEDATE ModifiedTime;     /\* Last modified time of note \*/  

   WORD     Flags;            /\* see FT\_RESULT\_ENTRY\_xxx \*/  

   WORD     ServerHintLength; /\* Length of Server hint \*/  

   WORD     TitleLength;      /\* Length of Databaes Title \*/  

   WORD     CategoriesLength; /\* Length of Database Categories \*/  

   WORD     HeadingLength;    /\* Length of View Column Heading \*/  

   WORD     SummaryLength;    /\* Length of View Summary \*/  

   BYTE     Score;                         

   BYTE     Spare;                         

} FT\_SEARCH\_RESULT\_ENTRY;


 


**Description :**



FTSearch
returns an FT\_SEARCH\_RESULTS structure.  If the Flags member of the
FT\_SEARCH\_RESULTS structure has the FT\_RESULTS\_EXPANDED bit set, then an array
of FT\_SEARCH\_RESULT\_ENTRY structures will follow the FT\_SEARCH\_RESULTS
structure.  This will occur with searches done on a search site database that
has a multi-database index.


 


The Server,
Title, Categories, Heading and Summary string fields follow the
FT\_SEARCH\_RESULT\_ENTRY array.


   


 **See Also :**


**[FTSearch](FTSearch.md)**


**[FT\_SEARCH\_RESULTS](FT_SEARCH_RESULTS.md)**


**[FT\_RESULTS\_xxx](FT_RESULTS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





