




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




**Initial Release 8.0**



**Function : Recovery**



**SECImportRecoveryInfo** **- Import
recovery information into an ID file**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECImportRecoveryInfo(**  

      KFHANDLE  hKFC,  

      DHANDLE  hRecoveryInfo,  

      DWORD  RecoveryInfoSize,  

      void \*pReserved,  

      DWORD  ReservedFlags**);**



**Description :**



Given the
name of an ID file to import recovery information into and recovery
information, import the recovery information creating the ID file ready for
recover.


Routine:


      1.
Get the currect password off the hKFC


      2.
Import the recovery information through a call to BSAFECreateRecoveryInfo.


 


**Parameters :**



Input :  

hKFC  -  ID file context to import the recovery information into (cannot be
NULLKFHANDLE)  

  

hRecoveryInfo  -  (1)- handle to recovery blob to be imported into hKFC  

                                    (2)-  (ODS version of recovery information)  

  

RecoveryInfoSize  -  blob size (ODS size of the recovery information)  

  

pReserved  -  reserved - should be set to NULL  

  

ReservedFlags  -  reserved - should be set to 0  

  




Output :  

(routine)  -  NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  




 **Sample Usage :**


      //
user ID releated


            KFHANDLE      hUserIDHandle;


            char                 \*puserIDPath
= "D:\\sectester.id";


            char                 \*puserIDPass
= "123456";


 


            //
recovery infomation releated


            DHANDLE                    hrecveryInfo;


            RECOVERY\_INFO        recvoeryInfo;


            DWORD                       recoveryInfoSize;


 


            //
import recovery info into the target user id


 


            if
(err = SECKFMOpen(&hUserIDHandle, puserIDPath, puserIDPass,
SECKFM\_open\_All, 0, NULL))


            {


                        printAPIErr(err);


                        SECKFMClose(&hcertHandle,
0, 0, NULL);


                        NotesTerm();


                        return
1;            


            }


 


            err
= SECImportRecoveryInfo(hUserIDHandle, hrecveryInfo, recoveryInfoSize, NULL,
0);


            if
(((err != 0) && (err != 3904)))


            {


                        printAPIErr(err);


                        NotesTerm();


                        return
1;                                    


            }


 




----------------------------------------------------------------------------------------------------------


 





