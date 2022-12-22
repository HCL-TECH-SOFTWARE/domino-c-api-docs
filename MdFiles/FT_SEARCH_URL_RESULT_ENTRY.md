




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



**Data Type : Full Text Search**



**FT\_SEARCH\_URL\_RESULT\_ENTRY** **-** Result entry
returned by FTSearchExt when FT\_RESULTS\_URL set.


**----------------------------------------------------------------------------------------------------------**



**#include
<ft.h>**



**Definition :**



typedef struct {  

   TIMEDATE CreatedTime;        /\* Creation time of note \*/  

   TIMEDATE ModifiedTime;       /\* Last modified time of note \*/  

   WORD     Flags;              /\* Flags \*/


   WORD    
UrlLength;          /\* Length of url string, or 0 if


                                  
notes link \*/  

   DBID     ReplicaID;          /\* replica id \*/  

   UNID     Unid;               /\* unid of note \*/  

   UNID     ViewUnid;           /\* unid of view containing note \*/  

   WORD     ServerHintLength;   /\* Length of Server hint \*/


   WORD    
DbTitleLength;      /\* Length of Database Title \*/  

   WORD     DbCategoriesLength; /\* Length of Database Categories \*/  

   WORD     HeadingLength;      /\* Length of View Column Heading \*/  

   WORD     DocSummaryLength;   /\* Length of Document Summary \*/  

   WORD     DocTitleLength;     /\* Length of Document Title \*/  

   WORD     DocAuthorLength;    /\* Length of Document Author \*/  

   BYTE     Score;              /\* Relevance score \*/  

   BYTE     Spare;           


}
FT\_SEARCH\_URL\_RESULT\_ENTRY;


 


**Description :**



FTSearchExt
returns an FT\_SEARCH\_RESULTS structure.  If the Flags member of the


FT\_SEARCH\_RESULTS
structure has the FT\_RESULTS\_URL bit set, the following structures will


be
following:


 


one
FT\_SEARCH\_URL\_RESULTS structure,


 


an array of
FT\_SEARCH\_URL\_RESULT\_ENTRY structures 


 


an array of
following variable length data (each set of variable data corresponds to each
FT\_SEARCH\_URL\_RESULT\_ENTRY appeared above):


url string


server hint
string


dbtitle
string


dbcategories
strings


heading
string


doc summary
string


doc title
string


doc author
string


 


 


If there is
a nonzero UrlLength, this is for a "foreign" url and the string
should be used.  Otherwise the ReplicaID/Unid/ViewUnid/ServerHint represent the
hit.


 




----------------------------------------------------------------------------------------------------------


 





