




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




 


**Function : Distinguished Name**



**DNCanonicalize** **-
Canonicalizes an abbreviated distinguished name.**


**----------------------------------------------------------------------------------------------------------**



**#include <dname.h>**



STATUS
LNPUBLIC **DNCanonicalize(**  

      DWORD  Flags,  

      const char far \*TemplateName,  

      const char far \*InName,  

      char far \*OutName,  

      WORD  OutSize,  

      WORD far \*OutLength**);**



**Description :**



This
function converts a distinguished name in abbreviated format to canonical
format.  A fully distinguished name is in canonical format - it contains all
possible naming components.  The abbreviated format of a distinguished name
removes the labels from the naming components.


 


**Parameters :**



Input :  

Flags  -  Reserved for future use.  Always pass in 0L for this argument.  

  

TemplateName  -  Optional.  Null-terminated template name string pointer.  Use
NULL to default the template to the current user name.  The template is used
when an abbreviated name consists only of the common name followed by a slash
(such as "Mary Tsen/").  In this case, the resulting canonical name
will have all the component types filled in according to the template.  The
template name string must be in canonical format.  

  

InName  -  Pointer to the null terminated abbreviated distinguished name that
is to be canonicalized.  If this name includes non-standard components or is a
non-distinguished name, the returned name is a copy of the input name.  

  

OutSize  -  Size of the OutName buffer.  

  




Output :  

(routine)  -  Return status of the call - indicates either success or what the
error is. The return codes include:  

  

NOERROR  

  

ERR\_xxx - Error returned by lower level functions.  Call OSLoadString to
interpret the code.  

  

  

OutName  -  Pointer to the returned canonical name string (null terminated). 
This string must be allocated by the caller.  A buffer size of MAXUSERNAME is
sufficient.  

  

OutLength  -  Optional.  Pointer to the returned length of the returned
canonical name string.  Use NULL if this information is not needed.  

  




 **Sample Usage :**


       

char AbbrevName[MAXUSERNAME];   

char CanonName[MAXUSERNAME];  

WORD retLen;    

  

/\* ... \*/  

  

   error = DNCanonicalize (0L, NULL, AbbrevName, CanonName,   

                           MAXUSERNAME, &retLen);     


 **See Also :**


**[DNAbbreviate](DNAbbreviate.md)**


**[DNParse](DNParse.md)**



----------------------------------------------------------------------------------------------------------


 





