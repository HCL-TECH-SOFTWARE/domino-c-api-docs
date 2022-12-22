




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




**Initial Release 4.0**



**Symbolic Value : Font**



**xxx\_FONT\_ID** **-** Font ID
values for pre-defined fonts


**----------------------------------------------------------------------------------------------------------**



**#include <fontid.h>**


 **Symbolic Values :**      DEFAULT\_FONT\_ID             -  FONTID for the Domino default
font. This default is normally plain black 10-point Helvetica.  

  

      DEFAULT\_BOLD\_FONT\_ID              -  FONTID for the Domino default font
with the bold attribute set.  

  

      DEFAULT\_SMALL\_FONT\_ID            -  FONTID for the Domino default
"small" font. This font is normally plain black 9-point Helvetica.  

  

      DEFAULT\_PPEN\_FONT\_ID              -  FONTID for the default permanent pen
font. This font is a bold red version of the default font; some systems may not
be able to display this font in red.  

  

      FOREIGN\_FONT\_ID             -  FONTID for the default font for
"foreign" text. This font is normally a plain black 10-point
fixed-pitch font.  

  




**Description :**



These macros
return FONTID values for the predefined Domino fonts.


 **Sample Usage :**


nError =
CompoundTextAddTextExt (  

hCompound,                 /\* handle to CompoundText context \*/  

dwStyleID,                 /\* style ID \*/  

DEFAULT\_FONT\_ID,           /\* font ID \*/  

StatText,                  /\* text to add \*/  

(DWORD) strlen (StatText), /\* length of text \*/  

"\r\n",                    /\* newline delimiter - handle \r \n   

                                and combinations of \r\n \*/  

COMP\_PRESERVE\_LINES,       /\* preserve line breaks \*/  

NULL);                     /\* optional NLS\_PINFO \*/


 **See Also :**


**[FONTID](FONTID.md)**


**[FONT\_FACE\_xxx](FONT_FACE_xxx.md)**


**[NOTES\_COLOR\_xxx](NOTES_COLOR_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





