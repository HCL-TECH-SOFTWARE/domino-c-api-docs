




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



**DUSGetGroupInformation** **- Get group
information for display.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSGetGroupInformation(**  

      DHANDLE  hContext,  

      char \*GroupName,  

      NOTEHANDLE  hGroupNote**);**



**Description :**



Returns full
information about the group for display immediately after the administrator has
selected the group from the available list.


 


**Parameters :**



Input :  

hContext  -  Handle to this DUS' specific context information.  

  

GroupName  -  Name of the group selected (originally supplied by the DUS with
DUSRetrieveGroups)  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

hGroupNote  -  A handle to the group note.  

  




 **See Also :**


**[DUSGetUserInformation](DUSGetUserInformation.md)**



----------------------------------------------------------------------------------------------------------


 





