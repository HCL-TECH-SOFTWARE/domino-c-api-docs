




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




**Initial Release 5.0.3**



**Symbolic Value : Constants;
Extension Manager**



**AUTHEM\_xxx** **-** Authentication
Extension Manager events


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**


 **Symbolic Values :**      AUTHEM\_StartAuthentication            -  An
EM\_SECAUTHENTICATION wEvent calling parameter indicating the callback should
initiate it's additional authentication protocol - WORD (0x0000).  

  

      AUTHEM\_Poll          -  An EM\_SECAUTHENTICATION wEvent calling parameter
indicating the callback has been invoked again after a delay for additional
processing - WORD (0x0001).  

  

      AUTHEM\_Identify     -  An EM\_SECAUTHENTICATION wEvent calling parameter
indicating the first authentication of the registered Extension Manager
callback. This callback expects a uniquely labeled null terminated text string
to be returned in the pName parameter that identifies the 3rd party
authentication extension - WORD (0x0002).  

  

      AUTHEM\_Terminate             -  An EM\_SECAUTHENTICATION wEvent calling
parameter indicating the session is closing and may have failed - WORD
(0x0003).  

  




**Description :**



The
Authentication Extension Manager EM\_SECAUTHENTICATION wEvent calling
parameters.


 **See Also :**


**[AuthenticationEMCallback](AuthenticationEMCallback.md)**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**


**[fAuth\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F632254A786B5BE7852568AB00535370)**



----------------------------------------------------------------------------------------------------------


 





