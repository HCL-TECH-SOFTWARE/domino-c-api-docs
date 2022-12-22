




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




**Initial Release 8.0**



**Function : Recovery**



**SECBuildEncryptedBackupIDFile** **- Create a
backup copy of the ID file and return the respository name of where it should
be mailed to.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECBuildEncryptedBackupIDFile(**  

      char \*pIDFileName,  

      KFM\_PASSWORD \*pCurrentPW,  

      char \*pBackupPath,  

      char \*retRepositoryBuf,  

      DWORD  MaxRepositoryBufLen,  

      DWORD \*retRepositoryBufLen,  

      void \*pReserved,  

      DWORD  ReservedFlags**);**



**Description :**



Given the
name of the ID file,password and location of where to put a backup copy of the
ID file, create the backup copy and return the respository information if
requested.


Routine:


      1.Read
in the KFC from the currently running ID file or from pIDFileName if non NULL


      2.
Call SECKFMBuildEncryptedBackup


      3.
If retRepositoryBuf is non NULL then fill in the repository name


 


**Parameters :**



Input :  

pIDFileName  -  pointer to name of the ID file to be used to create a backup
copy . NULL if use current  

  

pCurrentPW  -  KFM\_PASSWORD to pIDFileName - NULL if use current  

  

pBackupPath  -  pointer to where the backup copy of the ID file will be created  

  

retRepositoryBuf  -  pointer to receive the configured mail to address of the
recovery information. (Optional) maybe NULL.  

  

MaxRepositoryBufLen  -  max size of retRepositoryBuf  

  

pReserved  -  reserved - should be set to NULL  

  

ReservedFlags  -  reserved - should be set to 0  

  




Output :  

(routine)  -  NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

retRepositoryBufLen  -  the length value in retRepositoryBuf. (Optional) maybe
NULL.  

  




 **Sample Usage :**


         char     
\*puserIDPath = "D:\\sectester.id";


       
char        \*puserIDPass = "123456";


       
char        \*pUserIDBackUPPath = "d:\\sectesterBk.ide";


       
char    strRepositoryBuf[MAXPATH];


       
DWORD             repositoryBufRealLen = 0;


 


            //
create a backup copy of the id file


 


            SECKFMCreatePassword(puserIDPass,
&retHashedPassWD);


 


            if
(err = SECBuildEncryptedBackupIDFile(puserIDPath, &retHashedPassWD,
pUserIDBackUPPath,


                        strRepositoryBuf,
MAXPATH, &repositoryBufRealLen, NULL, 0)) 


            {


                        fprintf(flog,"SECBuildEncryptedBackupIDFile
failed\n");


                        printAPIErr(err);            


                        NotesTerm();


            }


 


**See Sample Program :**


MISC\IDBACKUP


 




----------------------------------------------------------------------------------------------------------


 





