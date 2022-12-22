




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




**Initial Release 6**



**Data Type : XML**



**XSLT\_PROPERTY** **-** XSLT
property


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


        xsltResultLog=1,                      /\*
MEMHANDLE,                 Readonly - the result log from the last transform.
\*/


        xsltResultLogComment=2,               /\*
char\*(i)/MEMHANDLE(o),     LMBCS string to be added as comment to top of result
log \*/


        xsltExitOnFirstFatalError=3,  /\*
BOOL,       TRUE = importer exits on first fatal error, \*/


                                             /\*
            FALSE = importer continues even if fatal error found \*/


        xsltInputValidationOption=4,  /\*
Xml\_Validation\_Option,Values defined in Xml\_Validation\_Option: 


                                               
...Validate\_Never, ...Validate\_Always, ...Validate\_Auto \*/


        xsltOutputCharset=5                   /\*
XSLT\_OUTPUT\_CHARSET,xsltOutputUtf8 or xsltOutputUtf16 \*/


 


}
XSLT\_PROPERTY;


 


**Description :**



XSLT\_PROPERTY
default values are set as follows:


 


 Note:   (i)
= can input new value into the exporter.


            (o)
= can get current value out of exporter.


            (io)
= can do both. 


 


 xsltResultLog                          =
(o)     NULLMEMHANDLE


 xsltResultLogComment            =
(io)    NULLMEMHANDLE


 xsltExitOnFirstFatalError          =
(io)    TRUE


 xsltInputValidationOption         =
(io)    Xml\_Validate\_Auto


 xsltOutputCharset                   =
(io)    xsltOutputUtf8


 **See Also :**


**[Xml\_Validation\_Option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B4BEC1AB6DE5693C85256B29005F7317)**


**[XSLTGetTransformProperty](XSLTGetTransformProperty.md)**


**[XSLTSetTransformProperty](XSLTSetTransformProperty.md)**


**[XSLT\_OUTPUT\_CHARSET](XSLT_OUTPUT_CHARSET.md)**



----------------------------------------------------------------------------------------------------------


 





