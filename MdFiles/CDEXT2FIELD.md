




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




**Initial Release 5.0**



**Data Type : Composite Data; Rich
Text**



**CDEXT2FIELD** **-** Extended
field reference record used for currency and numeric symbol information.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


        WSIG    Header;


        /\*
Numeric symbol data \*/


        BYTE    NumSymPref;                   /\*
NPREF\_xxx \*/


        BYTE    NumSymFlags;           /\*
NNUMSYM\_xxx \*/


        DWORD   DecimalSymLength;


        DWORD   MilliSepSymLength;


        DWORD   NegativeSymLength;


        WORD    MilliGroupSize;


        SWORD   VerticalSpacing;       /\*
extra vertical spacing (%) \*/


        SWORD   HorizontalSpacing;     /\*
extra horizontal spacing (%) \*/


        WORD    Unused2;


        WORD    FirstFieldLimitType;


        /\*
Currency data \*/


        BYTE    CurrencyPref;          /\*
NPREF\_xxx \*/


        BYTE    CurrencyType;          /\*
NCURFMT\_xxx \*/


        BYTE    CurrencyFlags;         /\*
NCURFMT\_xxx \*/


        DWORD   CurrencySymLength;


        DWORD   ISOCountry;    


        WORD    ThumbnailImageWidth;          /\*
Hannover Thumbnail support \*/


        WORD    ThumbnailImageHeight;


        WORD    wThumbnailImageFileNameLength;


        WORD    wIMOnlineNameFormulaLen;


        /\*
Date/time formatting data \*/


        BYTE    DTPref;                       /\*
NPREF\_xxx \*/


        DWORD   DTFlags;                      /\*
DT\_xxx \*/


        DWORD   DTFlags2;                     /\*
DT\_xxx \*/


        BYTE    DTDOWFmt;                     /\*
DT\_WFMT\_xxx \*/


        BYTE    DTYearFmt;                    /\*
DT\_YFMT\_xxx \*/


        BYTE    DTMonthFmt;                   /\*
DT\_MFMT\_xxx \*/


        BYTE    DTDayFmt;                     /\*
DT\_DFMT\_xxx \*/


        BYTE    DTDsep1Len;


        BYTE    DTDsep2Len;


        BYTE    DTDsep3Len;


        BYTE    DTTsepLen;


        BYTE    DTDShow;                      /\*
DT\_DSHOW\_xxx \*/


        BYTE    DTDSpecial;                   /\*
DT\_DSPEC\_xxx \*/


        BYTE    DTTShow;                      /\*
DT\_TSHOW\_xxx \*/


        BYTE    DTTZone;                      /\*
TZFMT\_xxx \*/


        DWORD   Unused5;


        /\*
Proportional font for fields data  \*/


 


        BYTE    ECFlags;


        BYTE    Unused612;


        WORD    wCharacters;   /\*
Number of characters if proportional width        \*/


        WORD    wInputEnabledLen;      /\*
Input enabled formula. \*/


        WORD    wIMGroupFormulaLen;    /\*
Instant messageing buddy list group name. \*/


                                                     /\*
Now comes the variable part of the struct... \*/


}
CDEXT2FIELD;


 


 


**Description :**



New field
attributes have been added in Release 5.0 of Domino.  To preserve compatibility
with existing applications, the new attributes have been placed in this second
extension to the CDFIELD record.  This record will be  present in the $Body
item of the form note for each field defined.


 


Header


      *Numeric
Symbol Data*


NumSmyPref                Numeric
Symbol Data preferences         


NumSymFlags              Reserved
for future use


DecimalSymLength       Decimal
Symbol Length


MilliSepSymLength         
Milli Separator Symbol Length        


NegativeSymLength      Negative
Symbol Length


MilliGroupSize              Number
of digits per "thousands" group (i.e. where to put the ","
in "1,000")


VerticalSpacing;           Extra
vertical spacing (%)  

HorizontalSpacing;        Extra horizontal spacing (%)


Unused2


FirstFieldLimitType 
This value reflects the Only allow multiple choice in the Limit Input of the
Rich Text Lite field,see FL\_xxx


CurrencyPref                Currency
Preferences


CurrencyType               Common
or custom currency


CurrencyFlags              see
NCURFMT\_xxx


CurrencySymLength     


ISOCountry                  ISO
Country Code


Unused3


Unused4


      *Date/Time
Formatting Data*


DTPref                         Date/Time
Preferences


DTFlags                       see
DT\_xxx [DTFlags]


DTFlags2                     see
DT\_xxx [DTFlags2]


DTDOWFmt                 see
DT\_WFTM\_xxx


DTYearFmt                   see
DT\_YFMT\_xxx


DTMonthFmt                see
DT\_MFMT\_xxx


DTDayFmt                    see
DT\_DFMT\_xxx


DTDsep1Len                Length
of first Date/Time Date separator


DTDsep2Len                    
Length of second Date/Time Date separator


DTDsep3Len                    
Length of third Date/Time Date separator


DTTsepLen                       
Length of Date/Time Time separator


DTDShow                     see
DT\_DSHOW\_xxx


DTDSpecial                  see
DT\_DSPEC\_xxx


DTTShow                     see
DT\_TSHOW\_xxx


DTTZone                      see
TZFMT\_xxx


Unused5


ECFlags                       see
EC\_FLAG\_WIDTH\_PROPORTIONAL


Unused612


wCharacters                 Number
of characters if proportional width


wInputEnabledLen         Input
enabled formula.


wIMGroupFormulaLen   Instant
messaging buddy list group name. 


 


Since the
$Body field has type TYPE\_COMPOSITE, API programs that run on non-Intel
architecture platforms must perform host/canonical conversion on CDEXT2FIELD
records when accessing the $Body field of a form note.  


 


If there is
variable numeric, currency and/or date/time data then the variable portion of
the data will follow the fixed portion of this CD record in the preceding
order. If you plan to use the date/time separators,you will need to declare the
separator variables and assign values to their lengths (DTDsep1Len, DTDsep2Len,
DTDsep3Len, DTTsepLen).


 


 The
DT\_STYLE\_xxx flags are set using the DT\_SET\_STYLE function . The other DTFlags
are set using an assignment statement.


*Example:* CDExt2Field.DTFlags = DT\_SHOWDATE | DT\_VALID; 


                         
DT\_SET\_STYLE(CDExt2Field.DTFlags, DT\_STYLE\_DMY);


 


 **See Also :**


**[CDFIELD](CDFIELD.md)**


**[DT\_DFMT\_xxx](DT_DFMT_xxx.md)**


**[DT\_DSHOW\_xxx](DT_DSHOW_xxx.md)**


**[DT\_DSPEC\_xxx](DT_DSPEC_xxx.md)**


**[DT\_MFMT\_xxx](DT_MFMT_xxx.md)**


**[DT\_TSHOW\_xxx](DT_TSHOW_xxx.md)**


**[DT\_WFMT\_xxx](DT_WFMT_xxx.md)**


**[DT\_xxx [CDEXT2FIELD - DTFlags2]](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/E81D3F23E5DE77D68525672F00011235)**


**[DT\_xxx [CDEXT2FIELD - DTFlags]](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/38F1D1816A01E4D48525672E00802904)**


**[DT\_YFMT\_xxx](DT_YFMT_xxx.md)**


**[NCURFMT\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/1D147BA259DF66598525674C0053250F)**


**[NPREF\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/9864934E886985628525672E007E020C)**


**[TZFMT\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/659769E36672989A8525621B00408849)**



----------------------------------------------------------------------------------------------------------


 





