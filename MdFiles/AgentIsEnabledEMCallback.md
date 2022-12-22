




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




**Initial Release 5.0.2**



**Function : Extension Manager**



**AgentIsEnabledEMCallback** **- Extension
Manager callback for EM\_AGENTISENABLED**


**----------------------------------------------------------------------------------------------------------**



**Note:** This function is only available as an Extension Manager callback
-- you cannot call this function directly.


 


**#include <extmgr.h>**



STATUS
LNPUBLIC **AgentIsEnabledEMCallback(**  

      HAGENT  hAgent,  

      BOOL \*return\_value**);**



**Description :**



Though
AgentIsEnabled is a publicly-defined function, its extension manager callback
has a slightly different signature because of the fact that the public function
returns BOOL instead of STATUS.  The extension manager callback has an added
argument which allows the callback to write the return value of the API
routine.  For purposes of the callback, it is as if the function signatures
were as follows:


 


**Parameters :**



Input :  

hAgent  -  Handle of Agent.  

  




Output :  

(routine)  -    

ERR\_EM\_CONTINUE  

  

  

return\_value  -  TRUE - agent is enabled.  FALSE - agent isn't enabled.  

  




 **See Also :**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





