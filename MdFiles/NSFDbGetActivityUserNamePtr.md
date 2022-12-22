




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




**Initial Release 4.5**



**Function : Database**



**NSFDbGetActivityUserNamePtr** **- Returns
the user name for a specific entry in the database's user session activity
array.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



char
FAR \* **NSFDbGetActivityUserNamePtr(**  

      DBACTIVITY\_ENTRY \*DbActivity,  

      int  Index**);**



**Description :**



This routine
returns the user name for a specific entry in the database user session
activity array.  Use NSFDbGetUserActivity() to obtain a handle to the user
session activity information.  Use OSLock() to lock this handle to obtain a
pointer to the data.  Pass this pointer in as the DbActivity argument of this
routine.


 


Implemented
as a macro:


 


#define
NSFDbGetActivityUserNamePtr(DbActivity, Index) \  

   (((char FAR \*) DbActivity) + DbActivity[Index].UserNameOffset)


 


**Parameters :**



Input :  

DbActivity  -  Pointer to the first structure in database's user session
activity array.  

  

Index  -  Index into the database's user session activity array.  This index is
zero-based and indicates which entry in the database's user session activity
array you wish to access.  

  




Output :  

(routine)  -  A null-terminated pointer to the user name component of a
database's user session activity information entry.  

  

  




 **See Also :**


**[NSFDbGetUserActivity](NSFDbGetUserActivity.md)**


**[DBACTIVITY](DBACTIVITY.md)**


**[DBACTIVITY\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/3B37410B1EDDFD3E85256379006EAB1B)**



----------------------------------------------------------------------------------------------------------


 





