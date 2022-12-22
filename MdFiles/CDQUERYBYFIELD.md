




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



**CDQUERYBYFIELD** **-** Query by
Field query CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG Header;  

   DWORD dwFlags;         /\* flags (QUERYBYFIELD\_FLAG\_xxx) \*/  

   WORD wDataType;        /\* data type of field to search \*/  

   WORD wOperator;        /\* operation QUERYBYFIELD\_OP\_xxx \*/  

   TIMEDATE Date1;        /\* first operand \*/  

   TIMEDATE Date2;        /\* second operand \*/  

   ALIGNED\_NUMBER Number1; /\* first operand \*/  

   ALIGNED\_NUMBER Number2; /\* second operand \*/


   WORD wFieldNameLen;    /\*
length of field name \*/  

   WORD wValueLen;        /\* length of value \*/


           /\* field
name follows \*/


           /\* value
follows \*/


} CDQUERYBYFIELD;


 


**Description :**



Field-level
query information is stored in a CDQUERYBYFIELD record in fields of type
TYPE\_QUERY, usually the query field of an Agent.  The query field of an Agent
is used to select documents to be operated on by the Agent.  This record
consists of this data structure, followed by the field name and any value for
the field query (in packed format).  The fields in this structure are:


 


Header                         Defines
this composite data item as a CDQUERYBYFIELD item.


dwFlags                       Field
query flags (see QUERYBYFIELD\_FLAG\_xxx).


wDataType                   Type
of field to search (see TYPE\_xxx).


wOperator                    Field
query operation (see QUERYBYFIELD\_OP\_xxx).


Date1                           First
TIMEDATE value for comparison.


Date2                           Second
TIMEDATE value defining a range.


Number1                      First
ALIGNED\_NUMBER value for comparison.


Number2                      Second
ALIGNED\_NUMBER value defining a range.


wFieldNameLen            Length
of the field name.


wValueLen                    Length
of the value.


 


This
structure is followed by a packed string containing the field name and any
field value.


 **See Also :**


**[QUERYBYFIELD\_FLAG\_xxx](QUERYBYFIELD_FLAG_xxx.md)**


**[QUERYBYFIELD\_OP\_xxx](QUERYBYFIELD_OP_xxx.md)**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





