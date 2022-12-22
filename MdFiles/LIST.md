




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : Item (Field) Information**



**LIST** **-** Used to
specify multiple values in a field.


**----------------------------------------------------------------------------------------------------------**



**#include
<global.h>**



**Definition :**



typedef struct {  

   USHORT ListEntries;  

/\* now come the list entries \*/  

} LIST;


 


**Description :**



This
datatype is used by several data structures to specify that a field contains a
list of one or more values.  A list is made up of one or more items of a
datatype, separated by a delimiter.  

  

The value in the ListEntries field of LIST is the number of items specified in
a delimited list of items.  

  




 **See Also :**


**[TYPE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**


**[TYPE\_xxx [TEXT\_LIST]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/FA0CCEF9D263BFBB8525622E0063A01A)**



----------------------------------------------------------------------------------------------------------


 





