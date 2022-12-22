




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



**EMRegister** **- Register
callback routine for specific NSF calls.**


**----------------------------------------------------------------------------------------------------------**



**#include <extmgr.h>**



STATUS
LNPUBLIC **EMRegister(**  

      EID  EmID,  

      DWORD  Flags,  

      EMHANDLER  Proc,  

      WORD  RecursionID,  

      HEMREGISTRATION far \*rethRegistration**);**



**Description :**



Register a
callback routine that will be called before or after (or before *and*
after) Domino or Notes performs a specified NSF function.


 


The
extension ID codes (EID) are described under EM\_xxx.


 


The
recursion ID is used in Domino or Notes core to resolve any recursion issues
that might arise from the callback function making a call to Domino or Notes
core functions (for example, calling NSFDbOpen() from an extension manager hook
for NSFDbOpen()).  

  

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



Input :  

EmID  -  The extension id of the specific NSF call.  See definition of EM\_xxx
for permissible values.  

  

Flags  -  Indicates when the registered callback function is to be called. Use
EM\_REG\_BEFORE if the callback function is to be called before Domino or Notes
performs the NSF function.  Use EM\_REG\_AFTER  if the callback function is to be
called after Domino or Notes performs the NSF function.  They can be ORed
together to have the callback function called both before and after the NSF
function.  

  

            #define EM\_REG\_BEFORE             0x0001  

            #define EM\_REG\_AFTER                0x0002  

  

Proc  -  User-written callback function.  

  

RecursionID  -  Unique Id created by a call to EMCreateRecursionID that is used
to resolve recursion problems if calls are made to the C API from inside the
callback function.  Passing 0 will eliminate the overhead related to checking
for recursion problems.  

  




Output :  

(routine)  -    

NOERROR  

ERR\_EM\_ILLEGALFLAGS  

ERR\_EM\_ILLEGAL  

  

  

rethRegistration  -  Handle to be used when de-registering.  

  




 **See Also :**


**[EMCreateRecursionID](EMCreateRecursionID.md)**


**[EMDeregister](EMDeregister.md)**


**[EMHANDLER](EMHANDLER.md)**


**[EM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CCB2911F1DF6C7AF8525681000480140)**



----------------------------------------------------------------------------------------------------------


 





