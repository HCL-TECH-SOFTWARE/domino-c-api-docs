




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




**Initial Release 6**



**Symbolic Value : Constants; Views**



**VCF\_HIDE\_xxx** **-** VIEW\_COLUMN\_FORMAT2
- wCustomHiddenFlags.


**----------------------------------------------------------------------------------------------------------**



**#include <viewfmt.h>**


 **Symbolic Values :**      VCF\_HIDE\_S\_NormalView    -  (Shift) Hide column if in normal
view  

  

      VCF\_HIDE\_M\_NormalView   -  (Mask) Hide column if in normal view  

  

      VCF\_HIDE\_S\_CalFormatTwoDay      -  (Shift) Hide column if in two day
calendar view  

  

      VCF\_HIDE\_M\_CalFormatTwoDay     -  (Mask) Hide column if in two day
calendar view  

  

      VCF\_HIDE\_S\_CalFormatOneWeek   -  (Shift) Hide column if in one week
calendar view  

  

      VCF\_HIDE\_M\_CalFormatOneWeek   -  (Mask) Hide column if in one week
calendar view  

  

      VCF\_HIDE\_S\_CalFormatTwoWeeks             -  (Shift) Hide column if in two
week calendar view  

  

      VCF\_HIDE\_M\_CalFormatTwoWeeks             -  (Mask) Hide column if in two
week calendar view  

  

      VCF\_HIDE\_S\_CalFormatOneMonth   -  (Shift) Hide column if in one month
calendar view  

  

      VCF\_HIDE\_M\_CalFormatOneMonth              -  (Mask) Hide column if in one
month calendar view  

  

      VCF\_HIDE\_S\_CalFormatOneYear     -  (Shift) Hide column if in one year calendar
view  

  

      VCF\_HIDE\_M\_CalFormatOneYear    -  (Mask) Hide column if in one year
calendar view  

  

      VCF\_HIDE\_S\_CalFormatOneDay      -  (Shift) Hide column if in one day
calendar view  

  

      VCF\_HIDE\_M\_CalFormatOneDay     -  (Mask) Hide column if in one day
calendar view  

  

      VCF\_HIDE\_S\_CalFormatWorkWeek              -  (Shift) Hide column if in
work week calendar view  

  

      VCF\_HIDE\_M\_CalFormatWorkWeek             -  (Mask) Hide column if in work
week calendar view  

  

      VCF\_HIDE\_S\_DB2\_MAPPING          -  (Shift) Column mapped to DB2 data
type.  

  

      VCF\_HIDE\_M\_DB2\_MAPPING          -  (Mask) Column mapped to DB2 data type.  

  

      VCF\_HIDE\_S\_DB2\_DATATYPE\_TEXT         -  (Shift) Column mapped to DB2 data
type TEXT.  

  

      VCF\_HIDE\_M\_DB2\_DATATYPE\_TEXT         -  (Mask) Column mapped to DB2 data
type TEXT.  

  

      VCF\_HIDE\_S\_DB2\_DATATYPE\_NUMBER    -  (Shift) Column mapped to DB2 data
type NUMBER.  

  

      VCF\_HIDE\_M\_DB2\_DATATYPE\_NUMBER   -  (Mask) Column mapped to DB2 data type
NUMBER.  

  

      VCF\_HIDE\_S\_DB2\_DATATYPE\_TIMEDATE             -  (Shift) Column mapped to
DB2 data type TIMEDATE.  

  

      VCF\_HIDE\_M\_DB2\_DATATYPE\_TIMEDATE            -  (Mask) Column mapped to
DB2 data type TIMEDATE.  

  

      VCF\_HIDE\_S\_DB2\_DATATYPE\_NONE        -  (Shift) Select Column mapping to
DB2 data type.  

  

      VCF\_HIDE\_M\_DB2\_DATATYPE\_NONE        -  (Mask) Select Column mapping to
DB2 data type.  

  




**Description :**



Values for
wCustomHiddenFlags member of VIEW\_COLUMN\_FORMAT2. In the calendar view, hidden
columns may be saved on a per calendar format basis. If the calendar format's
day display area is small (ex: a one month calendar format), you may wish to
hide more columns than when the day display is larger (ex: a two day calendar
format).


 **See Also :**


**[VIEW\_COLUMN\_FORMAT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/868D1214A6E2E199852561C000516B12)**



----------------------------------------------------------------------------------------------------------


 





