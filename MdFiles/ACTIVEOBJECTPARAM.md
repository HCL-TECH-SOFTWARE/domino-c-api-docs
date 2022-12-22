




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




**Initial Release 4.6**



**Data Type : Rich Text**



**ACTIVEOBJECTPARAM** **-** Active
object parameter specification.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WORD Length;        /\* Length of the text string that follows \*/  

   WORD FormulaLength; /\* Length of the formula data (if any) that


                         
follows \*/  

   WORD Reserved;  

/\* Variable length data follows (strings not null terminated) \*/  

} ACTIVEOBJECTPARAM;


 


**Description :**



This record
specifies how a parameter to an active object is obtained.  This record only
appears following an ACTIVEOBJECT record, and is part of a CDHOTSPOTBEGIN
record.  The ACTIVEOBJECTPARAM may contain either a string representing the
entire parameter, or a string representing the parameter name and a formula
representing the parameter value.


 


In the first
case, the variable length data is a string of the form
"ParameterName=ParameterValue".  In this case, "Length"
should be the number of bytes in this string, and "FormulaLength"
should be zero.


 


In the
second case, the variable length data consists of a string representing the
parameter name followed by a formula representing the parameter value.  In this
case, "Length" should be the number of bytes in the parameter name
string, and "FormulaLength" should be the length of the formula.


 


The fields
in this record are:


 


Length              Length
of string parameter or length of parameter name.


FormulaLength  Length
of the formula, if any.  If no formula is provided, 0.


Reserved          Reserved; 
must be 0.


  

This record is followed first by the string, in LMBCS format with no NULL
delimiter, then by the formula, if present.


 **See Also :**


**[ACTIVEOBJECT](ACTIVEOBJECT.md)**


**[CDHOTSPOTBEGIN](CDHOTSPOTBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





