




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




**Initial Release 5.0**



**Symbolic Value : Constants; Rich
Text**



**CDRESOURCE\_TYPE\_xxx** **-** CDRESOURCE
Type


**----------------------------------------------------------------------------------------------------------**



**#include <rsrcods.h>**


 **Symbolic Values :**      CDRESOURCE\_TYPE\_EMPTY        -  Empty  

  

      CDRESOURCE\_TYPE\_URL             -  CDRESOURCE type is a URL.  

  

      CDRESOURCE\_TYPE\_NOTELINK   -  CDRESOURCE type is a NoteLink.  

  

      CDRESOURCE\_TYPE\_NAMEDELEMENT    -  CDRESOURCE type is a NamedElement.  

  

      CDRESOURCE\_TYPE\_NOTEIDLINK            -  Currently not written to disk
only used in RESOURCELINK.  

  

      CDRESOURCE\_TYPE\_ACTION       -  This would be used in conjunction with
the formula flag. The formula is an @Command that would perform some action,
typically it would also switch to a Notes UI element. This will be used to
reference the replicator page and other UI elements.  

  

      CDRESOURCE\_TYPE\_NAMEDITEMELEMENT        -  Currently not written to disk.
Only used in RESOURCELINK.  

  

      CDRESOURCE\_TYPE\_RESERVERS            -  Defines the maximum value set for
future use on CDRESOURCE types.  

  




 **See Also :**


**[CDRESOURCE](CDRESOURCE.md)**



----------------------------------------------------------------------------------------------------------


 





