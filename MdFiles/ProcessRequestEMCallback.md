




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



**Function : Extension Manager**



**ProcessRequestEMCallback** **- Extension
Manager callback for EM\_ADMINPPROCESSREQUEST,**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **ProcessRequestEMCallback(**  

      NOTEHANDLE  nhRequest,  

      NOTEHANDLE  nhResponse**);**



**Description :**



This
callback enables you to extend the Administration Process.  For example, you
can generate additional administration requests and store them in the Aministration
Requests database.  


 


The
EM\_ADMINPPROCESSREQUEST occurs prior to and after the Administration Process
has processed a request on a server.


 


Note: 
Extensions to the Administration Process should not modify database ACLs
because their actions could conflict with the Administration Process's standard
ACL modification operations.


 


**Parameters :**



Input :  

nhRequest  -  The handle of the Admin Request note.  

  

nhResponse  -  The handle of the Admin Log note.  After the Administration
Process performs the Administration Request, the "$AdminpNoErrorDbs"
field of the AdminLog has a text list of the databases that were successfully
processed by the request and the "$AdminpErrorDbs" field of the
AdminLog has a text list of the databases that logged an error when the request
was processed.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE  

  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





