




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



**Function : Time**



**IntlTIMEDATEConvertToText** **- Convert
an International TIMDEDATE to text.**


**----------------------------------------------------------------------------------------------------------**



**#include <misc.h>**



STATUS
LNPUBLIC **IntlTIMEDATEConvertToText(**  

      INTLTIMEDATEHANDLE  hTimeDateHandle,  

      const void far \*IntlFormat,  

      const DTFMT \*ExtTextFormat,  

      WORD  DTFMTLen,  

      const TIMEDATE \*InputTime,  

      WORD  TextBufferLength,  

      char \*retTextBuffer,  

      WORD \*retTextLength**);**



**Description :**



This
function not only converts a Domino binary TIMEDATE structure into a character
text string, it also allows the capability to add additional PM or AM String
text to the converted TIMEDATE.


 


The DTFMT
(Date Time Format) structure must be set and passed into
IntlTIMEDATEConvertToText(..).  If the DTFMT structure is not set up then this
function will default to the ConvertTIMEDATEToText(..) behavior.  The binary
TIMEDATE will be converted to text, however there will be no additional
processing on the text string of this TIMEDATE.


 


Note: Values
that must be set within the DTFMT structure:


 


      DTFlags     DT\_VALID



                        DT\_SHOWTIME
or DT\_SHOWDATE


                        DT\_STYLE\_YMD
or DT\_STYLE\_DMY or DT\_STYLE\_MDY


 


      DTDOWFmt           refer
to Day of Week Format values defined in DT\_WFMT\_xxx 


 


      DTYearFmt             refer
to Year Format values defined in DT\_YFMT\_xxx


 


      DTMonthFmt          refer
to Month Format values defined in DT\_MFMT\_xxx


 


      DTDayFmt              refer
to Day Format values defined in DT\_DFMT\_xxx


 


      If
DTFlags is set to DT\_SHOWTIME then DTTZone must be set to one of the values
defined in TZFMT\_xxx and DTTShow must be set to one of the   values defined in
DT\_TSHOW\_xxx.


 


      If
DTFlags is set to DT\_SHOWDATE then DTDShow must be set to any of the values
defined in DT\_DSHOW\_xxx.


 


DTDSpecial
is optional and can be set to any one of the values defined in DT\_DSPEC\_xxx.


 


 


 


 


**Parameters :**



Input :  

hTimeDateHandle  -  International TIMEDATE Handle allocated with the call to
IntlTIMEDATECreateHandle.  

  

  

IntlFormat  -  The address of an INTLFORMAT structure in which the current
international settings are returned.  Use OSGetIntlSettings(..) to get the INTLFORMAT
structure.   

  

ExtTextFormat  -  The address of a DTFMT structure set up with the required
fields.  

  

DTFMTLen  -  Length of the DTFMT structure.  

  

InputTime  -  A pointer to the Domino binary time/date structure that you want
to convert.  

  

TextBufferLength  -  The length of the buffer pointed to by retTextBuffer minus
one(1) , since it is recommended that the buffer be sized using
MAXALPHATIMEDATE + 1, this is usually MAXALPHATIMEDATE.  

  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully convert to text  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  

retTextBuffer  -  The address of a text buffer in which the character text
Time/Date result of the conversion is returned.  It should be dimensioned to a
length of MAXALPHATIMEDATE + 1 .  The text  returned is not NULL terminated.  

  

retTextLength  -  The address of a WORD in which the length of the converted
character text time/date text is returned.  

  

  




 **Sample Usage :**



char                          UserDefinedString[]=
"Intl Setting PM";


INTL\_TIMEDATE\_PROPERTY propValue;


INTLTIMEDATEHANDLE            hTimeDate;


INTLFORMAT                    intlfmt;


char                          retpropValue[YTSTRMAX];


DTFMT                         dtFormat;


 


        OSGetIntlSettings(&intlfmt,
sizeof(intlfmt));


        intlfmt.Flags
|= TIME\_AMPM\_PREFIX;


        dtFormat.DTFlags
= DT\_VALID | DT\_SHOWDATE | DT\_SHOWTIME;


        dtFormat.DTDShow
= DT\_DSHOW\_MDY;


        dtFormat.DTDSpecial
= DT\_DSPEC\_21Y4;


        dtFormat.DTTZone
= TZFMT\_NEVER;


        if(intlfmt.Flags
& DATE\_YMD)


               DT\_SET\_STYLE(dtFormat.DTFlags,
DT\_STYLE\_YMD);


        else
if(intlfmt.Flags & DATE\_MDY)


               DT\_SET\_STYLE(dtFormat.DTFlags,
DT\_STYLE\_MDY);


        else
if(intlfmt.Flags & DATE\_DMY)


               DT\_SET\_STYLE(dtFormat.DTFlags,
DT\_STYLE\_DMY);


 


        if((intlfmt.Flags
& DATE\_4DIGIT\_YEAR) || (intlfmt.Flags & DT\_4DIGITYEAR))


               dtFormat.DTYearFmt
= DT\_YFMT\_YYYY;


        else


               dtFormat.DTYearFmt
= DT\_YFMT\_YY;


 


        if(dtFormat.DTFlags
& DT\_ALPHAMONTH)


               dtFormat.DTMonthFmt
= DT\_MFMT\_MMM;


        else


               dtFormat.DTMonthFmt
= DT\_MFMT\_MM;


        dtFormat.DTDayFmt
= DT\_DFMT\_DD;


        dtFormat.DTDOWFmt
= DT\_WFMT\_WWW;


        dtFormat.DTTShow
= DT\_TSHOW\_ALL;


 


        if(intlfmt.Flags
& CLOCK\_24\_HOUR)


               dtFormat.DTFlags
|= DT\_24HOUR;


        else


               dtFormat.DTFlags
&= ~DT\_24HOUR;


 


 


        dtFormat.DTDsep1
= intlfmt.DateString;


        dtFormat.DTDsep2
= intlfmt.DateString;


        dtFormat.DTDsep3
= intlfmt.DateString;


        dtFormat.DTTsep
= intlfmt.TimeString;


...


...


...


        if(error
= IntlTIMEDATECreateHandle( &hTimeDate ))


        {


       printf
("Error: unable to convert TIMEDATE to text.\n");


             
TimeStringLen = 0;


               ItemText[TimeStringLen]
= '\0';


               break;


       }


        propValue
= PMStringProperty;


        if(error
= IntlTIMEDATESetValue(hTimeDate, propValue, UserDefinedString))


        {


               IntlTIMEDATEDeleteHandle(
hTimeDate );


               printf
("Error: unable to convert TIMEDATE to text.\n");


             
TimeStringLen = 0;


               ItemText[TimeStringLen]
= '\0';


               break;


       }


        if(error
= IntlTIMEDATEGetValue(hTimeDate, propValue, sizeof(retpropValue),
retpropValue))


        {


               IntlTIMEDATEDeleteHandle(
hTimeDate );


               printf
("Error: unable to convert TIMEDATE to text.\n");


             
TimeStringLen = 0;


               ItemText[TimeStringLen]
= '\0';


               break;


        }


        printf("\nPMStringProperty
Value = %s:\n", retpropValue);


        if(error
= IntlTIMEDATEConvertToText(hTimeDate, &intlfmt, &dtFormat,
sizeof(dtFormat), &TimeItem, MAXALPHATIMEDATE,


                                                     ItemText,
&TimeStringLen))


        {


               IntlTIMEDATEDeleteHandle(
hTimeDate );


               printf
("Error: unable to convert TIMEDATE to text.\n");


             
TimeStringLen = 0;


               ItemText[TimeStringLen]
= '\0';


               break;


        }


        IntlTIMEDATEDeleteHandle(hTimeDate);


      
ItemText[TimeStringLen] = '\0';


      
break;


 **See Also :**


**[DTFMT](DTFMT.md)**


**[IntlTIMEDATECreateHandle](IntlTIMEDATECreateHandle.md)**


**[IntlTIMEDATEDeleteHandle](IntlTIMEDATEDeleteHandle.md)**


**[IntlTIMEDATEGetValue](IntlTIMEDATEGetValue.md)**


**[INTLTIMEDATEHANDLE](INTLTIMEDATEHANDLE.md)**


**[IntlTIMEDATESetValue](IntlTIMEDATESetValue.md)**


**[INTL\_TIMEDATE\_PROPERTY](INTL_TIMEDATE_PROPERTY.md)**


**[TIMEDATE](TIMEDATE.md)**



----------------------------------------------------------------------------------------------------------


 





