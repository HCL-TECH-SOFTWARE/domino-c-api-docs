




<!--
 /\* Font Definitions \*/
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



**Function : Basic Encoding Rules;
LDAP**



**ber\_alloc\_t** **-
Constructs and returns a BerElement structure.**


**----------------------------------------------------------------------------------------------------------**



**#include <lber.h>**



BerElement
\* LNPUBLIC **ber\_alloc\_t(**  

      int  options**);**



**Description :**



This routine
constructs and returns a BerElement structure.  The NULLBER pointer is returned
on error.  The options field contains a bitwise-or of options which are to be
used when generating the encoding of this BerElement. Unrecognized option bits
are ignored.


 


The
BerElement returned by ber\_alloc\_t() is initially empty.  Calls to ber\_printf()
will append bytes to the end of the ber\_alloc\_t().


 


Implemented
as a macro:


 


#define
ber\_alloc\_t(options)             ND\_ber\_alloc\_t((options))


 


**Parameters :**



Input :  

options  -  A bitwise-or of options which are to be used when generating the
encoding of this BerElement.  

  




Output :  

(routine)  -  Pointer to a BerElement structure.  

  

  




 **See Also :**


**[BerElement](BerElement.md)**


**[NULLBER](NULLBER.md)**



----------------------------------------------------------------------------------------------------------


 





