




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



**Function : Replica Info; Replication**



**NSFDbClearReplHistory** **- Clear
database replication history**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbClearReplHistory(**  

      DBHANDLE  hDb,  

      DWORD  dwFlags**);**



**Description :**



This
function clears out the replication history information of the specified
database replica.  This can also be done using the Notes user interface via the
File/Replication/History menu item selection.


 


**Parameters :**



Input :  

hDb  -  Handle to the database, already opened.  

  

dwFlags  -  Must be zero.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully cleared replication history information.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **Sample Usage :**


DBHANDLE   
db\_handle;         /\* handle of source database \*/


  
STATUS      error = NOERROR;   /\* return status from API calls \*/


   char
szErrorString[256];


 


   /\* Open
the database \*/


   ...


 


   /\* Clear
replication history \*/


   error =
NSFDbClearReplHistory(db\_handle, 0);


   if
(error)


   {


     
OSLoadString(0, ERR(error), szErrorString, 255);


     
printf ("Error from NSFDbClearReplHistory:  %s\n\n", szErrorString);


     
NSFDbClose (db\_handle);


     
LAPI\_RETURN (ERR(error));      


   }


   printf
("Replication history cleared\n");


 


   /\* Close
the database \*/


   ...


 


 **See Also :**


**[NSFDbGetReplHistorySummary](NSFDbGetReplHistorySummary.md)**



----------------------------------------------------------------------------------------------------------


 





