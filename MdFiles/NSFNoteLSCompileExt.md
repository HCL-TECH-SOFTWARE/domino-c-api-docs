




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




**Initial Release 7.0**



**Function : LotusScript**



**NSFNoteLSCompileExt** **- Extended
form of NSFNoteLSCompile**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteLSCompileExt(**  

      DBHANDLE  hDb,  

      NOTEHANDLE  hNote,  

      DWORD  dwFlags,  

      LSCOMPILEERRPROC  pfnErrProc,  

      void\*pCtx**);**



**Description :**



This API is
an extended form of NSFNoteLSCompile which returns additional error information
if there are any compilation errors when LotusScript code within the note is
compiled.


 


**Parameters :**



Input :  

hDb  -  Handle to the note containing LotusScript modules.  

  

hNote  -  Handle to the note containing LotusScript modules.  

  

dwFlags  -  (Reserved for future use) Must be 0.  

  

pfnErrProc  -  pointer to a callback function that is called if there are any
compilation errors  

  

pCtx  -  pointer to user-defined data which allows the application to pass
contextual data to the callback function.  

  




Output :  

(routine)  -  (routine)  -  Return indicates either success or what the error
is. The return codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_NULL\_NOTEHANDLE -  if hNote was not specified.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  

  

  




 **See Also :**


**[LSCOMPILEERRPROC](LSCOMPILEERRPROC.md)**


**[LSCOMPILE\_ERR\_INFO;](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/DA2041A0EDFF851D482570BB0059A6A1)**


**[NSFNoteLSCompile](NSFNoteLSCompile.md)**



----------------------------------------------------------------------------------------------------------


 





