




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



**CDQUERYFORMULA** **-** Formula
query CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {


   WSIG Header;  

   DWORD dwFlags;    /\* flags \*/  

   WORD wFormulaLen; /\* Length of formula \*/  

} CDQUERYFORMULA;


 


**Description :**



Formula
queries are stored in CDQUERYFORMULA records in fields of type TYPE\_QUERY,
usually the query field of an Agent.  The formula is run to select the
documents to be operated on by the Agent.  This record consists of this data
structure followed by the formula.  The fields in this structure are:


 


Header             Defines
this composite data item as a CDQUERYFORMULA item.


dwFlags                       Folder
query flags (see QUERYFORMULA\_FLAG\_xxx).


wFormulaLen                Length
of the formula.


 


This
structure is followed by the formula.


 **See Also :**


**[QUERYFORMULA\_FLAG\_xxx](QUERYFORMULA_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





