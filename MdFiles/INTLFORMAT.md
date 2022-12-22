




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




 


**Data Type : Time**



**INTLFORMAT** **-** Holds
country and workstation settings.


**----------------------------------------------------------------------------------------------------------**



**#include
<intl.h>**



**Definition :**



typedef struct {  

   WORD Flags;                   /\* OR'd #defines for daylight


                                 
  savings, number, time, and date


                                   
formats - see Symbolic Values


                                   
CLOCK\_24\_HOUR, CURRENCY\_SPACE,


                                   
CURRENCY\_SUFFIX, DATE\_DMY,


                         
          DATE\_MDY, DATE\_YMD,


                                   
DAYLIGHT\_SAVINGS,


                                   
NUMBER\_LEADING\_ZERO \*/  

   BYTE CurrencyDigits;          /\* Number of decimal digits in


                                   
fractional monetary amounts \*/  

   BYTE Length;                  /\* Length of this structure \*/  

                                    If this structure is set from


                                   
scratch, THIS MUST BE SET TO


                                   
THE EXACT SIZE OF THE STRUCTURE


                                   
WHEN ITS POINTER IS PASSED AS


                                   
AN ARGUMENT \*/  

   int  TimeZone;                /\* number of hours added to the time


                                   
to get Greenwich Mean Time. May be 


                                   
positive or negative. \*/  

   char AMString[ISTRMAX];       /\* AM/am string used in countries


                                   
with 12 hour time format \*/  

   char PMString[ISTRMAX];       /\* PM/pm string used in countries


                                   
with 12 hour time format \*/  

   char CurrencyString[ISTRMAX]; /\* Symbol for currency:


                                   
$, Fr, SEK, etc.  \*/  

   char ThousandString[ISTRMAX]; /\* Symbol formatting monetary


                                   
amounts in thousands  \*/  

   char DecimalString[ISTRMAX];  /\* Symbol denoting decimal


                                   
fraction of monetary amounts \*/  

   char DateString[ISTRMAX];     /\* Character(s) separating


                                   
components of date string \*/  

   char TimeString[ISTRMAX];     /\* Character(s) separating


                                   
components of time string \*/  

   char YesterdayString[YTSTRMAX]; /\* String denoting previous


                                   
day \*/  

   char TodayString[YTSTRMAX];   /\* String denoting current day \*/  

   char TomorrowString[YTSTRMAX];  

} INTLFORMAT;


 


**Description :**



The
INTLFORMAT typedef is used to declare a data structure that is returned from
OSGetIntlSettings with country and workstation dependant information.  This
structure provides information useful in parsing or composing Time, Date, and
Currency strings.  It is also used by ConvertTextToTIMEDATE and
ConvertTIMEDATEToText to indicate the expected or resulting string format,
current time zone and daylight savings values.


 


Note: The
function ConvertTIMEDATEToText does not take the DAYLIGHT\_SAVINGS flag  into
account.


 **See Also :**


**[CLOCK\_24\_HOUR](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/9182185CC24D28EC85256206006EA176)**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[CURRENCY\_SPACE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EE0531D80ED84BC785256206006E9A7D)**


**[CURRENCY\_SUFFIX](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BAC006D2200)**


**[DATE\_DMY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/521F7683DE15114E85256206006EA83E)**


**[DATE\_MDY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/AFC61CA593E33C0285256206006EA752)**


**[DATE\_YMD](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B16D53E7A5642C7685256206006EABE9)**


**[DAYLIGHT\_SAVINGS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E8A000CA68F88E5D85256206006EA34E)**


**[NUMBER\_LEADING\_ZERO](NUMBER_LEADING_ZERO.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**



----------------------------------------------------------------------------------------------------------


 





