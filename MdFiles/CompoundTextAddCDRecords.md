




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




**Initial Release 5.0.4**



**Function : Compound Text**



**CompoundTextAddCDRecords** **- Add CD
records to an existing CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAddCDRecords(**  

      DHANDLE  hCompound,  

      void \*pvRecord,  

      DWORD  dwRecordLength**);**



**Description :**



This function
adds a buffer of formatted CD records to an existing CompoundText context.


 


**Parameters :**



Input :  

hCompound  -  Handle of CompoundText context.  

  

pvRecord  -  A pointer to a buffer of formatted CD records.  

  

dwRecordLength  -  The length of the buffer.  

  




Output :  

(routine)  -  (routine)  -    Return status from this call:   

  

NOERROR - Successfully added the buffer to the CompoundText context.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **See Also :**


**[CompoundTextClose](CompoundTextClose.md)**


**[CompoundTextCreate](CompoundTextCreate.md)**



----------------------------------------------------------------------------------------------------------


 





