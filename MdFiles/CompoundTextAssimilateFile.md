




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



**CompoundTextAssimilateFile** **-
Assimilates contents of a CD file into a CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAssimilateFile(**  

      DHANDLE  hCompound,  

      char far \*pszFileName,  

      DWORD  dwFlags**);**



**Description :**



This routine
assimilates the contents of a CD file (a file containing rich text) into a
CompoundText context.  The contents are assimilated in that PABIDs and styles
are fixed up (renumbered/renamed as needed) before they are appended to the
CompoundText context.  

  

A CD file is a file containing data in Domino rich text format.
CompoundTextClose() creates a CD file when closing a stand alone context
containing more than 64K bytes of rich text.  A CD file consists of a datatype
word (usually TYPE\_COMPOSITE) followed by any number of CD records. The data
type word is always in Host (machine-specific) format.  The remainder of the
data in a CD file is in Domino Canonical format.


 


**Parameters :**



Input :  

hCompound  -  Handle of the CompoundText context.  

  

pszFileName  -  Pointer to null-terminated file specification of the file to
assimilate. The file must contain the data for a Domino rich text field in
Domino canonical format, beginning with the data type word.  

  

dwFlags  -  Assimilation flags reserved for future use.  Set this parameter to
0L.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully assimilated the contents of the CD file.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


COMPOUNDSTYLE  Style;  

STATUS         Status;  

DHANDLE         hCompound;  

DWORD          dwNormalStyle;  

char               \*pszTree = "They cannot see the forest\nfor the
trees.";  

  

Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);  

if (Status != NOERROR)  

    return Status;  

  

CompoundTextInitStyle(&Style);  

Status = CompoundTextDefineStyle( hCompound  

                                  "Normal",  

                                  &Style,  

                                  &dwNormalStyle);  

                                     

Status = CompoundTextAddTextExt(hCompound,  

                             dwNormalStyle,  

                             DEFAULT\_FONT\_ID,  

                             pszTree,  

                             (DWORD)strlen(pszTree),  

                             "\r\n",  

                             COMP\_PRESERVE\_LINES,  

                             NULL);  

if (Status != NOERROR)  

{  

CompoundTextDiscard(hCompound);  

return Status;  

}  

  

Status = CompoundTextAssimilateFile(     hCompound,  

                                                 "c:\\rich.txt",  

                                                 0L);  

if (Status != NOERROR)  

{  

CompoundTextDiscard(hCompound);  

return Status;  

}  

...


 **See Also :**


**[CompoundTextAssimilateItem](CompoundTextAssimilateItem.md)**


**[CompoundTextClose](CompoundTextClose.md)**



----------------------------------------------------------------------------------------------------------


 





