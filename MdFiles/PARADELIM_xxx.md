




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




 


**Symbolic Value : Rich Text**



**PARADELIM\_xxx** **-** Paragraph
recognition method.


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**


 **Symbolic Values :**      PARADELIM\_BLANKLINE     -  New paragraph on each blank line.  

  

      PARADELIM\_INDENTEDLINE          -  New paragraph on any indented line.  

  

      PARADELIM\_ANYBLANKLINE          -  New paragraph on each blank line, hard
CRs on each line. Note: PARADELIM\_ANYBLANKLINE sets justification = None.  

  

      PARADELIM\_ANYLINE         -  New paragraph on each line.  

  

      PARADELIM\_COLON           -  New paragraph on lines of the form
"fieldname: text".  

  

      PARADELIM\_RTLREADING             -  New paragraph on RTL reading order.  

  




**Description :**



WORD flag
used as 5th argument to ConvertItemToCompositeExt.  During conversion of plain
LMBCS text or an existing TYPE\_TEXT item to a TYPE\_COMPOSITE item, the location
of logical paragraphs must be determined and their presentation preserved by
building the appropriate Composite Data records into the converted item.  The
Notes Workstation application uses this information to correctly present the
Rich Text body to the user.


 **See Also :**


**[ConvertItemToCompositeExt](ConvertItemToCompositeExt.md)**



----------------------------------------------------------------------------------------------------------


 





