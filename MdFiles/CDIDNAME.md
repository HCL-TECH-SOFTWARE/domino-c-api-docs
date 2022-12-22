




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



**Data Type : Composite Data; Rich
Text; Table**



**CDIDNAME** **-** Defines an
HTML ID.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG Header;    /\*
Signature and length of this record \*/


   WORD Length;    /\*
Length of ID \*/


   WORD wClassLen; /\*
Length of CLASS \*/


   WORD wStyleLen; /\*
Length of STYLE \*/


   WORD wTitleLen; /\*
Length of TITLE \*/


   WORD wExtraLen; /\*
Length of extra attribute/value pairs \*/


   WORD wNameLen;  /\*
Length of NAME \*/


   BYTE  reserved[10];


/\*  id follows \*/


/\* class follows \*/


/\* style follows \*/


/\* title follows \*/


/\* extra attrib/value
pairs of object follows \*/


/\* name follows \*/


} CDIDNAME;


 


**Description :**



This CD
record describes the HTML field properties, ID, Class, Style, Title, Other and
Name associated for any given field defined within a Domino Form.


 




----------------------------------------------------------------------------------------------------------


 





