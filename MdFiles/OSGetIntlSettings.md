




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



**OSGetIntlSettings** **- Get
international settings.**


**----------------------------------------------------------------------------------------------------------**



**#include <intl.h>**



void
LNPUBLIC **OSGetIntlSettings(**  

      INTLFORMAT far \*retIntlFormat,  

      WORD  BufferSize**);**



**Description :**



Domino and
Notes maintain a table of International format information independent of the
host operating environment.  This table contains currency and date formatting
information.  

  

The INTLFORMAT structure is a parameter to several of the date and time
conversion functions. OSGetIntlSettings should be called prior to the calling
of any of these functions to initialize a local copy of the structure prior to
tailoring it to the desired options.  

  

If the program does not require tailored formats, use NULL as the address of
the INTLFORMAT structure to functions such as ConvertTIMEDATEToText instead of
calling this function, since a NULL argument to those functions is defined to
mean the "current international settings".


 


**Parameters :**



Input :  

  

BufferSize  -  Size of the INTLFORMAT structure pointed to by the intl\_format
parameter.  OSGetIntlSettings will fill in the Length field of the specified
INTLFORMAT structure  with this buffer size.  This allows API programs that use
OSGetIntlSettings to be compatible with future versions of Domino and Notes.  

  




Output :  

(routine)  -  None.  

  

  

retIntlFormat  -  The address of an INTLFORMAT structure in which the current
international settings are returned.  This structure is now ready for use with
TIMEDATE conversion routines or in conjunction with any user defined functions
that parse time, date, or currency strings.  

  




 **Sample Usage :**


  

   /\* Obtain International Settings, local TimeZone, and local \*/  

   /\* Daylight Savings Time status.                            \*/  

  

   OSGetIntlSettings(&intl\_format, sizeof(intl\_format));  

  




 **See Also :**


**[ConvertTextToTIMEDATE](ConvertTextToTIMEDATE.md)**


**[ConvertTIMEDATEToText](ConvertTIMEDATEToText.md)**


**[INTLFORMAT](INTLFORMAT.md)**



----------------------------------------------------------------------------------------------------------


 





