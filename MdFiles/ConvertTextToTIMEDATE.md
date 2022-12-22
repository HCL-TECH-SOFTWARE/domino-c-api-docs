




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




 


**Function : Time**



**ConvertTextToTIMEDATE** **- Converts
a character time/date string to TIMEDATE.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertTextToTIMEDATE(**  

      const void far \*IntlFormat,  

      const TFMT far \*TextFormat,  

      char far \* far \*Text,  

      WORD  MaxLength,  

      TIMEDATE far \*retTIMEDATE**);**



**Description :**



This
function converts a character time/date string into Domino binary TIMEDATE
format.   

  

You may also optionally request a non-standard format for the time/date string
by setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard
"current" settings are  acceptable.


 


The year
portion of the time/date string may be specified with all 4 digits.  If the
date format does not require a 4-digit year, then the years 1950 to 2049 may
also be specified using only the last 2 digits.  

  




Only
integral values in the text string are converted.  If the seconds component of
the string contains a decimal point, it will be truncated to its integer value.


 


**Parameters :**



Input :  

IntlFormat  -  A pointer to a structure containing the internationalization
settings in effect. You retrieve these settings in an INTLFORMAT structure by
calling OSGetIntlSettings.  This must be done BEFORE calling
ConvertTextToTIMEDATE.  Can be NULL, in which case this function invokes
OSGetIntlSettings and works with those settings for the duration of the call.  

  

TextFormat  -  A pointer to a TFMT structure -- which specifies the syntax of
the date/time text string.   This structure must be populated by you before
calling ConvertTextToTIMEDATE. See TDFMT\_xxx, TTFMT\_xxx, TZFMT\_xxx, and
TSFMT\_xxx for an explanation of the definitions.   Can be NULL, in which case
this function creates the required TFMT structure and assigns the following
values to its members:   

  

td\_format\_ptr->Date = TDFMT\_FULL;  

td\_format\_ptr->Time = TTFMT\_FULL;  

td\_format\_ptr->Zone = TZFMT\_NEVER;  

td\_format\_ptr->Structure = TSFMT\_DATETIME;  

  

  

Text  -  A pointer to a pointer to the buffer containing the character
time/date text. This buffer should have a maximum length of MAXALPHATIMEDATE +
1.  

  

MaxLength  -  The maximum number of significant characters in Text, usually
MAXALPHATIMEDATE.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - Conversion successful.   

ERR\_TDI\_CONV - Unable to interpret Time or Date.  This error indicates that the
character time/date string is not in the correct format.  A common cause for
this error is an incorrect date format.  The validity of a date format depends
on the date separator that is chosen in the operating environment control
panel.  The default separator in the Windows operating environment is a slash
(/).  Refer to the Lotus Domino Designer documentation for more information
about time/date formats.  

ERR\_IFMT - Invalid International Format Specifier.  

ERR\_TFMT - Invalid time/date Format Specifier.  

  

  

Text  -  The specified pointer is updated to the next character after the
time/date text that was parsed.  

  

retTIMEDATE  -  The address of a TIMEDATE structure in which the binary
equivalent of the time/date text is returned.  

  




 **Sample Usage :**


   /\* Build a time/date
string & convert to binary TIMEDATE structure\*/  

  

   strcpy(td\_string1, "07");  

   strcpy(&td\_string1[strlen(td\_string1)], intl\_format.DateString);  

   strcpy(&td\_string1[strlen(td\_string1)], "04");  

   strcpy(&td\_string1[strlen(td\_string1)], intl\_format.DateString);  

   strcpy(&td\_string1[strlen(td\_string1)], "91 4");  

   strcpy(&td\_string1[strlen(td\_string1)], intl\_format.TimeString);  

   strcpy(&td\_string1[strlen(td\_string1)], "30 PM EST");  

   td\_string\_ptr = &td\_string1[0];  

  

   if (error\_status = ConvertTextToTIMEDATE(&intl\_format, &td\_format,  

                                    &td\_string\_ptr, strlen(td\_string1),  

                                    &binary\_td1))  

       goto Exit;


 **See Also :**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**


**[TFMT](TFMT.md)**


**[TYPE\_xxx [TIME\_RANGE]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C598A7AE1C5A2C6A8525622E00645C02)**



----------------------------------------------------------------------------------------------------------


 





