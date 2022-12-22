




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




 


**Symbolic Value : Error Handling**



**ERR\_xxx** **-** Domino and
Notes error codes.


**----------------------------------------------------------------------------------------------------------**



**#include <xxxerr.h>**


 **Symbolic Values :**      ERR\_xxx      -  see Description  

  




**Description :**



Example
(from nsferr.h):


  

#define    
ERR\_NOT\_NSF   PKG\_NSF+1  

  errortext(ERR\_NOT\_NSF, "File is not a database")


 **Sample Usage :**


STATUS      error;  

char        szNotesError[MAX\_NOTES\_ERROR];  

  

if (error = NSFDbOpen(szName))  

{  

    OSLoadString(NULLHANDLE, ERR(error), szNotesError,  

                 MAX\_NOTES\_ERROR);  

    printf("Unable to open database: %s.\n", szNotesError);  

    return;  

}


 **See Also :**


**[ERR](ERR.md)**


**[errortext](errortext.md)**


**[OSLoadString](OSLoadString.md)**


**[PKG\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/32ECB9B5852E43FE85256984004DEC2B)**


**[STATUS](STATUS.md)**



----------------------------------------------------------------------------------------------------------


 





