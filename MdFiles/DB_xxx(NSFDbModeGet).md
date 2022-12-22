




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



**DB\_xxx (NSFDbModeGet)** **-** Specifies
whether a DBHANDLE is associated with a database or with a directory.


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DB\_LOADED            -  The DBHANDLE is a handle to a
database.  

  

      DB\_DIRECTORY      -  The DBHANDLE is a handle to a directory.  

  




**Description :**



The function
NSFDbModeGet returns one of these values to indicate whether a DBHANDLE is a
handle to a database or a handle to a directory.


 **See Also :**


**[NSFDbModeGet](NSFDbModeGet.md)**


**[NSFDbOpen](NSFDbOpen.md)**



----------------------------------------------------------------------------------------------------------


 





