




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




**Initial Release 4.0**



**Symbolic Value : Rich Text**



**PS\_xxx** **-** PRINT\_SETTINGS
- Flags; PRINTNEW\_SETTINGS - Flags


**----------------------------------------------------------------------------------------------------------**



**#include <editods.h>**


 **Symbolic Values :**      PS\_Initialized            -  Print settings have been
initialized.  

  

      PS\_HeaderFooterOnFirst      -  Print header/footer on first page.  

  

      PS\_CropMarks         -  Print crop marks.  

  

      PS\_ChangeBin         -  Paper source should be set for First and Other
Page.  

  

      PS\_HeaderFooterRTL           -  Header/Footer Printing order Right to
Left.  

  

      PS\_ReleaseRightMargin       -  Release the right margin when printing (to
print into gutter)  

  




**Description :**



These
symbols define possible values for the Flags member of the PRINT\_SETTINGS and
PRINTNEW\_SETTINGS structures.


 **See Also :**


**[PRINTNEW\_SETTINGS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/8AE7273B8F8B59E2852560510050C99C)**


**[PRINT\_SETTINGS](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E32B593415FD3E448525605100526907)**


**[EDITEXPORTDATA](EDITEXPORTDATA.md)**



----------------------------------------------------------------------------------------------------------


 





