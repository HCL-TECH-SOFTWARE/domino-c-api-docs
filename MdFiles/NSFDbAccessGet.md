




<!--
 /\* Font Definitions \*/
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



**Function : Database**



**NSFDbAccessGet** **- Get the
current access level for an open database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



void
LNPUBLIC **NSFDbAccessGet(**  

      DBHANDLE  hDB,  

      WORD far \*retAccessLevel,  

      WORD far \*retAccessFlag**);**



**Description :**



This function
gets the level of database access granted to the username that opened the
database.


 


**Parameters :**



Input :  

hDB  -  The handle to the open database.  

  




Output :  

(routine)  -  None  

  

  

retAccessLevel  -  The level of database access (as in ACL\_LEVEL\_xxx) that is
allowed to the username that was used to open the database.  

  

retAccessFlag  -  Modifier flags (as in ACL\_FLAG\_xxx) for the user's database
access.  

  




 **See Also :**


**[ACL\_FLAG\_xxx](ACL_FLAG_xxx.md)**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





