




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




**Initial Release 6**



**Data Type : DSAPI**



**FilterURLMapTypes** **-** URL map
types


**----------------------------------------------------------------------------------------------------------**



**#include
<dsapi.h>**



**Definition :**



typedef enum {


        kURLMapUnknown =
0,                   /\* Unknown mapping type. \*/


        kURLMapPass            =
1,                   /\* File system mapping rule \*/


        kURLMapExec            =
2,                   /\* CGI mapping rule \*/


        kURLMapRedirect
= 3,                  /\* Redirect mapping rule \*/


        kURLMapService =
4,                   /\* Obsolete. Not used anymore in Rnext. \*/


        kURLMapDomino  =
5                           /\* Domino mapping rule \*/


}
FilterURLMapTypes;


 


**Description :**



This
structure is a return value that the filter will have to provide the DSAPI
layer once the filter determines it needs to handle the kFilterMapURL event.
The filter is provided with the URL, and if the filter determines it needs to
do its own mapping, the filter has to provide what kind of mapping, passed via
this structure, it used to interpret the URL.


 




----------------------------------------------------------------------------------------------------------


 





