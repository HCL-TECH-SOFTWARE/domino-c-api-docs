




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




**Initial Release 4.0**



**Function : Database**



**NSFDbSetOptions** **- Set
option flags for a database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbSetOptions(**  

      DBHANDLE  hDB,  

      DWORD  DbOptions,  

      DWORD  Mask**);**



**Description :**



Set the
option flags for the database.  The option flags are described in the entry
DBOPTION\_xxx.


 


**Parameters :**



Input :  

hDB  -  Handle of the database.  

  

DbOptions  -  New option flag settings.  

  

Mask  -  Bit mask that controls which options are updated.  Only the specified
option bits will be updated with the DbOptions value.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success, or what
the error is.  The return codes include:  

  

NOERROR  

  

  




 **Sample Usage :**


...


/\* enable Full Text
indexing \*/


status =
NSFDbSetOptions(db\_handle, DBOPTION\_FT\_INDEX, DBOPTION\_FT\_INDEX);


...


/\* disable Full Text
indexing \*/


status =
NSFDbSetOptions(db\_handle, (DWORD)0, DBOPTION\_FT\_INDEX);


...


/\* enable Full Text
indexing, disable uniform replica access \*/


status =
NSFDbSetOptions(db\_handle, DBOPTION\_FT\_INDEX, 


                        
DBOPTION\_FT\_INDEX | DBOPTION\_UNIFORM\_ACCESS);


...


 **See Also :**


**[NSFDbGetOptions](NSFDbGetOptions.md)**


**[DBOPTION\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0EE5CF1B5F5804FF852562900050AADD)**



----------------------------------------------------------------------------------------------------------


 





