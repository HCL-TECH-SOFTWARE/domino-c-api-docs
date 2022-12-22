




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



**NSFDbGetOptions** **- Retrieve
database option flags.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetOptions(**  

      DBHANDLE  hDB,  

      DWORD far \*retDbOptions**);**



**Description :**



Get the
option flags set for this database.  The option flags are described in the
entry DBOPTION\_xxx.


 


**Parameters :**



Input :  

hDB  -  Handle of the database.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR - Successfully retrieved database option flags.  

  

ERR\_SPECIAL\_ID - No database option flags were found in this database.  This means
that no database option flags were set for this database.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

  

retDbOptions  -  Option flags for this database are stored at this address.  

  




 **See Also :**


**[NSFDbSetOptions](NSFDbSetOptions.md)**


**[DBOPTION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0EE5CF1B5F5804FF852562900050AADD)**



----------------------------------------------------------------------------------------------------------


 





