




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




**Initial Release 4.0**



**Symbolic Value : Limits**



**OLDMAXPATH** **-** Maximum
pathname (backward-compatible version).


**----------------------------------------------------------------------------------------------------------**



**#include <names.h>**



**Description :**



Before
Release 4 of the Notes C API, MAXPATH was 256 for the Macintosh, Netware, and
Unix platforms.  For all other platforms, it was 100.  Release 4 included
support for Windows 32-bit long filenames, requiring MAXPATH to be increased to
256.  For backwards compatibility, OLDMAXPATH is defined and has the same
definition of MAXPATH in Release 3 and earlier.  The MAXPATH definition in
Release 4 and later release is 256 for all platforms.


 **See Also :**


**[MAXPATH](MAXPATH.md)**



----------------------------------------------------------------------------------------------------------


 





