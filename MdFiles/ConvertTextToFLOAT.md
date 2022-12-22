




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




 


**Function : Number**



**ConvertTextToFLOAT** **- Converts
a character number string to FLOAT.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **ConvertTextToFLOAT(**  

      const void far \*IntlFormat,  

      const NFMT far \*NumberFormat,  

      char far \* far \*ppInputText,  

      WORD  InputTextMaxLength,  

      NUMBER far \*retNumber**);**



**Description :**



This
function converts a character number string into a floating point number.  

  

You may also optionally request a nonstandard format for the number string by
setting up an NFMT and/or an INTLFORMAT structure.  Use NULL if the standard
"current" settings are  acceptable.


 


**Parameters :**



Input :  

IntlFormat  -  A pointer to a structure containing the internationalization
settings in effect. You retrieve these settings in an INTLFORMAT structure by
calling OSGetIntlSettings.  This must be done BEFORE calling
ConvertTextToFLOAT.  Can be NULL, in which case this function invokes
OSGetIntlSettings and works with those settings for the duration of the call.  

  

NumberFormat  -  A pointer to an NFMT structure -- which specifies the format
and attributes of the number text string.   This structure must be populated by
you before calling ConvertTextToFLOAT.  See NFMT\_xxx, NATTR\_xxx for an
explanation of the definitions.   Can be NULL, in which case this function
creates a default NFMT structure with the following settings:  

  

NumberFormat->Digits = 2;  

NumberFormat->Format = NFMT\_GENERAL;  

NumberFormat->Attributes = 0;  

  

ppInputText  -  A pointer to a pointer to the buffer containing the character
number text. This buffer should have a maximum length of MAXALPHANUMBER.  

NOTE:  This function will parse the input string until the first non-numeric
character is found.  Thus, if the string "123X456" is passed to the
function, the function will return without error, having placed the value 123
in the retNumber variable.  

  

InputTextMaxLength  -  The maximum number of  characters in ppInputText,
usually MAXALPHANUMBER.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:   

  

NOERROR - Conversion successful.   

ERR\_FLOAT\_CONVERSION - Cannot convert text to a number.  This error indicates
that the character number string is a not valid number.  A common cause for
this error is a number string that begins with an invalid character.    

ERR\_IFMT - Invalid International Format Specifier.  

ERR\_NFMT - Invalid Number Format Specifier.  

  

  

ppInputText  -  The original pointer incremented by the number of characters
converted.  

  

retNumber  -  The address of a NUMBER variable in which to store the returned
FLOAT.  

  




 **Sample Usage :**


  

/\*  

 \*  Save ptr to start of string, and get length of  

 \*  input string.  

 \*/  

    

  pStringBegin = pInputText;    /\* save pointer to   

  length = strlen(pInputText);  

   

/\*  

 \*  convert the string into a floating point number. If an  

 \*  error is returned, return it immediately.   

 \*/  

    

  if (sError = ConvertTextToFLOAT(NULL,  

                                  NULL,  

                                  &pInputText,  

                                  MAXALPHANUMBER,  

                                  &retNumber))  

  

   {  

   return (ERR(sError));  

   }                                 

  

/\*  

.\*  If no error, see if the function processed the entire string.  

 \*  If the number of bytes processed by the function is not equal  

 \*  to the length of the string, it probably means that the string  

 \*  contained invalid characters.  

 \*/  

  

  if ((pInputText - pStringBegin) != length)  

  {  

      :  

   perform appropriate processing.  

      :  

  }  

  

  




 **See Also :**


**[ConvertFLOATToText](ConvertFLOATToText.md)**


**[OSGetIntlSettings](OSGetIntlSettings.md)**



----------------------------------------------------------------------------------------------------------


 





