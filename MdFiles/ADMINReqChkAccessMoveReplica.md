




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



**ADMINReqChkAccessMoveReplica** **- Create a
"Check Access for Move Replica Creation" request.** 


**----------------------------------------------------------------------------------------------------------**



**#include <adminp.h>**



STATUS
LNPUBLIC **ADMINReqChkAccessMoveReplica(**  

      DBHANDLE  dbhAdmin4,  

      char far \*chAuthor,  

      char far \*chSrcServer,  

      char far \*chSrcPathName,  

      char far \*chTitle,  

      DBREPLICAINFO \*Replicainfo,  

      char far \*chDesServer,  

      char far \*chDesPathName,  

      ADMINReqParams far \*arpAdminReqParamsPtr,  

      WORD  wAdminReqParamsSize**);**



**Description :**



This
function creates a "Check Access for Move Replica Creation" request
in the Administration Requests database (admin4.nsf). 


 


**Parameters :**



Input :  

dbhAdmin4  -  Handle of the Administration Request database (admin4.nsf) that
is the destination of the created Admin Request note.  

  

chAuthor  -  A pointer to the Author's name (hierarchical names MUST be in
canonical format).  

  

chSrcServer  -  A pointer to Source Server name (hierarchical names MUST be in
canonical format).  

  

chSrcPathName  -  A pointer to source file name including path relative to the
Domino data directory.  

  

chTitle  -  A pointer to the Title of the database being replicated.  

  

Replicainfo  -  Replicainfo - A pointer to source database Replicainfo.  

  

chDesServer  -  A pointer to destination Server name (hierarchical names MUST
be in canonical format).  

  

chDesPathName  -  A pointer to destination file name including path relative to
the Domino data directory.  

  

arpAdminReqParamsPtr  -  Pointer to an ADMINReqParams structure.  

  

wAdminReqParamsSize  -  Size of the buffer (ADMINReqParams structure) that the
arpAdminReqParamsPtr parameter points to.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is.  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions. Call OSLoadString to
interpret code.  

  

  




 **Sample Usage :**


if (error =
NSFDbReplicaInfoGet (hSrcDB, &replica\_info))  

{  

      NSFDbClose (hSrcDB);  

      return (ERR(error));  

}


 


if (error =
NSFDbOpen (AdminDBPath, &hAdminReq))  

{  

      NSFDbClose (hSrcDB);  

      return (ERR(error));  

 }


 


if (error =
ADMINReqChkAccessMoveReplica (  

      hAdminReq,  

      "CN=Alan Admin/O=Org",  

      SOURCE\_SRVR,  

      SOURCE\_FILE,  

      DB\_TITLE,  

      &replica\_info,  

      TARGET\_SRVR,  

      TARGET\_FILE,  

      &ARPptr,  

      sizeof(ARPptr)) )  

{  

      NSFDbClose (hSrcDB);  

      NSFDbClose (hAdminReq);  

      return (ERR(error));  

}


 **See Also :**


**[ADMINReqChkAccessNewReplica](ADMINReqChkAccessNewReplica.md)**


**[ADMINReqDeleteInACL](ADMINReqDeleteInACL.md)**


**[ADMINReqDeleteInNAB](ADMINReqDeleteInNAB.md)**


**[ADMINReqMoveComplete](ADMINReqMoveComplete.md)**


**[ADMINReqMoveUserInHier](ADMINReqMoveUserInHier.md)**


**[ADMINReqParams](ADMINReqParams.md)**


**[ADMINReqRecertify](ADMINReqRecertify.md)**


**[ADMINReqRename](ADMINReqRename.md)**



----------------------------------------------------------------------------------------------------------


 





