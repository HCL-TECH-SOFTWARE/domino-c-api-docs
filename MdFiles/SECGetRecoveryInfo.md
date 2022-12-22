




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



**SECGetRecoveryInfo** **- Extract
the recovery information from a certifier record or a certifier hKFC.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECGetRecoveryInfo(**  

      KFHANDLE  hKFC,  

      DHANLDE  hNote,  

      DHANDLE \*rethRecoveryInfo,  

      DWORD \*retRecoveryInfoSize,  

      RECOVERY\_INFO \*retRecoveryInfo,  

      void \*pReserved,  

      DWORD  ReservedFlags**);**



**Description :**



Given the
hNote of a certifier record or the hKFC from a certifier with recovery
information, extract the recovery information as a blob to be used later.


Routine:


      1.
If hNote is non null then locate ITEM\_RECOVERY\_INFO


      2.
Convert the item information from HAC to ODS and put into rethRecoveryInfo and
retRecoveryInfoSize, parse it and fill retRecoveryInfo.


      3.
If hNote is NULL and hKFC is non null determine if hKFC is Certifier or User.


        
If Certifier then create a certifier context based on the hKFC, get the
ODS-converted signed BBRequest object from the certifier context by calling
SECKFMCreateBBRequest, and put into rethRecoveryInfo and retRecoveryInfoSize. 


      4.Fill
in the retRecoveryInfo by determining Certifier or User hKFC or Certifier
hnote. 


            If
Certifier - pull information from the ODS in hRecoveryInfo


            If
User - pull information from KFM\_extratype\_BBCookies, ...\_BBPW and ...\_BBKeys


 


**Parameters :**



Input :  

hKFC  -  (1)- certifier's key file context if recovery info is to come from
certifier ID file   

                                    (2)- user's key file context if recovery
info is to come from a user ID file  

                                    (3)- otherwise NULLKFHANDLE  

  

hNote  -  (1)- note handle if recovery information is to come from a certifier
record   

                                    (2)- otherwise NULLHANDLE  

  

pReserved  -  reserved - should be set to NULL  

  

ReservedFlags  -  reserved - should be set to 0  

  




Output :  

(routine)  -  NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

rethRecoveryInfo  -  (1)- blob (ODS version of recovery information) to be
returned to the user  

                                    (2) - NULLHANDLE if hKFC is from User ID
file  

  

retRecoveryInfoSize  -  (1)- blob size (ODS size of the recovery information)  

                                    (2) - 0 if hKFC is from User ID file  

  

retRecoveryInfo  -  structure filled with the recovery information  

  




 **Sample Usage :**


        // cert ID
releated


            KFHANDLE      hcertHandle;


            char                 \*pcertIDPath
= "d:\\cert.id";


            char                 \*pcertIDPass
= "123456";


 


            //
recovery infomation releated


            DHANDLE                    hrecveryInfo;


            RECOVERY\_INFO        recvoeryInfo;


            DWORD                       recoveryInfoSize;


 


            if
(err = SECKFMOpen(&hcertHandle, pcertIDPath, pcertIDPass, SECKFM\_open\_All,
0, NULL)) 


            {


                        printAPIErr(err);


                        NotesTerm();


                        return
1;


            }


 


            err
= SECGetRecoveryInfo(hcertHandle, NULL, &hrecveryInfo,
&recoveryInfoSize, &recvoeryInfo, NULL, 0);


            if
(err) 


            {


                        printAPIErr(err);


                        SECKFMClose(&hcertHandle,
0, 0, NULL);


                        NotesTerm();


                        return
1;                        


            }


 




----------------------------------------------------------------------------------------------------------


 





