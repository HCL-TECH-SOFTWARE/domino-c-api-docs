




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



**Data Type : Agents**



**ODS\_ASSISTFIELDSTRUCT** **-** Field
actions associated with a form.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WORD wTotalLen;      /\* Total length of field structure


                          
(includes padding) \*/  

   WORD wOperator;      /\* Query or action operator


                          
(ACTIONBYFIELD\_OP\_xxx or


                           
QUERYBYFIELD\_OP\_xxx) \*/  

   WORD wFieldNameLen;  /\* Field name length \*/  

   WORD wValueLen;      /\* Length of value \*/  

   WORD wValueDataType; /\* Reserved; must be 0 \*/  

   WORD wSpare;


           /\* Field
name follows \*/


           /\* Text list
of values follows \*/


           /\* Padded to
WORD boundary \*/  

} ODS\_ASSISTFIELDSTRUCT;


 


**Description :**



Within a
CDACTIONBYFORM record, the actions for individual fields are specifed in an
array of ODS\_ASSISTFIELDSTRUCT structures.  The fields in this structure are:


 


wTotalLen                     Length
of this structure, including padding, in bytes


wOperator                    Field
operation - one of the ACTIONBYFIELD\_OP\_xxx or QUERYBYFIELD\_OP\_xxx values


wFieldNameLen            Length
of the field name


wValueLen                    Length
of the value


wValueDataType           Reserved; 
must be 0


 


This
structure is followed by the field name, then the data for the new value.  The
value is stored as a text list, beginning with the type word containing
TYPE\_TEXT\_LIST.


 **See Also :**


**[ACTIONBYFIELD\_OP\_xxx](ACTIONBYFIELD_OP_xxx.md)**


**[CDACTIONBYFORM](CDACTIONBYFORM.md)**


**[QUERYBYFIELD\_OP\_xxx](QUERYBYFIELD_OP_xxx.md)**


**[CDQUERYBYFORM](CDQUERYBYFORM.md)**



----------------------------------------------------------------------------------------------------------


 





