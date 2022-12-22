




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




 


**Function : Database**



**NSFDbClassGet** **- Gets the
database creation class.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbClassGet(**  

      HANDLE  hDB,  

      WORD far \*retClass**);**



**Description :**



This
function gets the database creation class specified when the database was
created.  This function is useful for those API programs that need to determine
whether the database was created specifically for alternate mail (in this case,
DBCLASS\_ENCAPSMAILFILE will be returned).  However, for all other types of
databases, there is no guarantee that the database matches the database
creation class description.


 


**Parameters :**



Input :  

hDB  -  Handle to an opened Domino database.  

  




Output :  

(routine)  -  Return status from this call.  NOERROR is always returned.  

  

  

retClass  -  The address of the database creation class specified when the
database was created.  See DBCLASS\_xxx for a list of the database creation
classes.  

  




 **See Also :**


**[NSFDbCreate](NSFDbCreate.md)**


**[DBCLASS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B460075BDBF)**



----------------------------------------------------------------------------------------------------------


 





