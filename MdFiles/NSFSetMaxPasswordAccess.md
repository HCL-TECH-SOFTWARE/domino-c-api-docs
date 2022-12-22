




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




**Initial Release 4.6.1**



**Function : Access Control List**



**NSFSetMaxPasswordAccess** **- Sets the
maximum internet name and password access level.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFSetMaxPasswordAccess(**  

      DBHANDLE  hDB,  

      WORD  Level**);**



**Description :**



Set the
database's maximum internet name and password access level for Web users.


 


**Parameters :**



Input :  

hDB  -  Handle to database.  

  

Level  -  Maximum password access level (ACL\_LEVEL\_xxx).  

  




Output :  

(routine)  -  NOERROR - Successfully set the password access level.  

ERR\_ACL\_VERSION - Invalid Level parameter.  

ERR\_xxx - Use OSLoadString to display the error returned.  

  

  




 **See Also :**


**[ACL\_LEVEL\_xxx](ACL_LEVEL_xxx.md)**


**[NSFGetMaxPasswordAccess](NSFGetMaxPasswordAccess.md)**



----------------------------------------------------------------------------------------------------------


 





