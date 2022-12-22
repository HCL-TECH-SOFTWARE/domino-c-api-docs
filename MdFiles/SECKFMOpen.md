




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



**SECKFMOpen** **- Open an
ID file.**


**----------------------------------------------------------------------------------------------------------**



**#include <kfm.h>**



STATUS
LNPUBLIC **SECKFMOpen(**  

      KFHANDLE \*phKFC,  

      char \*pIDFileName,  

      char \*pPassword,  

      DWORD  Flags,  

      DWORD  Reserved,  

      void \*pReserved**);**



**Description :**



This routine
will read all the information in the ID file and return a handle to it.


 


**Parameters :**



Input :  

  

pIDFileName  -  Name of ID file to be read.  

  

pPassword  -  Null terminated password string.  

  

Flags  -  Zero or SECKFM\_open\_All will read all information out of the id
file.  See SECKFM\_xxx.  

  

Reserved  -  Reserved for future use, should be set to zero.  

  

pReserved  -  Reserved for future use, should be set to NULL.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is.   The return codes include:  

  

NOERROR - action successful  

  

  

phKFC  -  ID file handle to be passed back upon successful opening of the id
file.  

  




 **See Also :**


**[SECKFM\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F9283FFA09C26B8585256DD4004E288F)**



----------------------------------------------------------------------------------------------------------


 





