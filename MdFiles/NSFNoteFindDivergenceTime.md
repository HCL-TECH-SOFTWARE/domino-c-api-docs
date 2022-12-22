




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



**Function : Note**



**NSFNoteFindDivergenceTime** **- Find when
two notes were last in synch.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteFindDivergenceTime(**  

      NOTEHANDLE  hNote1,  

      NOTEHANDLE  hNote2,  

      DWORD  dwFlags,  

      TIMEDATE \*tdLastSyncTime**);**



**Description :**



This routine
returns the last TIMEDATE two notes were in synch (ie replicated).


 


**Parameters :**



Input :  

hNote1  -  Handle to the first note.  

  

hNote2  -  Handle to the second note.  

  

dwFlags  -  Reserved for future use.  Must be set to 0L.  

  




Output :  

(routine)  -  NOERROR - Successfully found the last synch time.  

ERR\_SYNC\_TIME\_NOT\_FOUND - The two notes do not have a common revision time.  

ERR\_xxx - There are many possible errors. It is best to use the code in a call
to OSLoadString and display/log the error for the user as your default error
handling.  

  

  

tdLastSyncTime  -  TIMEDATE when the notes were last in synch.  

  




 **See Also :**


**[NSFDbGetNoteInfo](NSFDbGetNoteInfo.md)**



----------------------------------------------------------------------------------------------------------


 





