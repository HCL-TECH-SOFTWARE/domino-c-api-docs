




<!--
 /\* Font Definitions \*/
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




 


**Symbolic Value : Database**



**NSF\_INFO\_SIZE** **-** Maximum
length for thedatabase information buffer of a Domino database.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



**Description :**



This is the
maximum length for the database information buffer of a Domino database.  This
buffer is defined to contain text in host format that is null-terminated.  This
is the ONLY null-terminated field in all of NSF.  The database information
buffer contains one or more of the following pieces of information:  database
title, categories, class, and design class.


 **See Also :**


**[NSFDbInfoGet](NSFDbInfoGet.md)**


**[NSFDbInfoModify](NSFDbInfoModify.md)**


**[NSFDbInfoParse](NSFDbInfoParse.md)**


**[NSFDbInfoSet](NSFDbInfoSet.md)**



----------------------------------------------------------------------------------------------------------


 





