




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



**Function : Database; Extension
Manager**



**NSFDbUserNameGet** **- Get the
user name of the user who is accessing the specified database.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbUserNameGet(**  

      DBHANDLE  hDB,  

      char far \*retUserName,  

      WORD  BufferLength**);**



**Description :**



This
function returns the name of the user who is accessing the specified database. 
This function is useful in client and server extension manager applications in
order to obtain the user name of the user performing the database operation. 
This allows extension manager applications to obtain the same user name that is
available to database hook drivers.


 


**Note:**  If calling
NSFDbOpenExtended with option set to DBOPEN\_NO\_USERINFO, and the client or
server extension manager is trapping this call, calling NSFDbUserNameGet will
return an empty string for the user name. 


 


**Parameters :**



Input :  

hDB  -  Handle to the open database.  

  

BufferLength  -  Length of the retUserName buffer.  

  




Output :  

(routine)  -   Return status from this call:  

  

NOERROR - Success  

  

ERR\_xxx - Function was not successful.  Use OSLoadString() to interpret the
error status as a string that you may display/log for the user.  

  

  

retUserName  -  Pointer to the buffer in which a null-terminated user name
string is returned.  The buffer should have a minimum length of MAXUSERNAME + 1
(see names.h).  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





