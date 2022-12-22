




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




**Initial Release 7.0.2**



**Data Type : HTML**



**UAT** **-** URL
Addressable Type


**----------------------------------------------------------------------------------------------------------**



**#include
<urltypes.h>**



**Definition :**



typedef enum
\_UAT


{


   
UAT\_None                    = 0,


   
UAT\_Server                  = 1,


   
UAT\_Database                = 2,


   
UAT\_View                    = 3,


   
UAT\_Form                    = 4,


   
UAT\_Navigator               = 5,


   
UAT\_Agent                   = 6,


   
UAT\_Document                = 7,


   
UAT\_Filename                = 8,    /\* internal filename of attachment \*/


   
UAT\_ActualFilename          = 9,    /\* external filename of attachment if
different \*/


   
UAT\_Field                   = 10,


   
UAT\_FieldOffset             = 11,


   
UAT\_FieldSuboffset          = 12,


   
UAT\_Page                    = 13,


   
UAT\_FrameSet                = 14,


   
UAT\_ImageResource           = 15,


   
UAT\_CssResource             = 16,


   
UAT\_JavascriptLib           = 17,


   
UAT\_FileResource            = 18,


   
UAT\_About                   = 19,


   
UAT\_Help                    = 20,


   
UAT\_Icon                    = 21,


   
UAT\_SearchForm              = 22,


   
UAT\_SearchSiteForm          = 23,


   
UAT\_Outline                 = 24,


 


   
UAT\_NumberOfTypes           /\* must be the last one \*/


}
UAT;


 


**Description :**



This can be
used to determine the URL address type, some operation on the generated HTML
text should be done according to the URL type. For more information, please
refer the samples released with the C API toolkit


 **Sample Usage :**


see sample
html/convattach


 **See Also :**


**[HTMLAPI\_URLTargetComponent](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/2827D557FD70E40E48257196003EC7DC)**



----------------------------------------------------------------------------------------------------------


 





