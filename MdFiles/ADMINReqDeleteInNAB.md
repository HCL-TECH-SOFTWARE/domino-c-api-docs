




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




**Initial Release 4.6.2**



**Function : Administration Process**



**ADMINReqDeleteInNAB** **- Create a
"Delete in Address Book" request.**


**----------------------------------------------------------------------------------------------------------**



**#include <adminp.h>**



STATUS
LNPUBLIC **ADMINReqDeleteInNAB(**  

      DBHANDLE  dbhAdmin4,  

      char far \*chAuthor,  

      char far \*chUserName,  

      char far \*chMailServerName,  

      char far \*chMailFileName,  

      char far \*chDeleteMailFile,  

      ADMINReqParams far \*arpAdminReqParamsPtr,  

      WORD  wAdminReqParamsSize**);**



**Description :**



This
function creates a "Delete in Address Book" request in the
Administration Requests database (admin4.nsf).


 


**Parameters :**



Input :  

dbhAdmin4  -  Handle of the Administration Request database (admin4.nsf) that
is the destination of the created Admin Request note.  

  

chAuthor  -  A pointer to the Author's name (hierarchical names MUST be in
canonical format).  

  

chUserName  -  A pointer to the User's name being deleted (hierarchical names
MUST be in canonical format).  

  

chMailServerName  -  A pointer to the Mail Server name (hierarchical names MUST
be in canonical format).  

  

chMailFileName  -  A pointer to the Mail file name including path relative to
the Domino data directory.  

  

chDeleteMailFile  -  A pointer to a string indicating whether to delete the
mail file:  

  

          "0" = Don't delete mail file  

          "1" = Delete just mail file specified in person record  

          "2" = Delete mail file specified in person record & all
replicas  

  

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the
arpAdminReqParamsPtr parameter points to.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is.  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret code.  

  

  

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.  

  




 **Sample Usage :**


if (error =
NSFDbOpen (AdminDBPath, &hAdminReq))  

{


      return
(ERR(error));  

}


 


if (error =
ADMINReqDeleteInNAB (


      hAdminReq,  

      "CN=Alan Admin/O=Org",


      "CN=Joe
User/O=Org",  

      MAIL\_SRVR,  

      MAIL\_FILE,  

      "1",  

      &ARPptr,  

      sizeof(ARPptr)) )  

{


      error
= NSFDbClose (hAdminReq);  

      return (ERR(error));  

}


 **See Also :**


**[ADMINReqChkAccessMoveReplica](ADMINReqChkAccessMoveReplica.md)**


**[ADMINReqChkAccessNewReplica](ADMINReqChkAccessNewReplica.md)**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqMoveComplete](ADMINReqMoveComplete.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqParams](ADMINReqParams.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqRename](ADMINReqRename.md)**



----------------------------------------------------------------------------------------------------------


 





