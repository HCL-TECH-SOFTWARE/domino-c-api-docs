




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




**Initial Release 6**



**Data Type : Composite Data; Rich
Text**



**CDLAYER** **-** Start record
for a layer on a form.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef
struct  

      {  

      BSIG Header;  

      DWORD Reserved[4];  

      } CDLAYER;


 


**Description :**



The
definition for a layer on a form is stored as CD records in the $Body item of
the form note.  A layer is comprised of a Layer Object Run (pointer to box that
represents the layer), Box Run and Position Data. 


 


An example
of the ODS stream describing a layer and its contents:


CDBEGIN -
(signature CDLAYER)


CDLAYER


CDPOSITIONING


CDBOXSIZE


CDBEGIN
(signature CDBACKGROUNDPROPERTIES) - optional


CDBACKGROUNDPROPERTIES
- optional


CDRESOURCE
(SIG\_CD\_HREF of shared image) - optional


CDCOLOR
(SIG\_CD\_BACKGROUNDCOLOR) - optional, if not present the background is
transparent


CDEND
(signature CDBACKGROUNDPROPERTIES) - optional


Next follow
the cd records of the paragraphs in the layer.


If another
CDBEGIN record for a layer is encountered before the CDEND of the previous
layer, this means this is the start of a child layer.


CDEND - (of
signature SIG\_CD\_LAYER)


 


You can
design a form to have text, images, and all other document content positioned
anywhere above or below the normal content layer.   With layers you can
position text over an image. 


 


A layer is
like a table cell that you can position anywhere. A layer behaves like a table
cell in that it is a container to put other objects in.  Unlike a table cell, a
layer has handles for moving and sizing it. A z-index on a layer controls its
position in relation to other layers (in front of or behind them).


 


 **See Also :**


**[CDBACKGROUNDPROPERTIES](CDBACKGROUNDPROPERTIES.md)**


**[CDBOXSIZE](CDBOXSIZE.md)**


**[CDLAYER\_VERSIONxxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E8AD97C1B90E7E31852569830050DD45)**


**[CDPOSITIONING](CDPOSITIONING.md)**



----------------------------------------------------------------------------------------------------------


 





