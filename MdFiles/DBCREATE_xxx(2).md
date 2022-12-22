




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




**Initial Release 7.0**



**Symbolic Value : Database**



**DBCREATE\_xxx(2)** **-** NSFDbCreateExtendedWithOptions
- Options


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**


 **Symbolic Values :**      DBCREATE\_USE\_SERVER\_DEFAULT\_DATASTORE          -  Use server
default database type.  

  

      DBCREATE\_FORCE\_NSF\_DATASTORE      -  Use NSF database type (must have
proper authorization.)  

  

      DBCREATE\_FORCE\_DB2\_DATASTORE      -  Use DB2 database type (must have
proper authorization.)  

  

      DBCREATE\_UNDEFINED\_OPTIONS2          - 
DBCREATE\_USE\_SERVER\_DEFAULT\_DATASTORE | DBCREATE\_FORCE\_NSF\_DATASTORE |                                                             DBCREATE\_FORCE\_DB2\_DATASTORE
| DBCREATE\_OVERRIDE\_ADMINP  

  




**Description :**



Database
creation options.


 **See Also :**


**[NSFDbCreateExtendedWithOptions](NSFDbCreateExtendedWithOptions.md)**



----------------------------------------------------------------------------------------------------------


 





