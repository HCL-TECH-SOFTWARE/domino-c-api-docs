




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



**Data Type : Composite Data; Rich
Text**



**CDPABFORMULAREF** **-** Identify
both "Hide When" formula and CDPABDEFINITION record


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    BSIG Header;  

    WORD SourcePABID; /\* ID number of the source PAB  

                           containing the formula. \*/  

    WORD DestPABID;   /\* ID number of the dest PAB \*/  

} CDPABFORMULAREF;


 


**Description :**



Starting in
Release 4.0 of Notes, a paragraph may have an associated formula that
determines when the paragraph is to be hidden.  The CDPABFORMULAREF is similar
to the CDPABREFERENCE record, with an additional field that identifies the
CDPABDEFINITION record containing the CDPABHIDE record for the "Hide
When" formula.


  

The fields in this record are:  

  




Header -
Identifies this as a CDPABFORMULAREF record  

  




SourcePABID
- ID number of PAB containing the "Hide When" formula  

  




DestPABID -
ID number of CDPABDEFINITION record for this paragraph


 **See Also :**


**[CDPABDEFINITION](CDPABDEFINITION.md)**


**[CDPABREFERENCE](CDPABREFERENCE.md)**



----------------------------------------------------------------------------------------------------------


 





