




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




**Initial Release 7.0.2**



**Data Type : HTML**



**HTMLAPI\_PROP\_TYPE** **-** Information
about the converter object is handled with an enumeration and a pair of get/set
methods.


**----------------------------------------------------------------------------------------------------------**



**#include
<htmlapi.h>**



**Definition :**



typedef enum


{


            HTMLAPI\_PROP\_TEXTLENGTH
= 0     


            ,HTMLAPI\_PROP\_NUMREFS
= 1         


            ,HTMLAPI\_PROP\_USERAGENT\_LEN
= 3 


            ,HTMLAPI\_PROP\_USERAGENT
= 4 


            ,HTMLAPI\_PROP\_BINARYDATA
= 6


            ,HTMLAPI\_PROP\_MIMEMAXLINELENSEEN
= 102       


 


}
HTMLAPI\_PROP\_TYPE;


 


 


**Description :**



Information
about the converter object is handled with an enumeration and a pair of get/set
methods.  The data type passed through the API is void\*.  Depending on the
enumeration value, the thing pointed to by the void\* is cast to the actual type
of that property. The symbols(r & w) in the parentheses below represent
whether this property can be read(r) or write(w)


 


 


            HTMLAPI\_PROP\_TEXTLENGTH
= 0     


                                    /\*
(r DWORD)   Number of bytes in output HTML text buffer.


                                                This
property is valid after calls to HTMLConvertXXX() 


                                    \*/


 


            ,HTMLAPI\_PROP\_NUMREFS
= 1         


                                    /\*
(r DWORD)   Number of references in output list of HTML references.


                                                This
property is valid after callst to HTMLConvertXXX()


                                    \*/


 


            ,HTMLAPI\_PROP\_USERAGENT\_LEN
= 3 


                                    /\*
(r DWORD)  Length of the USERAGENT property -- 0 if the USERAGENT


                                                property
isn't set.


                                    \*/


 


            ,HTMLAPI\_PROP\_USERAGENT
= 4 


                                    /\*
(rw char \*)  NULL-terminated string indicating the "browser" being
used.


                                                Some
HTML is generated differently depending on browser.


                                                (On
set, if the string is too big -- gerater than MAX\_DOMINO\_USERAGENT\_LENGHT --


                                                 then
ERR\_HTMLAPI\_INVALID\_ARG is returned.


                                                 On
get, buffer must hold at least PROP\_USERAGENT\_LEN+1 bytes.) 


 


                                                This
property must be set before calls to HTMLConvertXXX()


                                    \*/


 


            ,HTMLAPI\_PROP\_BINARYDATA
= 6


                                    /\*
(r BOOL) Indicates (when TRUE) that the results of GetText are binary data.


                                                "HTMLConvertImage"
and "HTMLConvertElement" usualy return binary text data.


                          
\*/


 


 


            ,HTMLAPI\_PROP\_MIMEMAXLINELENSEEN
= 102


                           
/\* (r DWORD) Indicates the maximum number of LMBCS characters that have been


                                                encountered
between newlines in the generated HTML.


 


                                                This
proerty is only valid AFTER a calls to GetText() for a given converstion.


 


                                                If
the result of the HTMLCovertXXX() command is "binary" data, then this
property


                                                is
not calculated, and the value returned is meaningless.


 


                                                Details:


                                                When
GetText() is called it calculates "line lengths" by counting


                                                the
number of LMBCS characters between CRLFs.  The maximum line length encountered


                                                is
maitained in this property.


 


                                                Note
that if GetText is called multiple      times with different starting offsets


                                                and
with a return buffer smaller than the total text length, the line length
calculations


                                                may
not be accurate.


                                    


                                                Example: 
assume return buffer contains:


                                                            1
2 3 4 5 6 CR LF 7 8 9


 


                                                            The
text length == 11


 


                                                            Call
GetText with StartingOffset == 0 and \*pTextLength == 11, then this property


                                                            will
have value of 6


 


                                                            Call
GetText with StartingOffset == 0 and \*pTextLength == 4, then this property


                                                            will
have value of 4


 


                                                            Next
call GetText with StartingOffset == 4 and \*pTextLength == 7, then this


                                                            property
will have value of 4.


 


                                    \*/


 


 **Sample Usage :**



 rslt =
HTMLGetProperty(hHTML, HTMLAPI\_PROP\_BINARYDATA, &bBinary);


 if(rslt =
HTMLGetProperty(hHTML, HTMLAPI\_PROP\_TEXTLENGTH, &wTextLength))


{


        PrintLogInfo("HTML
Get Image Binary Length fail");


        //PrintAPIError(rslt);


        return
rslt;


}


 **See Also :**


**[HTMLGetProperty](HTMLGetProperty.md)**


**[HTMLGetText](HTMLGetText.md)**


**[HTMLSetProperty](HTMLSetProperty.md)**



----------------------------------------------------------------------------------------------------------


 





