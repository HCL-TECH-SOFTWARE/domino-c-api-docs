




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



**SchContainer\_DupHandle** **- Duplicate
the container handle.**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **SchContainer\_DupHandle(**  

      HCNTNR  hOrigCntnr,  

      HCNTNR FAR \*phDup**);**



**Description :**



This routine
duplicates the handle to a container. The new container handle is valid in the
context of the current process. This is used by gateways because they receive
requests for schedules in a container. They use this call to instantiate the
handle in the context of their process. This insures that Domino won't free the
container memory until both processes release the handle by calling
SchContainer\_Free.


 


**Parameters :**



Input :  

hOrigCntnr  -  The container handle to be duplicated.  

  




Output :  

(routine)  -  NOERROR - Successfully duplicated a container handle.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  

phDup  -  Pointer to the newly duplicated container handle.  

  




 **See Also :**


**[SchContainer\_Free](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1B1F99C51F7DAA688525635D006DEB1C)**


**[SchContainer\_New](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E4EEE4DB09BC7FE78525635D006DAB79)**


**[SchRetrieve](SchRetrieve.md)**


**[SchSrvRetrieve](SchSrvRetrieve.md)**



----------------------------------------------------------------------------------------------------------


 





