




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



**NSFDB2GetServerInfo** **- Gets the
DB2-related information about a Domino server.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDB2GetServerInfo(**  

      char \*szServerName,  

      int  infotype,  

      void far \*buffer,  

      DWORD \*size**);**



**Description :**



This
function retrieves the DB2-related information about a Domino server.


 


**Parameters :**



Input :  

szServerName  -  The name of the Domino server.  

  

infotype  -  The type of information to return.  See DB2NSF\_SERVINFO\_xxx.  

  

size  -  Specifies the size, in bytes, of buffer.  

  




Output :  

(routine)  -  Return status from this call indicates either success or what the
error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_DB2NSF\_BUF\_TOO\_SMALL - Allocated buffer too small.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  

buffer  -  Pointer to a buffer where specific server information will be
returned.  For type of server information returned, see DB2NSF\_SERVERINFO\_xxx.  

  

size  -  The size, in bytes, of the data returned.  If STATUS is
ERR\_DB2NSF\_BUF\_TOO\_SMALL, returns the required size, in bytes, of the buffer.  

  




 **See Also :**


**[DB2NSF\_SERVINFO\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F939A55A81D3BD2E85256E60004D21C8)**


**[NSFDB2GetInfo](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/406189AFDCB6E04385256E60004A00D1)**


**[NSFDB2ListNSFDB2Databases](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/A57AF7CF730AA01685256E6000560BE5)**


**[NSFDB2ReconnectNotesDatabase](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F551E2856602672185256E600054B6EC)**


**[NSFDB2RegenerateLinks](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/986F1A03FA32C49985256E600055985D)**



----------------------------------------------------------------------------------------------------------


 





