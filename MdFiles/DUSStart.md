




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



**DUSStart** **-
Initializes the DUS (Domino Upgrade Services) environment.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



STATUS
LNCALLBACK **DUSStart(**  

      HMODULE  hInstance,  

      DHANDLE \*pRethContext,  

      NOTEHANDLE  hUserNote,  

      DWORD \*pRetInitFlags,  

      DUSPROGRESSBARPROC  DUSProgressBar,  

      DUSLOGEVENTPROC  DUSLogEvent**);**



**Description :**



This
function notifies the DUS of one of two situations:


      1)         It
has been selected from the Foreign Directory Import source list in the Foreign
Directory Import dialog.


      2)         The
first of possibly several users retrieved from this DUS is about to be
registered with Domino Administration.


It also
supplies the DUS framework with a context handle, which will be passed back to
the DUS with every subsequent DUS.... function call.  


 


**Parameters :**



Input :  

hInstance  -  Instance handle to the DUS DLL.  

  

hUserNote  -  this note handle will only be valid  (non-NULL) if DUSStart() is
called just prior to user registration.  When DUSStart() is called from the
Foreign Directory dialog, hUserNote will be NULLHANDLE and the DUS allocates
and initializes a context buffer for the first time.  

  

pRetInitFlags  -  DUS Initialization flags.  Refer to fDUSxxx.  

  

DUSProgressBar  -  pointer to a callback function used by the DUS to display
progress on potentially lengthy operations, such as user retrieval.  

  

DUSLogEvent  -  pointer to a callback function used by the DUS to log progress
to the Domino log on any operation, such as user retrieval.  

  




Output :  

(routine)  -  Return status from the call -- indicates either success (NOERROR)
or what the error is.  

  

  

pRethContext  -  pointer to a context handle the DUS can optionally
allocate/return to the DUS framework.  On every subsequent call to the DUS in
the current session, this context handle will be passed to the DUS by the DUS
framework.  The DUS is responsible for freeing this handle in DUSStop().  Can
be NULL.  

  




 **See Also :**


**[DUSLOGEVENTPROC](DUSLOGEVENTPROC.md)**


**[DUSPROGRESSBARPROC](DUSPROGRESSBARPROC.md)**


**[fDUSxxx](fDUSxxx.md)**



----------------------------------------------------------------------------------------------------------


 





