




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 6.0.2**



**Data Type : Time**



**DTFMT** **-** Date/Time
formatting data


**----------------------------------------------------------------------------------------------------------**



**#include
<misc.h>**



**Definition :**



typedef struct {


        BYTE    Preferences;                  /\*
NPREF\_xxx. Get preferences from the Client or from the Form/View? \*/


        DWORD   DTFlags;                      


        DWORD   DTFlags2;                     /\*
In case we need more room \*/


        BYTE    DTDOWFmt;                     /\*
Day-of-week format choice \*/


        BYTE    DTYearFmt;                    /\*
Year format choice \*/


        BYTE    DTMonthFmt;                   /\*
Month format choice \*/


        BYTE    DTDayFmt;                     /\*
Day format choice \*/


        BYTE    DTDShow;                      /\*
Date display choice \*/


        BYTE    DTTShow;                      /\*
Time display choice \*/


        BYTE    DTDSpecial;                   /\*
Date special display choice \*/


        BYTE    DTTZone;                      /\*
Time zone display choice \*/


        char\*   DTDsep1;                      /\*
Date field separator string #1 \*/


        char\*   DTDsep2;                      /\*
Date field separator string #2 \*/


        char\*   DTDsep3;                      /\*
Date field separator string #3 \*/


        char\*   DTTsep;                /\*
Time field separator string \*/


} DTFMT;  

  




 


**Description :**



This
structure holds the format for date and time information.  This structure must
be filled out when passed into the function IntlTIMEDATEConvertToText(..). 
Please see IntlTIMEDATEConvertToText(..) for more information.


 **See Also :**


**[DT\_DFMT\_xxx](DT_DFMT_xxx.md)**


**[DT\_DSHOW\_xxx](DT_DSHOW_xxx.md)**


**[DT\_DSPEC\_xxx](DT_DSPEC_xxx.md)**


**[DT\_GET\_STYLE](DT_GET_STYLE.md)**


**[DT\_MFMT\_xxx](DT_MFMT_xxx.md)**


**[DT\_SET\_STYLE](DT_SET_STYLE.md)**


**[DT\_TSHOW\_xxx](DT_TSHOW_xxx.md)**


**[DT\_WFMT\_xxx](DT_WFMT_xxx.md)**


**[DT\_xxx [CDEXT2FIELD - DTFlags2]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E81D3F23E5DE77D68525672F00011235)**


**[DT\_xxx [CDEXT2FIELD - DTFlags]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/38F1D1816A01E4D48525672E00802904)**


**[DT\_YFMT\_xxx](DT_YFMT_xxx.md)**


**[IntlTIMEDATEConvertToText](IntlTIMEDATEConvertToText.md)**


**[NPREF\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9864934E886985628525672E007E020C)**



----------------------------------------------------------------------------------------------------------


 





