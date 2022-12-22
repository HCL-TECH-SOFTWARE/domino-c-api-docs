




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



**SECidfGet** **- Get the
id file from the vault**


**----------------------------------------------------------------------------------------------------------**



**#include <idvault.h>**



STATUS
FAR PASCAL **SECidfGet(**  

      char \*pUserName,  

      char \*pPassword,  

      char \*pPutIDFileHere,  

      KFHANDLE \*phKFC,  

      char \*pServerName,  

      DWORD  dwReservedFlags,  

      WORD  wReservedType,  

      void \*pReserved**);**



**Description :**



Will contact
the server and locate a vault for pUserName. Then extract the ID file from the
vault and write it to pPutIDFileHere, and/or open down loaded ID file into an
hKFC, if successful returns with the vault server name in pServerName.


 


 


**Parameters :**



Input :  

pUserName  -  Name of user whose ID is being put into vault - should be full
Notes DN name.           

  

pPassword  -  Password to id file being uploaded to the vault  

  

pServerName  -  Name of server to contact - on successful return, name of
server which has the vault,should point to a MAXUSERNAME length  

  

dwReservedFlags  -  Reserved flag should be set to 0  

  

wReservedType  -  Rserved type should be set to 0  

       

  




Output :  

(routine)  -  An ERR status on failure indicating the problem.   

  

  

pPutIDFileHere  -  Path to where the download ID file should be created or
overwritten,may be NULL if phKFC is not NULL  

  

phKFC  -  Pointer receive the hKFC of the ID file down loaded file from the
vault,may be NULL if pPutIDFileHere is not NULL  

  

pServerName  -  Name of server to contact - on successful return, name of
server which has the vault,should point to a MAXUSERNAME length  

  




 **Sample Usage :**


        // Get id file
to local file name and hKFC


               error
= SECidfGet (UserName, 


                                             "2sherlock2",


                                             "c:\\s2.id",



                                             &hKFC2,



                                             ServerName,



                                             0,


                                             0,


                                             NULL);


 **See Also :**


**[SECidfPut](SECidfPut.md)**



----------------------------------------------------------------------------------------------------------


 





