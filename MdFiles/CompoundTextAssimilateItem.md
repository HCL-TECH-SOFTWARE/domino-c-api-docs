




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



**CompoundTextAssimilateItem** **-
Assimilates one or more TYPE\_COMPOSITE items into a CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAssimilateItem(**  

      DHANDLE  hCompound,  

      NOTEHANDLE  hNote,  

      char far \*pszItemName,  

      DWORD  dwFlags**);**



**Description :**



This routine
assimilates the contents of one or more named TYPE\_COMPOSITE items from a
document into a CompoundText context.  The contents are assimilated in that
PABIDs and styles are fixed up (renumbered/renamed as needed) before they are
appended to the CompoundText context.  

  

Note: This function does not handle features of rich text that depend on
special items that reside outside the rich text field specified by the
"pszItemName" parameter.  

  

Two such features of rich text include doc links that depend on the special
$Links item, and font faces that depend on the special $Fonts item. These
special items in the note reside outside the specified rich text field. 
Therefore, when CompoundTextAssimilateItem merges a rich text field containing
doc links consisting of CDLINK2 records into a Compound Text context, the doc
link in the resulting compound text does not function. A work-around to this
problem is demonstrated by sample program HISTORY in the RICHTEXT directory.   

  

Also, when CompoundTextAssimilateItem merges a rich text field containing font
faces that require a font table (a $Fonts item in the note)  the resulting
compound text does not reflect the font face used in the original field.


 


**Parameters :**



Input :  

hCompound  -  Handle of the CompoundText context.  

  

hNote  -  Handle of the note that contains the TYPE\_COMPOSITE item(s) to
assimilate.  

  

pszItemName  -  Pointer to null-terminated item name to assimilate.  

  

dwFlags  -   Assimilation flags reserved for future use.  Set this parameter to
0L.  

  




Output :  

(routine)  -   Return status from this call:   

  

NOERROR - Successfully assimilated the specified item.  

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

char               \*pszDogs = "It was for\nthe dogs.";  

  

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

  

Status = CompoundTextAddTextExt(hCompound,  

                             dwNormalStyle,  

                             DEFAULT\_FONT\_ID,  

                             pszDogs,  

                             (DWORD)strlen(pszDogs),  

                             "\r\n",  

                             COMP\_PRESERVE\_LINES,  

                             NULL);  

if (Status != NOERROR)  

{  

CompoundTextDiscard(hCompound);  

return Status;  

}  

  

Status = CompoundTextAssimilateItem(     hCompound,  

                                                 hOriginalNote,  

                                                 "Body",  

                                                 0L);  

  

...  

  




 **See Also :**


**[CompoundTextAssimilateFile](CompoundTextAssimilateFile.md)**



----------------------------------------------------------------------------------------------------------


 





