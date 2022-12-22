




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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



**DUSExtendedErrorText** **- Retrieves
the text to be displayed in the event of an error calling the DUS extension
DLL.**


**----------------------------------------------------------------------------------------------------------**



**#include <dus.h>**



void
LNCALLBACK **DUSExtendedErrorText(**  

      DHANDLE  hContext,  

      char \*ErrorBuffer,  

      WORD  BufferLen,  

      WORD \*pErrorLevel**);**



**Description :**



This call
retrieves the text to be displayed in the event that a call to the DUS
application fails and the DUS application wishes to return its own error
string. 


 


**Parameters :**



Input :  

hContext  -  handle to this DUS' specific context information.  

  

BufferLen  -  Length of ErrorBuffer.  

  




Output :  

(routine)  -  None.  

  

  

ErrorBuffer  -  LMBCS string passed to the DUS framework for display.  

  

pErrorLevel  -  pointer to one of three error level flags supplied by the DUS. 
This value determines how the error message box will be displayed.  Please
refer to DUS\_ERROR\_LEVEL\_xxx.  

  




 **Sample Usage :**



#define
PKG\_DUS                                      PKG\_ADDIN


#define
STR\_DUS\_ERR\_NOFILE                   (PKG\_DUS+7)


typedef
struct  

{  

        HMODULE                hDUSModule;  

        WORD                          ExtendedError;  

        WORD                          ExtendedErrorLevel;  

        DUSPROGRESSBARPROC     ProgressBarProc;  

        DUSLOGEVENTPROC               LogEventProc;  

}DUS\_CONTEXT, \*PDUS\_CONTEXT;


 


        ....


        error
= ERR\_DUS\_EXTENDED\_ERROR;  

        pDUSCtx->ExtendedError = STR\_DUS\_ERR\_NOFILE;  

        pDUSCtx->ExtendedErrorLevel = DUS\_ERROR\_LEVEL\_ERROR; /\* Going to
gracefully shutdown \*/


        ....


        return(error);


 **See Also :**


**[DUS\_ERROR\_LEVEL\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/C62FC173C2DC05A4852566760040D547)**



----------------------------------------------------------------------------------------------------------


 





