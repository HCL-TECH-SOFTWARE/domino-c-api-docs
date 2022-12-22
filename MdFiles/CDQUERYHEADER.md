




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




**Initial Release 4.0**



**Data Type : Agents; Composite Data**



**CDQUERYHEADER** **-** Query header
CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   BSIG Header;  

   DWORD dwFlags; /\* Flags for query \*/  

} CDQUERYHEADER;


 


**Description :**



The on-disk
format for a query consists of a query header structure followed by a number of
query term structures.  The CDQUERYHEADER record is located at the beginning of
a data item of TYPE\_QUERY, usually the query field of an Agent.  The fields in
this structure are:


 


Header Defines
this composite data item as a CDQUERYHEADER item.


dwFlags           Query
flags (see QUERY\_FLAG\_xxx).


 


 **See Also :**


**[QUERY\_FLAG\_xxx](QUERY_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





