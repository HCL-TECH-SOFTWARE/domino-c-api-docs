




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




**Initial Release 6**



**Function : Rich Text**



**EVSetSimpleViewShowCurrentThread** **- Sets the
EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD flag.**


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



void **EVSetSimpleViewShowCurrentThread(**  

      CDEMBEDDEDVIEW \*pEView,  

      BOOL  fSet**);**



**Description :**



To set the
EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD flag on or off in the Flags
member of the CDEMBEDDEDVIEW structure.  Implemented as a macro:


 


#define
EVSetSimpleViewShowCurrentThread(pEView,fSet) \


            {\


                        if
( fSet ) (pEView)->Flags |=
EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD;\


                        else
(pEView)->Flags &= ~EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD;\


            }


 


**Parameters :**



Input :  

pEView  -  Pointer to the CDEMBEDDEDVIEW structure.  

  

fSet  -  TRUE to set the EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD flag
on.  FALSE  to set the EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_SHOW\_CURRENT\_THREAD flag
off.  

  




 


 **See Also :**


**[CDEMBEDDEDVIEW](CDEMBEDDEDVIEW.md)**


**[EMBEDDEDVIEW\_FLAG\_xxx](EMBEDDEDVIEW_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





