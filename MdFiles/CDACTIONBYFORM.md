




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



**CDACTIONBYFORM** **-** Form action
CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;  

   WORD  wFieldCount;  /\* Number of fields that follow \*/  

   WORD  wFormNameLen; /\* Length of form name \*/


           /\*
ODS\_ASSISTFIELDSTRUCTs follow \*/


           /\* Form name
follows \*/  

} CDACTIONBYFORM;


 


**Description :**



Actions
associated with a form are stored in a CDACTIONBYFORM record in fields of type
TYPE\_ACTION, usually the action field of an Agent.  This record consists of
this data structure, followed by field actions specified by
ODS\_ASSISTFIELDSTRUCT records, then followed by the name of the form.  The
fields in this structure are:


 


Header             Defines
this composite data item as a CDACTIONBYFORM item.


dwFlags                       Form
action flags (see ACTIONBYFIELD\_OP\_xxx or QUERYBYFIELD\_OP\_xxx).


wFieldCount                  Number
of fields that follow (number of ODS\_ASSISTFIELDSTRUCT records).


wFormNameLen            Length
of the form name.


 


This
structure is followed by the ODS\_ASSISTFIELDSTRUCT structures, then a packed
string containing the form name.


 **See Also :**


**[ACTIONBYFIELD\_OP\_xxx](ACTIONBYFIELD_OP_xxx.md)**


**[ODS\_ASSISTFIELDSTRUCT](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A3E6C6BBE236009C852562610053DF95)**



----------------------------------------------------------------------------------------------------------


 





