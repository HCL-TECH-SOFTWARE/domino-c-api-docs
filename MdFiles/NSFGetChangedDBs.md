




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




 


**Function : Database**



**NSFGetChangedDBs** **- Get the
changed databases that have occurred on the server since SinceTime**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
far PASCAL **NSFGetChangedDBs(**  

      char \*ServerName,  

      TIMEDATE \*SinceTime,  

      DWORD \*ChangesSize,  

      DHANDLE \*hChanges,  

      TIMEDATE \*NextSinceTime**);**



**Description :**



Get the
changed databases that have occurred on the server since SinceTime


 


**Parameters :**



Input :  

ServerName  -  name of server to check for changed dbs on (failover will not
happen with this API)  

  

SinceTime  -  list of dbs located in rethChanges will only be populated with
dbs that have been modified since this time   

  




Output :  

(routine)  -  NOERROR - Successful.  

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

ChangesSize  -  Size in bytes of the value represented by hChanges  

  

hChanges  -  Returned list of dbs that have changed since SinceTime.  

  

NextSinceTime  -  New Since Time  

  




 **Sample Usage :**



char                      \*server\_name;               
/\*
server name where database lives\*/


TIMEDATE         SinceTime,NextSinceTime;


STATUS    
      error = NOERROR;             /\* error code from API calls \*/


DWORD
                            ChangesSize;


DHANDLE
        hChanges=NULLHANDLE;


char                      \*pChanges;


char                      DbPath[MAXPATH]
= {0};


int                         i=0;


DWORD                             PathLen
= 0;


 


 


if
( error = NSFGetChangedDBs(server\_name, &SinceTime, 


  
                                        &ChangesSize, &hChanges,
&NextSinceTime))


{


  
          goto exit;


  
          


}


if (  (error ==
NOERROR) && (ChangesSize > 0) && (hChanges != NULLHANDLE))


{


               pChanges
= OSLock(char,hChanges);                                                                       


               strcpy(DbPath,
pChanges);


               printf("
Get modifed dbs list that have occurred on the server since
SinceTime:\n");


               while(ChangesSize>0)


               {


                              i=i++;


                              strcpy(DbPath,
pChanges);


                              PathLen
= strlen(DbPath) + 1;


                              pChanges
+= PathLen;


                              ChangesSize
-= PathLen;


                              printf
("%d, %s\n",i,DbPath);


               }


                                             


               OSUnlock(hChanges);


 


}


else 


{


               printf
("------ No Modified dbs found\n");


}


 


 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





