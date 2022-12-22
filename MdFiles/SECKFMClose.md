




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



**Function : IDs**



**SECKFMClose** **- Close an
ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMClose(**  

      KFHANDLE \*phKFC,  

      DWORD  Flags,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This routine
will close the ID file.  If the Flags parameter is set it will write the
information contained in the handle out to the ID file specified, otherwise it
will clear the handle passed in and set it to NULL before closing it.


 


**Parameters :**



Input :  

phKFC  -  Pointer to id file handle to be closed.  

  

Flags  -  Write the information contained in the handle out to ID file
otherwise set to 0.  See SECKFM\_close\_WriteIdFile in SECKFM\_xxx.  

  

Reserved  -  Reserved for future use, should be set to 0.  

  

pReserved  -  Reserved for future use, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - action successful  

  

  




 **See Also :**


**[SECKFMOpen](SECKFMOpen.md)**


**[SECKFM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F9283FFA09C26B8585256DD4004E288F)**



----------------------------------------------------------------------------------------------------------


 





