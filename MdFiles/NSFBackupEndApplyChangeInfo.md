




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



**NSFBackupEndApplyChangeInfo** **- End
application of the backup change information.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFBackupEndApplyChangeInfo(**  

      DHANDLE  ApplyInfoContext,  

      DWORD  Flags**);**



**Description :**



This
function will terminate the application of the backup change information to a
backup file.


 


**Parameters :**



Input :  

ApplyInfoContext  -  Handle to the apply info context obtained from
NSFBackupStartApplyChangeInfo.  

  

Flags  -  Zero to terminate the application of the backup change information. 
See APPLYEND\_xxx for more options.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successful.  

  

ERR\_INVALID\_CHANGE\_INFO\_CONTEXT - The ApplyInfoContext handle is invalid.  

  

ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error code for display.  

  

  




 **Sample Usage :**


   /\* Done with the
backup \*/  

   NSFBackupEndApplyChangeInfo(ApplyInfoContext,0);  

  




 **See Also :**


**[APPLYEND\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9D268541AC19D8FF852567110068FACE)**


**[NSFBackupStartApplyChangeInfo](NSFBackupStartApplyChangeInfo.md)**



----------------------------------------------------------------------------------------------------------


 





