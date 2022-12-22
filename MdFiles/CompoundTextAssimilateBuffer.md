




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Function : Compound Text** 



**CompoundTextAssimilateBuffer** **- Append
the contents in PABID's (Personal Address Book ID's )  of a compound text
buffer to a compound text context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS **CompoundTextAssimilateBuffer(**  

      DHANDLE  hCompound,  

      void \*pvData,  

      DWORD  dwDataLen**);**



**Description :**




Append
the contents of a compound text buffer to a compound text context. 


 


The
contents are adjust  in that PABID's (Personal Address Book ID's ) and styles
defined in the source are renumbered and/or renamed as necessary to fit into
the destination context.


 


**Parameters :**



Input :  

hCompound  -  Compound context handle.  

  

pvData  -  Void pointer to store the data.  

  

dwDataLen  -  Length, in bytes, of the data provide in pData.  

  




Output :  

(routine)  -  if error ,returns ERR\_MISC\_INVALID\_ARGS error ,else NOERROR.  

  

  




 **Sample Usage :**


      void
\*pvData = OSLock(void, hMainOutputBuffer); 


            DWORD
dwLen = 0; 


            STATUS
error = OSMemGetSize(hMainOutputBuffer, &dwLen); 


            if
(NOERROR == error) 


                        error
= CompoundTextAssimilateBuffer(hCompound, pvData, dwLen); 


            OSUnlock(hMainOutputBuffer);


 **See Also :**




----------------------------------------------------------------------------------------------------------


 





