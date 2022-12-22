




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




**Initial Release 4.6**



**Symbolic Value : Rich Text**



**PABFLAG2\_xxx** **-** CDPABDEFINITION
- Flags2


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      PABFLAG2\_HIDE\_WEB        -  Hide paragraph when viewed with
a Web browser.  

  

      PABFLAG2\_CHECKEDLIST              -  Set if check list is checked off.  

  

      PABFLAG2\_LM\_OFFSET      -  LeftMargin is an offset value.  

  

      PABFLAG2\_LM\_PERCENT   -  LeftMargin is a percentage value.  

  

      PABFLAG2\_FLLM\_OFFSET              -  First Line LeftMargin is an offset
value.  

  

      PABFLAG2\_FLLM\_PERCENT           -  First Line LeftMargin is a percentage
value.  

  

      PABFLAG2\_RM\_OFFSET     -  RightMargin is an offset value.  

  

      PABFLAG2\_RM\_PERCENT   -  RightMargin is a percentage value.  

  

      PABFLAG2\_LM\_DEFAULT    -  LeftMargin Default.  

  

      PABFLAG2\_FLLM\_DEFAULT            -  First Line LeftMargin Default.  

  

      PABFLAG2\_RM\_DEFAULT   -  RightMargin Default.  

  

      PABFLAG2\_CIRCLELIST      -  Paragraph contains a circle list.  

  

      PABFLAG2\_SQUARELIST    -  Paragraph contains a square list.  

  

      PABFLAG2\_UNCHECKEDLIST         -  Set if check list is unchecked.  

  

      PABFLAG2\_BIDI\_RTLREADING       -  Set if right to left reading order.  

  

      PABFLAG2\_MORE\_FLAGS   -  Set if one or two DWORD extensions follow
CDPABDEFINITION.  

  

      PABFLAG2\_HIDEBITS          -  PABFLAG2\_HIDE\_WEB  

  

      PABFLAG2\_CHECKLIST      -  Paragraph contains a check list -
PABFLAG2\_UNCHECKEDLIST | PABFLAG2\_CHECKEDLIST  

  

      PABFLAG2\_MARGIN\_DEFAULTS\_MASK     -  PABFLAG2\_LM\_DEFAULT |
PABFLAG2\_RM\_DEFAULT | PABFLAG2\_FLLM\_DEFAULT  

  

      PABFLAG2\_MARGIN\_MASK             -  PABFLAG2\_MARGIN\_STYLES\_MASK |
PABFLAG2\_MARGIN\_DEFAULTS\_MASK  

  

      PABFLAG2\_MARGIN\_STYLES\_MASK          -  PABFLAG2\_LM\_OFFSET |
PABFLAG2\_LM\_PERCENT | PABFLAG2\_FLLM\_OFFSET | PABFLAG2\_FLLM\_PERCENT |
PABFLAG2\_RM\_OFFSET | PABFLAG2\_RM\_PERCENT  

  

      PABFLAG2\_ROMANUPPERLIST      -  PABFLAG2\_CHECKEDLIST |
PABFLAG2\_CIRCLELIST  

  

      PABFLAG2\_ROMANLOWERLIST     -  PABFLAG2\_CHECKEDLIST | PABFLAG2\_SQUARELIST  

  

      PABFLAG2\_ALPHAUPPERLIST        -  PABFLAG2\_SQUARELIST |
PABFLAG2\_CIRCLELIST  

  

      PABFLAG2\_ALPHALOWERLIST       -  PABFLAG2\_CHECKEDLIST |
PABFLAG2\_SQUARELIST | PABFLAG2\_CIRCLELIST  

  




**Description :**



Possible
optional values for the Flags2 member of the CDPABDEFINITION structure.  These
symbols specify additional paragraph attribute flags.  If the Flags2 member of
CDPABDEFINITION is set to PABFLAG2\_MORE\_FLAGS, the CDPABDEFINITION may be
followed by a DWORD extension. If the value of this DWORD extension is
EXTENDEDPABFLAGS3, then a second DWORD extension may be present with a value of
PABFLAG3\_HIDE\_EE. These DWORD extensions follow the six R5 margin extension
WORDs, if they are present.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[EXTENDEDPABFLAGS3](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E48F9EDCE17226DF852569D7005F8FAF)**



----------------------------------------------------------------------------------------------------------


 





