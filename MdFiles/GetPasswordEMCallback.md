




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




**Initial Release 4.0**



**Function : Extension Manager**



**GetPasswordEMCallback** **- Extension
Manager callback for EM\_GETPASSWORD.**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **GetPasswordEMCallback(**  

      DWORD  MaxPwdLen,  

      DWORD far \*retLength,  

      char far \*retPassword,  

      char far \*FileName,  

      char far \*OwnerName,  

      DWORD  DataLen,  

      BYTE far \*Data**);**



**Description :**



EM\_GETPASSWORD
occurs when a user is about to be prompted for a password to decrypt an ID
file.  EM\_GETPASSWORD can only be registered with the EM\_REG\_BEFORE flag.  An
extension manager hook for EM\_GETPASSWORD cannot be called after Domino or
Notes processes this operation.


 


**Parameters :**



Input :  

MaxPwdLen  -  Longest password you may supply.  

  

FileName  -  The name of the ID file.  

  

OwnerName  -  The name of the owner of the ID file.  

  

DataLen  -  The length of the extra ID information.  

  

Data  -  The extra ID information (if any).  Domino and Notes know nothing
about the contents of this information.  In order to be portable between
platforms, the calling application is responsible for converting this
information from cannonical to host format.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE - Continue processing.  Domino or Notes will prompt the user
for a password.  

ERR\_BSAFE\_EXTERNAL\_PASSWORD - Use the value in the retPassword for the new
password and do not have Domino or Notes prompt the user.  

ERR\_BSAFE\_USER\_ABORT - The password request was canceled.  

ERR\_BSAFE\_PASSWORD\_REQUIRED - A password is required for this id file.  

  

  

retLength  -  Return the length of the password here.  

  

retPassword  -  Return the password here.  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





