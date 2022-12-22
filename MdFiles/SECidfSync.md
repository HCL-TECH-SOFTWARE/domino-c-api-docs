




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




**Initial Release 8.5.2**



**Function : ID vault**



**SECidfSync** **- Synch the
ID file contents to the vault**


**----------------------------------------------------------------------------------------------------------**



**#include <idvault.h>**



STATUS
FAR PASCAL **SECidfSync(**  

      char \*pUserName,  

      char \*pPassword,  

      char \*pIDFilePath,  

      KFHANDLE \*phKFC,  

      char \*pServerName,  

      DWORD  dwReservedFlags,  

      WORD  wReservedType,  

      void \*pReserved,  

      DWORD \*retdwFlags**);**



**Description :**



Will either
open the ID file name provided or use the contents of phKFC if provided, locate
a vault server, synch the ID file contents to the vault, then return the
synched content in \*phKFC and/or pIDFilePath.If successful the vault server
name is retuned in pServerName.


 


 


**Parameters :**



Input :  

pUserName  -  Name of user whose ID is being synched with the vault copy -
should be full Notes DN name  

  

pPassword  -  Password to id file stored in the vault  

  

pIDFilePath  -  Path to id file being synched to the vault,may be NULL if phKFC
is not NULL  

  

phKFC  -  Pointer to hKFC of ID file being upload to the vault,may be NULL if
pIDFilePath is not NULL   

  

dwReservedFlags  -  Reserved flag should be set to 0  

  

wReservedType  -  Reserved type should be set to 0  

  

pReserved  -  Reserved pointer should be set to NULL  

  




Output :  

(routine)  -  An ERR status on failure indicating the problem.   

  

  

pIDFilePath  -  Path to id file being synched to the vault,may be NULL if phKFC
is not NULL  

  

phKFC  -  Pointer to hKFC of ID file being upload to the vault,may be NULL if
pIDFilePath is not NULL  

  

retdwFlags  -  Set to valus below based on results  

retdwFlags values  

#define IDV\_syncRetFlag\_IDSyncDone           
1  

#define IDV\_syncRetFlag\_IDFoundInVault        2  

#define IDV\_syncRetFlag\_IDNotFoundInVault    4  

  

  

  




 **Sample Usage :**


// Sync the
hKFC with the ID file in the Vault and write to S2.id and hKFC


               error
= SECidfSync (UserName, "2sherlock2",


                                             "c:\\s2.id",



                                             &hKFC2,



                                             ServerName,



                                             0,


                                             0,


                                             NULL,



                                             &VaultFlags);


 **See Also :**


**[SECidfGet](SECidfGet.md)**


**[SECidfPut](SECidfPut.md)**



----------------------------------------------------------------------------------------------------------


 





