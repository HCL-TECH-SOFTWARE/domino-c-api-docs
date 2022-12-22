




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



**Symbolic Value : Database**



**DBCREATE\_ENCRYPT\_xxx** **-** NSFDbCreateExtended
- EncryptStrength


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCREATE\_ENCRYPT\_NONE         -  Do not locally encrypt
database.  

  

      DBCREATE\_ENCRYPT\_SIMPLE      -  Locally encrypt this database with simple
level encryption.  

  

      DBCREATE\_ENCRYPT\_MEDIUM     -  Locally encrypt this database with medium
level encryption.  

  

      DBCREATE\_ENCRYPT\_STRONG    -  Locally encrypt this database with strong
level encryption.  

  




**Description :**



Local
encryption level for this database.  A locally encrypted database cannot be
opened locally without the appropriate user ID.  Refer to the Notes Help
documentation for a detailed description of the various local encryption
levels.


 **See Also :**


**[NSFDbCreateExtended](NSFDbCreateExtended.md)**



----------------------------------------------------------------------------------------------------------


 





