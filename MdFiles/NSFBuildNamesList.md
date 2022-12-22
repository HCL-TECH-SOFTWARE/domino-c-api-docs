




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



**NSFBuildNamesList** **- Builds a
NAMES\_LIST structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBuildNamesList(**  

      char \*UserName,  

      DWORD  dwFlags,  

      DHANDLE \*rethNamesList**);**



**Description :**



This
function builds a NAMES\_LIST structure with the supplied UserName, and returns
a HANDLE to the structure.  The resulting NAMES\_LIST structure contains the
UserName along with any related group names the user is a member of.  Group
information is obtained from the local Domino Directory.


 


This HANDLE
may then be passed to the function NSFDbOpenExtended to open a local database
with the specified UserName.  This causes the user's ACL permissions to be
enforced if they exist in the Access Control List.  Normally Domino and Notes
do not check the ACL when opening a local database.


 


After
calling NSFBuildNamesList, you must set the Authenticated member of the
NAMES\_LIST structure to NAMES\_LIST\_AUTHENTICATED or
NAMES\_LIST\_PASSWORD\_AUTHENTICATED (or both values OR'd together) to gain access
to the database.  Any other value will result in the error code ERR\_NOACCESS
being returned.


 


**Parameters :**



Input :  

UserName  -  The specified user name whose ACL you want enforced.  Use NULL for
the current User.  If the user name is hierarchical, use the fully
distinguished name, not the abbreviated user name.  

  

dwFlags  -  Currently not used.  Set to 0.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully built the NAMES\_LIST.  

ERR\_NO\_ACCESS - User isn't authorized to perform operation.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

rethNamesList  -  Returns a HANDLE to a NAMES\_LIST structure that contains the
UserName along with any related group names the user is a member of. The caller
is responsible for freeing this handle with OSMemFree.  This structure is
defined in ACL.H.  

  




 **Sample Usage :**


if (error =
NSFBuildNamesList(pUserName, 0 ,&hNamesList))


   goto Exit;


 


pNamesList =
OSLock(NAMES\_LIST, hNamesList);


 


/\* set Authenticated
member of NAMES\_LIST structure \*/


pNamesList->Authenticated
= NAMES\_LIST\_AUTHENTICATED | NAMES\_LIST\_PASSWORD\_AUTHENTICATED;


 


/\* to print out
NAMES\_LIST structure \*/


ptr = (char
\*)&pNamesList[1];


 


for (i=0;
i<pNamesList->NumNames; i++)


{


 
printf("Names:%s\n", ptr);


  ptr += strlen(ptr) +
1;


}


 


 


/\* pass hNamesList to
NSFDbOpenExtended \*/


error =
NSFDbOpenExtended(PathName, 0, hNamesList, 0, &db\_handle, data\_td\_src,


                         
nondata\_td\_src);


 


/\* free up memory \*/


if (hNamesList)


{


  OSUnlock(hNamesList);


 
OSMemFree(hNamesList);


}


if (error)


    ...


 **See Also :**


**[NAMES\_LIST](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/009F0044002000E285255E3F0001744B)**


**[NAMES\_LIST\_xxx](NAMES_LIST_xxx.md)**


**[NSFDbOpenExtended](NSFDbOpenExtended.md)**



----------------------------------------------------------------------------------------------------------


 





