




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



**EVIsSimpleViewMouseTrackOn** **- Returns
TRUE if EMBEDDEDVIEW\_FLAG\_SIMPLE\_MOUSE\_TRACK\_ON flag is set, FALSE otherwise.**


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**



BOOL **EVIsSimpleViewMouseTrackOn(**  

      CDEMBEDDEDVIEW \*pEView**);**



**Description :**



To see if
the EMBEDDEDVIEW\_FLAG\_SIMPLE\_MOUSE\_TRACK\_ON flag is set in the Flags member of
the CDEMBEDDEDVIEW structure.  Implemented as a macro:


 


#define
EVIsSimpleViewMouseTrackOn(pEView) ( (pEView)->Flags &
EMBEDDEDVIEW\_FLAG\_SIMPLE\_VIEW\_MOUSE\_TRACK\_ON )


 


**Parameters :**



Input :  

pEView  -  Pointer to the CDEMBEDDEDVIEW structure.  

  




Output :  

(routine)  -  TRUE if EMBEDDEDVIEW\_FLAG\_SIMPLE\_MOUSE\_TRACK\_ON flag is set,
FALSE otherwise.  

  

  




 **See Also :**


**[CDEMBEDDEDVIEW](CDEMBEDDEDVIEW.md)**


**[EMBEDDEDVIEW\_FLAG\_xxx](EMBEDDEDVIEW_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





