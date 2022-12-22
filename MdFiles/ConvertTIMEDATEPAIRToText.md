




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



**ConvertTIMEDATEPAIRToText** **- Converts
binary TIMEDATE\_PAIR to a character text string.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertTIMEDATEPAIRToText(**  

      const void far \*IntlFormat,  

      const TFMT far \*TextFormat,  

      const TIMEDATE\_PAIR far \*InputTime,  

      char far \*retTextBuffer,  

      WORD  TextBufferLength,  

      WORD far \*retTextLength**);**



**Description :**



This
function converts a Domino binary TIMEDATE\_PAIR structure into a character text
string.   The character text string consists of two date strings separated by
" - ".  

  

You may also optionally request a non-standard format for the output string by
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard
"current" settings is acceptable.


 


**Parameters :**



Input :  

IntlFormat  -  The internationalization settings in effect. You retrieve these
settings in an INTLFORMAT structure returned during a call to
OSGetIntlSettings. This argument is a void pointer to the INTLFORMAT.  Can be
NULL, in which case this function invokes OSGetIntlSettings and works with
those settings for the duration of this call.  

  

TextFormat  -  A pointer to a TFMT structure -- which specifies the desired
format of the character converted time/date string.  Can be NULL, in which case
this function creates a temporary version of the required TFMT structure and
assigns the following values to its members:   

  

td\_format\_ptr->Date = TDFMT\_FULL;  

td\_format\_ptr->Time = TTFMT\_FULL;  

td\_format\_ptr->Zone = TZFMT\_NEVER;  

td\_format\_ptr->Structure = TSFMT\_DATETIME;  

  

  

InputTime  -  A pointer to the Domino binary time/date structure that you want
to convert.  

  

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus
one(1) or usually MAXALPHATIMEDATEPAIR.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - conversion successful.   

ERR\_BUFFER\_OVERFLOW - Output Buffer Overflow.  

ERR\_TDO\_CONV - Invalid Time or Date Encountered.  

ERR\_IFMT - Invalid International Format Specifier.  

ERR\_TFMT - Invalid Time/Date Format Specifier.  

  

  

retTextBuffer  -  The address of a text buffer in which the character text
time/date result of the conversion is returned. The buffer must be declared
with a length of (MAXALPHATIMEDATEPAIR) + 1.  This includes 1 for a future NULL
terminator.  The returned text is not NULL terminated.  

  

retTextLength  -  The address of a WORD in which the length of the converted
character time/date pair text is returned.  

  




 **Sample Usage :**


    

   /\* Convert Time/Date Pair to Text \*/  

   binary\_td\_pair.Lower.Innards[0] = binary\_td2.Innards[0];  

   binary\_td\_pair.Lower.Innards[1] = binary\_td2.Innards[1];  

   binary\_td\_pair.Upper.Innards[0] = binary\_td3.Innards[0];  

   binary\_td\_pair.Upper.Innards[1] = binary\_td3.Innards[1];  

   td\_string\_ptr = &td\_string\_pair[0];  

   if (error\_status = ConvertTIMEDATEPAIRToText(&intl\_format,  

                                   &td\_format, &binary\_td\_pair,  

                                   td\_string\_ptr, MAXALPHATIMEDATEPAIR,  

                                   &string\_len))  

       goto Exit;  

  




 **See Also :**


**[ConvertTextToTIMEDATEPAIR](ConvertTextToTIMEDATEPAIR.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**


**[TYPE\_xxx [TIME\_RANGE]](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C598A7AE1C5A2C6A8525622E00645C02)**



----------------------------------------------------------------------------------------------------------


 





