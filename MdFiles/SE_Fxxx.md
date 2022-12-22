




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




 


**Symbolic Value : Search**



**SE\_Fxxx** **-** SEARCH\_MATCH
- SERetFlags


**----------------------------------------------------------------------------------------------------------**



**#include <nsfsearc.h>**


 **Symbolic Values :**      SE\_FNOMATCH       -  Does not match formula (deleted or
updated).  

  

      SE\_FMATCH            -  Matches formula.  

  

      SE\_FTRUNCATED   -  Document truncated.  

  

      SE\_FPURGED          -  Note has been purged. Returned only when
SEARCH\_INCLUDE\_PURGED is used.  

  

      SE\_FNOPURGE       -  Note has no purge status. Returned only when
SEARCH\_FULL\_DATACUTOFF is used.  

  

      SE\_FSOFTDELETED           -  If SEARCH\_NOTIFYDELETIONS: note is soft
deleted; NoteClass&NOTE\_CLASS\_NOTIFYDELETION also on (off for hard delete).  

  




**Description :**



If
recompiling a V3 API application and you used the MatchesFormula field the
following code change should be made:  

For V3 -  

   1) if (SearchMatch.MatchesFormula == SE\_FMATCH)  

   2) if (SearchMatch.MatchesFormula == SE\_FNOMATCH)  

   3) if (SearchMatch.MatchesFormula != SE\_FMATCH) is equivalent to 2)  

   4) if (SearchMatch.MatchesFormula != SE\_FNOMATCH) is equivalent to 1)  

For V4 -  

   1) if (SearchMatch.SERetFlags & SE\_FMATCH)  

   2) if (!(SearchMatch.SERetFlags & SE\_FMATCH))


 **See Also :**


**[SEARCH\_MATCH](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B57006FA778)**



----------------------------------------------------------------------------------------------------------


 





