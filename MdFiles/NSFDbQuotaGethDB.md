




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




**Initial Release 6**



**Function : Database**



**NSFDbQuotaGethDB** **- Return
the database quota given a database handle.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbQuotaGethDB(**  

      DBHANDLE  hDB,  

      DBQUOTAINFOEXT \*QuotaInfo**);**



**Description :**



This
function returns the specified database quota information given its database
handle.  This information is also available from the Notes user interface by
choosing menu items File - Tools - Server Administration to bring up Domino
Administrator.  Next, click on the File tab and select a database, then choose
Files - Quotas from the menu to see the quota settings dialog.


 


**Parameters :**



Input :  

hDB  -  The handle to the database  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully obtained quota information.  

  

ERR\_NO\_SERVER\_ACCESS - You are not authorized to use the server.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

QuotaInfo  -  Pointer to the returned DBQUOTAINFOEXT structure.   

  




 **See Also :**


**[DBQUOTAINFOEXT](DBQUOTAINFOEXT.md)**



----------------------------------------------------------------------------------------------------------


 





