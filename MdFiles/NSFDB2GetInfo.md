




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



**Function : Database; DB2**



**NSFDB2GetInfo** **- Gets the
DB2 database information buffer.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2GetInfo(**  

      DBHANDLE  hDB,  

      int  infotype,  

      void far \*buffer,  

      DWORD \*size**);**



**Description :**



This
function retrieves the DB2-related information about a Domino database.


 


**Parameters :**



Input :  

hDB  -  The handle to the database for which you want information.  

  

infotype  -  The type of information to return.  See DB2NSF\_INFO\_xxx.  

  

size  -  Specifies the size, in bytes, of buffer.  

  




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_DB2NSF\_BUF\_TOO\_SMALL - Allocated buffer too small.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

buffer  -  Pointer to a buffer where specific database information will be
returned.  For type of database information returned, see DB2NSF\_INFO\_xxx.  

  

size  -  The size, in bytes, of the data returned.  If STATUS is
ERR\_DB2NSF\_BUF\_TOO\_SMALL, returns the required size, in bytes, of the buffer.  

  




 **See Also :**


**[DB2NSF\_INFO\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/971654431D33A08385256E60004B9601)**


**[NSFDB2GetServerInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F4041BDF22D5C4B585256E60004CAE77)**


**[NSFDB2ListNSFDB2Databases](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A57AF7CF730AA01685256E6000560BE5)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**


**[NSFDB2RegenerateLinks](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/986F1A03FA32C49985256E600055985D)**



----------------------------------------------------------------------------------------------------------


 





