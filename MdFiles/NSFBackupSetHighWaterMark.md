




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




**Initial Release 5.0**



**Function : Backup**



**NSFBackupSetHighWaterMark** **- Indicate
that backup has proceeded to a certain point.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupSetHighWaterMark(**  

      DBHANDLE  hDB,  

      DHANDLE  BackupContext,  

      DWORD  HighWaterMarkLow,  

      DWORD  HighWaterMarkHigh**);**



**Description :**



This
function indicates that the file has been recorded up to a certain point to
reduce before-image recording cost.


 


**Parameters :**



Input :  

hDB  -  The handle to the database on which the backup is being performed.  

  

BackupContext  -  Handle to the backup context that was obtained from
NSFBackupStart.  

  

HighWaterMarkLow  -  Low-order 32 bits of new high water mark.  

  

HighWaterMarkHigh  -  High-order 32 bits of new high water mark.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_NOT\_LOCAL - Database is remote.  

  

ERR\_NOT\_DOING\_BACKUP - No backup is underway.  

  

ERR\_xxx - Errors returned by lower level functions.  Call OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   do  

   {  

      ReadCount = 0;  

      while (BytesLeft)  

      {     

         BytesRead = min(BUFFER\_SIZE, BytesLeft);  

        

         if (err = OSFileRead(srcfd, Buffer, BytesRead))  

            break;  

           

         if ((MAXDWORD - SrcPositionLow) < BytesRead)  

         {  

            SrcPositionHigh++;  

            SrcPositionLow = (BytesRead - (MAXDWORD - SrcPositionLow)) - 1;  

         }  

         else  

         {  

            SrcPositionLow += BytesRead;  

         }  

     

         /\* Occassionally tell NSF that we've made progress to cut down on  

            recording overhead \*/  

         if ((++ReadCount % 10) == 0)  

            NSFBackupSetHighWaterMark(hDB,  

                                      BackupContext,  

                                      SrcPositionLow,  

                                      SrcPositionHigh);  

           

         if (err = OSFileWrite(dstfd, Buffer, BytesRead))  

            break;


 


        
BytesLeft -=BytesRead;  

      }


 


      if
(FileSizeHigh > 0)  

      {  

         BytesLeft = MAXDWORD;  

         FileSizeHigh--;  

      }  

      else  

      {  

         BytesLeft = FileSizeLow;  

         FileSizeLow = 0;  

      }


 


   } while
(BytesLeft && !(err));


 


 **See Also :**


**[NSFBackupStart](NSFBackupStart.md)**



----------------------------------------------------------------------------------------------------------


 





