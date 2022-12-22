




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



**CDQUERYTOPIC** **-** Verity Topic
query CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG Header;


   DWORD dwFlags;      
/\* Flags \*/  

   WORD wTopicQueryLen; /\* Length of topic query \*/  

   WORD wDataLen;       /\* Length of data \*/  

           /\* Topic query follows \*/  

           /\* Data follows \*/  

    } CDQUERYTOPIC;


 


**Description :**



Domino and
Notes incorporate a search engine provided by Verity, Inc.  Search queries for
the Verity search engine are stored in CDQUERYTOPIC records in fields of type
TYPE\_QUERY, usually the query field of an Agent.  The query is used by the
Verity search engine to select the documents to be operated on by the Agent. 
This record consists of this data structure followed by the query topic and
data for the search.  The fields in this structure are:


 


Header             Defines
this composite data item as a CDQUERYTOPIC item.


dwFlags                       Reserved; 
must be 0.


wTopicQueryLen           Length
of query topic.


wDataLen                     Length
of query data.


 


This
structure is followed by the query topic, then the query data.


 




----------------------------------------------------------------------------------------------------------


 





