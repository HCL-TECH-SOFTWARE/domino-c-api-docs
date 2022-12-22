




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




**Initial Release 5.0**



**Function : Domino Upgrade Services**



**DUSGetUserInformation** **- Get Full
User Information for this User to be migrated.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSGetUserInformation(**  

      DHANDLE  hContext,  

      char \*UserName,  

      NOTEHANDLE  hUserNote,  

      DWORD  TotalLeftToRead**);**



**Description :**



This call
supplies the upgrade DLL with full user information for the user selected.


 


**Parameters :**



Input :  

hContext  -  Handle to this DUS' specific context information.  

  

UserName  -  Name of the user to obtain information for.  Originally supplied
to the DUS framework with DUSRetrieveUsers().  

  

hUserNote  -  Handle to the note which contains the User information
requested.  It is used by the DUS to identify the user for which full
information is being requested.  The hUserNote should NOT be updated or closed
by the DUS.  The DUS framework (caller) writes additional fields to this note
and will update/close the hUserNote appropriately.   

  

TotalLeftToRead  -  The number of selected users for which full information
still needs to be returned by the DUS.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  




 **See Also :**


**[DUSGetGroupInformation](DUSGetGroupInformation.md)**



----------------------------------------------------------------------------------------------------------


 





