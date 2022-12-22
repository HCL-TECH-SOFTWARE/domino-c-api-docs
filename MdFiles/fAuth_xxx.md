




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



**Symbolic Value : Extension Manager**



**fAuth\_xxx** **-** Authentication
Extension Manager flags


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**


 **Symbolic Values :**      fAuthRoleServer       -  This flag is set to indicate that
the callback is being called during authentication in the role of the server.  

  

      fAuthRolePassthruServer      -  This flag is set when the client is
authenticating with the server with the intention of using the server as a
passthru server.  

  

      fAuthClientViaPassthruServer           -  This flag is set when the
client is accessing the server thru a passthru server. The network address in
this case is the address of the passthru server ( not the client).  

  




**Description :**



Authentication
Extension Manager flags that indicate details of authentication role and state.


 **See Also :**


**[AUTHEM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/0BB02A45BD3FBDD5852568AB00535371)**


**[AuthenticationEMCallback](AuthenticationEMCallback.md)**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





