




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



**SchContainer\_GetRequest** **- Get the
first request in a container.**


**----------------------------------------------------------------------------------------------------------**



**#include <schgtw.h>**



STATUS
LNPUBLIC **SchContainer\_GetRequest(**  

      DHANDLE  hCntnr,  

      HCNTNROBJ FAR \*rethRqst,  

      void FAR \* FAR \*retpRqst,  

      LIST FAR \* FAR \*retpNameList,  

      LIST FAR \* FAR \*repClientNames,  

      char FAR \* FAR \*retpNS**);**



**Description :**



This
function is used to get the first request in a container. Requests are used to
obtain free time information from a foreign system calendaring and scheduling
gateway.


 


**Parameters :**



Input :  

hCntnr  -  The container Handle  

  




Output :  

(routine)  -  NOERROR - Successfully got the request.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

  

rethRqst  -  Points to where we return the handle to the request.  

  

retpRqst  -  Points to where we return the pointer to the request.  

  

retpNameList  -  Points to where we return the list of names to query.  

  

repClientNames  -  Points to list of clients names doing the query.  

  

retpNS  -  Points to name of Lotus Domino Server to chain to.  

  




 **See Also :**


**[SchContainer\_FreeRequest](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/F8E36ABDBF2014E4482573FB00323576)**



----------------------------------------------------------------------------------------------------------


 





