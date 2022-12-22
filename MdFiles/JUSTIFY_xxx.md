




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




 


**Symbolic Value : Miscellaneous**



**JUSTIFY\_xxx** **-** Definitions
for the JustifyMode member of the CDPABDEFINITION structure.


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      JUSTIFY\_LEFT        -  Paragraphs will be aligned along the
left margin.  

  

      JUSTIFY\_RIGHT      -  Paragraphs will be aligned along the right margin.  

  

      JUSTIFY\_BLOCK     -  Paragraphs will be aligned along both the left
margin and the right margin. Spaces between words will be added as necessary
(this is also known as full justification).  

  

      JUSTIFY\_CENTER   -  Paragraphs will be centered.  

  

      JUSTIFY\_NONE       -  No line wrapping will only occur except on explicit
carriage returns.  

  




**Description :**



These
symbols define how paragraphs will be aligned or justified in a rich text
field.


 **Sample Usage :**


  
pabdef.Header.Signature = SIG\_CD\_PABDEFINITION;  

    pabdef.Header.Length = ODSLength( \_CDPABDEFINITION );  

    pabdef.PABID = PARA\_STYLE\_ID;  

    pabdef.JustifyMode = JUSTIFY\_CENTER;  

    pabdef.LineSpacing = DEFAULT\_LINE\_SPACING;  

    pabdef.ParagraphSpacingBefore = DEFAULT\_ABOVE\_PAR\_SPACING;  

    pabdef.ParagraphSpacingAfter = DEFAULT\_BELOW\_PAR\_SPACING;  

    pabdef.LeftMargin = DEFAULT\_LEFT\_MARGIN;  

    pabdef.RightMargin = DEFAULT\_RIGHT\_MARGIN;  

    pabdef.FirstLineLeftMargin = DEFAULT\_FIRST\_LEFT\_MARGIN;  

    pabdef.Tabs = DEFAULT\_TABS;  

    pabdef.Tab[0] = DEFAULT\_TAB\_INTERVAL;  

    pabdef.Flags = 0;


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**



----------------------------------------------------------------------------------------------------------


 





