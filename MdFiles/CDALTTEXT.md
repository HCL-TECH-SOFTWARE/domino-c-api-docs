




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



**Data Type : Composite Data; Rich
Text**



**CDALTTEXT** **-** Alternate
text for HTML Web browsers.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG Header;    /\* Tag and length \*/  

   WORD wLength;   /\* text length \*/  

   WORD Reserved1; /\* Reserved for future use \*/  

/\* The 8-bit text string follows... \*/  

} CDALTTEXT;


 


**Description :**



Documents
stored on a Lotus Domino server that are viewed via a Web browser may contain
elements that cannot be displayed by the browser.  These elements may have
alternate text that the browser will display in their place.  The alternate
text is stored in a CDALTTEXT record.  The fields in this record are:


 


Header             Identifies
this as a CDALTTEXT record.


wLength           Length
of the text string, in bytes.


Reserved1        Reserved; 
must be 0.


 


This record
is followed by the alternate text string.


 




----------------------------------------------------------------------------------------------------------


 





