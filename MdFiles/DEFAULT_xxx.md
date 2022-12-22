




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



**DEFAULT\_xxx** **-** Various
default settings for Paragraph Attribute Blocks, table cells, and layout
regions.


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      DEFAULT\_JUSTIFICATION   -  JUSTIFY\_LEFT  

  

      DEFAULT\_LINE\_SPACING   -  0  

  

      DEFAULT\_ABOVE\_PAR\_SPACING   -  0  

  

      DEFAULT\_BELOW\_PAR\_SPACING              -  0  

  

      DEFAULT\_LEFT\_MARGIN    -  ONEINCH  

  

      DEFAULT\_FIRST\_LEFT\_MARGIN    -  DEFAULT\_LEFT\_MARGIN  

  

      DEFAULT\_RIGHT\_MARGIN             -  0  

  

Note: Right Margin = "0" means [DEFAULT\_RIGHT\_GUTTER] inches from
right edge of paper, regardless of paper width.  

  

      DEFAULT\_RIGHT\_GUTTER             -  ONEINCH  

  

      DEFAULT\_PAGINATION      -  0  

  

Note: Tabs are relative to the absolute left edge of the paper.  

  

      DEFAULT\_FLAGS2   -  0  

  

      DEFAULT\_MARGIN\_STYLE             -  PABFLAG2\_LM\_OFFSET |
PABFLAG2\_RM\_OFFSET  

  

      DEFAULT\_TABS      -  0  

  

      DEFAULT\_TAB\_INTERVAL   -  (ONEINCH/2)  

  

      DEFAULT\_TABLE\_HCELLSPACE     -  0  

  

      DEFAULT\_TABLE\_VCELLSPACE     -  0  

  

      DEFAULT\_LAYOUT\_LEFT    -  DEFAULT\_LEFT\_MARGIN  

  

      DEFAULT\_LAYOUT\_WIDTH             -  (ONEINCH \* 6)  

  

      DEFAULT\_LAYOUT\_HEIGHT           -  (3 \* ONEINCH / 2)  

  

      DEFAULT\_LAYOUT\_ELEM\_WIDTH              -  (4 \* ONEINCH / 3) /\* 1.333 inch
\*/  

  

      DEFAULT\_LAYOUT\_ELEM\_HEIGHT            -  (ONEINCH / 5)  

  




**Description :**



Various
default settings for Paragraph Attribute Blocks, table cells, and layout
regions.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[CDTABLEBEGIN](CDTABLEBEGIN.md)**


**[ELEMENTHEADER](ELEMENTHEADER.md)**



----------------------------------------------------------------------------------------------------------


 





