




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



**Function : Access Control List; User**



**NSFDbGetNamesList** **- Returns a
Handle to a NAMES\_LIST structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetNamesList(**  

      DBHANDLE  hDB,  

      DWORD  Flags,  

      DHANDLE \*rethNamesList**);**



**Description :**



This
function is used with an Extension Manager running on a Lotus Domino server,
and can be called after trapping an EM\_NSFDBOPENEXTENDED hook.  This function
returns a HANDLE to a NAMES\_LIST structure which can be NULL (will always be
NULL on a local database).  The NAMES\_LIST structure contains ACL information
for the specified database.  


 


Note: A
database's ACL is only enforced on a server.


 


 


**Parameters :**



Input :  

hDB  -  A Handle to a database.  

  

Flags  -  The Flags parameter is not used at this time.  Set to 0.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully made the call.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

  

rethNamesList  -  Returns a HANDLE to a NAMES\_LIST structure.   This structure
is in the header file acl.h.  The handle may be NULL.  

  




 **Sample Usage :**


if (error =
NSFDbGetNamesList(hDb, 0 ,&hNamesList))


   goto Exit;


 


/\* to print out
NAMES\_LIST structure \*/


pNamesList =
OSLock(NAMES\_LIST, hNamesList);


 


ptr = (char
\*)&pNamesList[1];


for (i=0;
i<pNamesList->NumNames; i++)


{


 
printf("Names:%s\n", ptr);


  ptr += strlen(ptr) +
1;


}


 


/\* free up memory \*/


if (hNamesList)


{


  OSUnlock(hNamesList);


 
OSMemFree(hNamesList);


}


 


 **See Also :**


**[NAMES\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/009F0044002000E285255E3F0001744B)**


**[NAMES\_LIST\_xxx](NAMES_LIST_xxx.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





