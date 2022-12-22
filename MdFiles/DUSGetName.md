




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



**DUSGetName** **- Provide
UI string immediately after the DUS dll is loaded.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSGetName(**  

      HMODULE  hInstance,  

      char \*DUSNameBuf,  

      WORD  DUSNameBufLen,  

      char \*DUSDescriptionBuf,  

      WORD  DUSDescriptionBufLen**);**



**Description :**



This call
notifies the upgrade DLL that the upgrade dialog is being displayed.  It also
passes in the instance handle of the DUS, which the DUS may want to store for
later DUS operations.


 


**Parameters :**



Input :  

hInstance  -  instance handle of this DUS.  

  

DUSNameBufLen  -  size of the DUSNameBuf.  

  

DUSDescriptionBufLen  -  size of the DUSDescriptionbuf.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

DUSNameBuf  -  buffer into which the DUS will copy the name of the DUS as it
will appear in the Foreign Directory Source listbox (in the upgrade dialog).  

  

DUSDescriptionBuf  -  buffer into which the DUS will copy a brief description
of the DUS as it will appear in the upgrade dialog.  

  




 




----------------------------------------------------------------------------------------------------------


 





