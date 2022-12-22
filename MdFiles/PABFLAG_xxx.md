




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



**PABFLAG\_xxx** **-** CDPABDEFINITION
- Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editdflt.h>**


 **Symbolic Values :**      PABFLAG\_PAGINATE\_BEFORE       -  Start new page with this
paragraph  

  

      PABFLAG\_KEEP\_WITH\_NEXT         -  Don't separate this and next paragraph  

  

      PABFLAG\_KEEP\_TOGETHER          -  Don't split lines in paragraph  

  

      PABFLAG\_PROPAGATE      -  Propagate even PAGINATE\_BEFORE and
KEEP\_WITH\_NEXT  

  

      PABFLAG\_HIDE\_RO            -  Hide paragraph in R/O mode  

  

      PABFLAG\_HIDE\_RW            -  Hide paragraph in R/W mode  

  

      PABFLAG\_HIDE\_PR             -  Hide paragraph when printing  

  

      PABFLAG\_DISPLAY\_RM      -  Not used in Relase 5.0 and later. In earlier
releases, this flag had to be set if the paragraph is in a table.  

  

      PABFLAG\_HIDE\_UNLINK     -  The pab was saved in Release 4. Set this bit
or the Notes client will assume the pab was saved pre-Release 4 and will thus
"link" these bit definitions (assign the right one to the left one)
since preview did not exist pre-Release 4:  

PABFLAG\_HIDE\_PV = PABFLAG\_HIDE\_RO  

PABFLAG\_HIDE\_PVE = PABFLAG\_HIDE\_RW  

  

      PABFLAG\_HIDE\_CO            -  Hide paragraph when copying/forwarding  

  

      PABFLAG\_BULLET   -  Display paragraph with bullet  

  

      PABFLAG\_HIDE\_IF   -  Use the hide when formula (if the formula is
present)  

  

      PABFLAG\_NUMBEREDLIST             -  Display paragraph with number  

  

      PABFLAG\_HIDE\_PV             -  Hide paragraph when previewing  

  

      PABFLAG\_HIDE\_PVE           -  Hide paragraph when editing in the preview
pane  

  

      PABFLAG\_HIDE\_NOTES      -  Hide paragraph from Notes clients  

  

      PABFLAG\_HIDEBITS           -  (PABFLAG\_HIDE\_RO | PABFLAG\_HIDE\_RW | PABFLAG\_HIDE\_CO
| PABFLAG\_HIDE\_PR | PABFLAG\_HIDE\_PV | PABFLAG\_HIDE\_PVE | PABFLAG\_HIDE\_IF |
PABFLAG\_HIDE\_NOTES)  

  




**Description :**



These
symbols may be used to set paragraph attributes in the Flags member of the
CDPABDEFINITION record.  They may be OR'd together for multiple attributes.


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**



----------------------------------------------------------------------------------------------------------


 





