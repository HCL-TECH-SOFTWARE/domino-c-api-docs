




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




 


**Function : Compound Text**



**CompoundTextDefineStyle** **- Defines a
CompoundText style.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextDefineStyle(**  

      DHANDLE  hCompound,  

      char far \*pszStyleName,  

      COMPOUNDSTYLE far \*pDefinition,  

      DWORD far \*pdwStyleID**);**



**Description :**



This routine
defines a CompoundText style for use in calls to CompoundTextAddParagraphExt
and CompoundTextAddTextExt..


 


**Parameters :**



Input :  

hCompound  -  Handle of CompoundText context.  

  

pszStyleName  -  Pointer to the null-terminated style name.  

  

pDefinition  -  Pointer to COMPOUNDSTYLE structure which defines paragraph
attributes for the style.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully defined a style.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

pdwStyleID  -  Pointer to a DWORD where the Style ID will be returned.  The
Style ID is used in subsequent calls to CompoundTextAddParagraphExt and
CompoundTextAddTextExt to reference the style definition.  

  




 **Sample Usage :**


  

COMPOUNDSTYLE  Style;  

DWORD          dwNormalStyle;  

  

CompoundTextInitStyle(&Style);  

Status = CompoundTextDefineStyle( hCompound  

                                  "Normal",  

                                  &Style,  

                                  &dwNormalStyle);


 **See Also :**


**[CompoundTextInitStyle](CompoundTextInitStyle.md)**


**[CompoundTextAddParagraphExt](CompoundTextAddParagraphExt.md)**


**[CompoundTextAddTextExt](CompoundTextAddTextExt.md)**



----------------------------------------------------------------------------------------------------------


 





