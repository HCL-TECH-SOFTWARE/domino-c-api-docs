




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



**CDQUERYTEXTTERM** **-** Text Search
Term query CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<queryods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD dwFlags;                    /\* flags for this string \*/  

   DWORD dwLength[MAXTEXTTERMCOUNT]; /\* length of strings \*/


           /\* strings
follow \*/


} CDQUERYTEXTTERM;


 


**Description :**



Text search
information is stored in the CDQUERYTEXTTERM record in a field of TYPE\_QUERY,
usually in the query field of an Agent.  These text strings are used as input
to the full text search facility to select the documents to be operated on by
the Agent.  This record consists of the structure, followed by up to
MAXTEXTTERMCOUNT strings containing the text to search for.  The fields in this
structure are:


 


Header Defines
this composite data item as a CDQUERYTEXTTERM item.


dwFlags           Text
search flags (see TEXTTERM\_FLAG\_xxx).


dwLength          Array
containing the lengths of the strings;  entries may be 0.


 


This
structure is followed by the text strings in packed format (no NUL
terminators).


 **See Also :**


**[MAXTEXTTERMCOUNT](MAXTEXTTERMCOUNT.md)**


**[TEXTTERM\_FLAG\_xxx](TEXTTERM_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





