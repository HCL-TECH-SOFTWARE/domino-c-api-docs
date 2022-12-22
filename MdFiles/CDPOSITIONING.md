




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




**Initial Release 6**



**Data Type : Composite Data**



**CDPOSITIONING** **-** Defines
position information for a layer box. 


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct  

   {  

   BSIG              Header;  

   BYTE              Scheme;  

   BYTE              bReserved;              /\*  reserved for future use \*/  

   LONG              ZIndex;  

   LENGTH\_VALUE      Top;  

   LENGTH\_VALUE      Left;  

   LENGTH\_VALUE      Bottom;  

   LENGTH\_VALUE      Right;                  /\*  not implemented \*/


      ALIGNED\_NUMBER    BrowserLeftOffset;      /\* 
subtract from Top.Length to get left for a browser \*/


      ALIGNED\_NUMBER    BrowserRightOffset;     /\* 
not implemented \*/  

      } CDPOSITIONING;


 


**Description :**



This CD
record contains position information for a layer box. The fields in this record
are:


 


Header                         Signature
and Length of this CD record.


Scheme                        See
CDPOSITIONING\_SCHEME\_xxx. 


bReserved                    Reserved
for future use.


ZIndex                          Controls
the position of a layer in relation to other layers (in front of or behind
them).


Top                              The
upper position of a CDBOX in a layer.


Left                              The
left position of a CDBOX in a layer.


Bottom                         The
lower position of a CDBOX in a layer.


Right                            Not
implemented.


            BrowserLeftOffset 
      Subtract from Top.Length to get left for a browser.


            BrowserRightOffset      Not
implemented.


 


 **See Also :**


**[CDBOXSIZE](CDBOXSIZE.md)**


**[CDLAYER](CDLAYER.md)**


**[CDPOSITIONING\_SCHEME\_xxx](CDPOSITIONING_SCHEME_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





