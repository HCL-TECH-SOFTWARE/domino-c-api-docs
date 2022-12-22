




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




**Initial Release 4.5**



**Function : Calendaring and
Scheduling**



**SchRetrieve** **- Retrieve
a schedule.**


**----------------------------------------------------------------------------------------------------------**



**#include <schedule.h>**



STATUS
LNPUBLIC **SchRetrieve(**  

      const UNID FAR \*pApptUnid,  

      TIMEDATE FAR \*pApptOrigDate,  

      DWORD  dwOptions,  

      TIMEDATE\_PAIR FAR \*pInterval,  

      LIST FAR \*pNames,  

      HCNTNR FAR \*rethCntnr,  

      void FAR \*MustBeNull1,  

      void FAR \*MustBeNull2,  

      void FAR\* FAR \*MustBeNull3**);**



**Description :**



Synchronously
retrieves a local or remote schedule by asking the caller's home server for the
schedule.


 


      
The ONLY time that local busy time is used is when the client is in the
Disconnected mode which is specified through the location document.  Otherwise,
the API will route ALL lookup requests to the users home server for processing.


 


**Parameters :**



Input :  

pApptUnid  -  Ignore this UNID in computations.  

  

pApptOrigDate  -  Reserved.  Must be set to NULL.  

  

dwOptions  -  Option flags:  

SCHRQST\_COMPOSITE    return composite schedule  

SCHRQST\_EACHPERSON  return each person's schedule  

SCHRQST\_LOCAL do only local lookup  

SCHRQST\_FORCEREMOTE force remote even if you are using workstation based email  

SCHRQST\_EXTFORMAT get busytime in the SCHED\_ENTRY\_EXT format instead of the
normal SCHED\_ENTRY format from pre 6 Note: Use does not guarantee that data
will be in SCHED\_ENTRY\_EXT format since we do not convert data from pre 6
servers.  

  

pInterval  -   Pointer to a TIMEDATE\_PAIR structure that specifies the range
over which the free time search should be performed. In typical scheduling
applications, this might be a range of 1 day or 5 days.  

  

pNames  -  Pointer to a list of fully distinguished names whose schedule should
be searched. This list is in TEXT\_LIST format without the datatype work. This
list can be conveniently built with the textlist package.  

  

MustBeNull1  -  This parameter must be NULL.  

  

MustBeNull2  -  This parameter must be NULL.  

  

MustBeNull3  -  This parameter must be NULL.  

  




Output :  

(routine)  -  NOERROR - Successfully retrieved a schedule.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

rethCntnr  -  Handle of schedule container results are returned in. If
\*rethCntnr is NULLHANDLE, then the container will be allocated by this call. If
it is not NULLHANDLE then the caller has allocated it and is responsible for
freeing it on all errors.  

  




 **See Also :**


**[SchContainer\_Free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1B1F99C51F7DAA688525635D006DEB1C)**


**[SchSrvRetrieve](SchSrvRetrieve.md)**


**[SCHRQST\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/619DE548C731AFEB8525635D00797CEC)**



----------------------------------------------------------------------------------------------------------


 





