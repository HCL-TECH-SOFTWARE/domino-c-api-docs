




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




**Initial Release 5.0**



**Function : Compound Text**



**CompoundTextAddParagraphExt** **- Writes a
paragraph of text to a CompoundText context.**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAddParagraphExt(**  

      DHANDLE  hCompound,  

      DWORD  dwStyleID,  

      FONTID  FontID,  

      char far \*pchText,  

      DWORD  dwTextLen,  

      NLS\_PINFO  pInfo**);**



**Description :**



NOTE: This
function replaces the deprecated function CompoundTextAddParagraph.


 


      This
routine writes a paragraph of text to a CompoundText context.  The text must
not contain any special characters such as '\r', '\n' or '\0'.  

  

This routine is best used when you know the exact format of the text you want
written to the CompoundText context (for example you just created a text string
using sprintf).  Use CompoundTextAddTextExt if you would like text parsed into
lines and/or paragraphs before is is written into the CompoundText context.  

  

This routine provides the most efficient means of getting text into CD format
because, if translation is not necessary, the text is never parsed.  

  

If the pInfo parameter is specified, the text will be translated (imported)
into Domino format (LMBCS) using the specified character set. Specify NULL for
pInfo if the text is LMBCS format already.  

  

To specify a character set, call NLS\_load\_charset first, specifying the file
name of the appropriate character set. NLS\_load\_charset returns a pointer to
use as the pInfo parameter value.


 


**Parameters :**



Input :  

hCompound  -  Handle of CompoundText context.  

  

dwStyleID  -  CompoundText style ID as defined by a previous call to
CompoundTextDefineStyle.  

  

FontID  -  Specifies the FONTID.  

  

pchText  -  Pointer to a buffer that contains the text to add.  

  

dwTextLen  -  Length of the text to add.  

  

pInfo  -  Pointer to an NLS\_INFO structure.  

  




Output :  

(routine)  -    Return status from this call:   

  

NOERROR - Successfully added the paragraph to the CompoundText context.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  




 **Sample Usage :**


  

COMPOUNDSTYLE  Style;  

STATUS         Status;  

DHANDLE         hCompound;  

WORD           dwNormalStyle;  

char               \*pszTree = "They cannot see the forest for the
trees.";  

char               \*pszDogs = "It was for the dogs.";


 


  

Status = CompoundTextCreate(NULLHANDLE, NULL, &hCompound);  

if (Status != NOERROR)  

    return Status;  

  

CompoundTextInitStyle(&Style);  

Status = CompoundTextDefineStyle( hCompound  

                                  "Normal",  

                                  &Style,  

                                  &dwNormalStyle);  

                                     

Status = CompoundTextAddParagraphExt(hCompound,  

                                     dwNormalStyle,  

                                     DEFAULT\_FONT\_ID,  

                                     pszTree,  

                                     (DWORD)strlen(pszTree),  

                                     NULL);  

if (Status != NOERROR)  

{  

CompoundTextDiscard(hCompound);  

return Status;  

}  

  

Status = CompoundTextAddParagraphExt(hCompound,  

                                     dwNormalStyle,  

                                     DEFAULT\_FONT\_ID,  

                                     pszDogs,  

                                     (DWORD)strlen(pszDogs),  

                                     NULL);  

if (Status != NOERROR)  

{  

CompoundTextDiscard(hCompound);  

return Status;  

}  

...


 **See Also :**


**[NLS\_load\_charset](NLS_load_charset.md)**


**[CompoundTextAddTextExt](CompoundTextAddTextExt.md)**


**[CompoundTextDefineStyle](CompoundTextDefineStyle.md)**


**[NLS\_PINFO](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/CD47F3E691E37C4E852561C00078D60C)**



----------------------------------------------------------------------------------------------------------


 





