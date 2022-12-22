




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



**ConvertTextToTIMEDATEPAIR** **- Convert
character time/date pair to TIMEDATE\_PAIR.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertTextToTIMEDATEPAIR(**  

      const void far \*IntlFormat,  

      const TFMT far \*TextFormat,  

      char far \* far \*Text,  

      WORD  MaxLength,  

      TIMEDATE\_PAIR far \*retTIMEDATE**);**



**Description :**



This
function converts a character time/date pair string into Domino binary
TIMEDATE\_PAIR format.   

  

You may also optionally request a non-standard format for the output string by
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard
"current" settings is acceptable.  

  

The string syntax is: 1st\_time/date\_string + " - " +
2nd\_time/date\_string.  The two strings must not be identical, otherwise an
error will be returned.  

  

Please note that this "-" seperator is not neccessarily the same as
the date seperator provided by OSGetIntlSettings.


 


**Parameters :**



Input :  

IntlFormat  -  A pointer to a structure containing the internationalization
settings in effect. You retrieve these settings in an INTLFORMAT structure by
calling OSGetIntlSettings.  This must be done BEFORE calling
ConvertTextToTIMEDATE.   Can be NULL, in which case this function invokes
OSGetIntlSettings and works with those settings for the duration of this call.  

  

TextFormat  -  A pointer to a TFMT structure -- which specifies the syntax of
the date/time text string.   This structure must be populated by you before
calling ConvertTextToTIMEDATE. See TDFMT\_xxx, TTFMT\_xxx, TZFMT\_xxx, and
TSFMT\_xxx for an explanation of the definitions.   Can be NULL, in which case
this function creates temporary version of the required TFMT structure and
assigns the following values to its members:   

  

td\_format\_ptr->Date = TDFMT\_FULL;  

td\_format\_ptr->Time = TTFMT\_FULL;  

td\_format\_ptr->Zone = TZFMT\_NEVER;  

td\_format\_ptr->Structure = TSFMT\_DATETIME;  

  

Text  -  A pointer to a pointer to the character time/date pair string. This
string should have a maximum length of (MAXALPHATIMEDATEPAIR) + 1.  

  

MaxLength  -  The maximum number of significant characters in Text.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - conversion successful .  

ERR\_TDI\_CONV - Unable to interpret Time or Date.  

ERR\_NOT\_TDPAIR - TIMEDATE, not TIMEDATE\_PAIR.  

ERR\_IFMT - Invalid International Format Specifier.  

ERR\_TFMT - Invalid Time/Date Format Specifier.  

  

  

retTIMEDATE  -  The address of a TIMEDATE\_PAIR structure in which the binary
equivalent of the time/date pair text string is returned.  

  




 **Sample Usage :**


  

   td\_string\_ptr = &td\_string\_pair[0];  

   if(error\_status = ConvertTextToTIMEDATEPAIR(&intl\_format,  

                            &td\_format, &td\_string\_ptr,  

                            strlen(td\_string\_ptr), &binary\_td\_pair))  

       goto Exit;  

  




 **See Also :**


**[ConvertTIMEDATEPAIRToText](ConvertTIMEDATEPAIRToText.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**



----------------------------------------------------------------------------------------------------------


 





