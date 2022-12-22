




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



**ConvertTIMEDATEToText** **- Converts
a binary TIMEDATE to a character text string.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertTIMEDATEToText(**  

      const void far \*IntlFormat,  

      const TFMT far \*TextFormat,  

      const TIMEDATE far \*InputTime,  

      char far \*retTextBuffer,  

      WORD  TextBufferLength,  

      WORD far \*retTextLength**);**



**Description :**



This
function converts a Domino binary TIMEDATE structure into a character text
string.   

  

You may also optionally request a non-standard format for the output string by
setting up a TFMT or INTLFORMAT structures.  Use NULL if the standard
"current" settings is acceptable.


 


Note: If
4-digit year is specified in the date setting of the operating system, then the
converted text will contain a 4-digit year.  If a 2-digit year is specified in
the date setting of the operating system, and if the year portion of the date
in the TIMEDATE structure is in the range 1950 to 1999, the converted text will
only contain the last 2 digits of the year (e.g. "98".)  Otherwise
all 4 digits of the year will be represented (e.g. "2001".)   To
represent all years, including 1950 to 1999, with 4 digits, specify TFMT.Date
as either TDFMT\_FULL4, TDFMT\_CPARTIAL4, or  TDFMT\_DPARTIAL4.


 


**Parameters :**



Input :  

IntlFormat  -  The internationalization settings in effect. You retrieve these
settings in an INTLFORMAT structure returned during a call to
OSGetIntlSettings. This argument is a void pointer to the INTLFORMAT.   Can be
NULL, in which case this function invokes OSGetIntlSettings and works with
those settings for the duration of the call.  

  

TextFormat  -  A pointer to a TFMT structure -- which specifies the desired
format of the character text converted time/date string.    Can be NULL, in
which case this function creates a temporary version of the required TFMT
structure and assigns the following values to its members:   

  

td\_format\_ptr->Date = TDFMT\_FULL;  

td\_format\_ptr->Time = TTFMT\_FULL;  

td\_format\_ptr->Zone = TZFMT\_NEVER;  

td\_format\_ptr->Structure = TSFMT\_DATETIME;  

  

  

InputTime  -  A pointer to the Domino binary time/date structure that you want
to convert.  

  

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus
one(1) , since it is recommended that the buffer be sized using MAXALPHATIMEDATE
+ 1, this is usually MAXALPHATIMEDATE.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - conversion successful.   

ERR\_TDO\_CONV - Invalid Time or Date Encountered.  

ERR\_IFMT - Invalid International Format Specifier.  

ERR\_TFMT - Invalid Time/Date Format Specifier.  

  

  

retTextBuffer  -  The address of a text buffer in which the character text
Time/Date result of the conversion is returned.  It should be dimensioned to a
length of MAXALPHATIMEDATE + 1 .  The text  returned is not NULL terminated.  

  

retTextLength  -  The address of a WORD in which the length of the converted
character text time/date text is returned.  

  




 **Sample Usage :**


    

   /\* Get Last modified time/date of note just created \*/  

  

   NSFNoteGetInfo(note\_handle, \_NOTE\_MODIFIED, &binary\_td2);  

   td\_string\_ptr = &td\_string1[0];  

   if (error\_status = ConvertTIMEDATEToText(&intl\_format, &td\_format,  

                                       &binary\_td2, td\_string\_ptr,  

                                       MAXALPHATIMEDATE, &string\_len))  

       goto Exit;  

   td\_string\_ptr[string\_len] = '\0';  /\* provide NULL terminator \*/  

  




 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[OSCurrentTIMEDATE](OSCurrentTIMEDATE.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**


**[TFMT](TFMT.md)**



----------------------------------------------------------------------------------------------------------


 





