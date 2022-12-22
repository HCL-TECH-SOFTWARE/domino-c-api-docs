




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



**EMCreateRecursionID** **- Returns a
recursion ID for use with EMRegister().**


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**



STATUS
LNPUBLIC **EMCreateRecursionID(**  

      WORD far \*retRecursionID**);**



**Description :**



The
recursion ID is used in Domino or Notes core to resolve any recursion issues
that might arise from the callback function making a call to core functions
(for example, calling NSFDbOpen() from an extension manager hook for
NSFDbOpen()).  

  

If a recursion ID of zero is passed to EMRegister(), Domino or Notes will not
check for recursion.  The extension manager hook will always be called for that
function.


 


In order to
prevent recursion, a recursion ID must be obtained by calling
EMCreateRecursionID() and this recursion ID must be passed to EMRegister(). 
Domino or Notes will check before calling the extension manager hook to ensure
that the current thread has not already called the hook.  If it has, the call
to the extension manager hook is skipped.


 


**Parameters :**




Output :  

(routine)  -    

NOERROR  

ERR\_ILLEGALEXT  

  

  

retRecursionID  -  Returns recursion ID to be passed to EMRegister.  

  




 **See Also :**


**[EMRegister](EMRegister.md)**


**[EMHANDLER](EMHANDLER.md)**



----------------------------------------------------------------------------------------------------------


 





