




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




 


**Symbolic Value : DDE**



**DDEFLAGS\_xxx** **-** Specifies
DDE link type.


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      DDEFLAGS\_AUTOLINK        -  Link type == Automatic (hot).  

  

      DDEFLAGS\_MANUALLINK   -  Link type == Manual (warm).  

  

      DDEFLAGS\_EMBEDDED      -  Embedded document exists.  

  

      DDEFLAGS\_INITIATE          -  Used on paste to indicate not to prompt
user to initiate link.  

  

      DDEFLAGS\_CDP     -  Used on paste to indicate that server uses Compound
Document protocol.  

  

      DDEFLAGS\_NOTES\_LAUNCHED     -  Used on CDP paste/load to indicate that
Notes launched the application to establish original conversation.  

  

      DDEFLAGS\_CONV\_ACTIVE             -  Used on non-CDP paste/load to
indicate that conversation is already active.  

  

      DDEFLAGS\_EMBEDEXTRACTED    -  Used on non-CDP paste/load to indicate that
Notes extracted the embedded file so that it may later be closed.  

  

      DDEFLAGS\_NEWOBJECT   -  Set if this DDE Range is a new inserted object
which contains no embedded object yet, i.e. a "blank" object.  

  




**Description :**



These values
specify the DDE link flag used in the structure, CDDDEBEGIN.


 **See Also :**


**[CDDDEBEGIN](CDDDEBEGIN.md)**



----------------------------------------------------------------------------------------------------------


 





