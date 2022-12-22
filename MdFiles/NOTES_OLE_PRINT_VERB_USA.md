




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




 


**Symbolic Value : OLE**



**NOTES\_OLE\_PRINT\_VERB\_USA** **-** U. S.
English print verb


**----------------------------------------------------------------------------------------------------------**



**#include <olenotes.h>**



**Description :**



If you want
your OLE object to receive the NOTES\_DOC\_INFO\_MSG message when the document
containing your objects is printed, then your application must handle an
OleActivate() using the predefined printing verb named "Print" (for
USA), or translated to the localized country translation, which matches that of
the translation used by Domino and Notes.  Domino and Notes actually store the
localized string "Print" in its string resources, and does not
actually use this constant in compiled code.  However, it is defined as a
convenience to Domino and Notes C API developers as a reference.


 




----------------------------------------------------------------------------------------------------------


 





