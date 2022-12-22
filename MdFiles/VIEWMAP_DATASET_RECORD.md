




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



**Data Type : Navigators**



**VIEWMAP\_DATASET\_RECORD** **-** Navigator
settings CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   WORD  Version;  

    WORD  ViewNameLen; /\* length of initial view name; 0 if none \*/  

   WORD  Gridsize;    /\* (in pixels) \*/  

   WORD  Flags;       /\* VM\_DSET\_xxx \*/  

   WORD  bAutoAdjust;  

   WORD  BGColor;  

   WORD  SeqNums[VM\_MAX\_OBJTYPES]; /\* highest sequence number for \*/


                                 
/\* each type of draw object \*/


                                 
/\* supported (w/extra space for \*/


                                 
/\* future) \*/  

   VIEWMAP\_STYLE\_DEFAULTS StyleDefaults;  

   WORD  NumPaletteEntries;  

   WORD  ViewDesignType;           /\* design type of initial view \*/  

   COLOR\_VALUE BGColorValue;       /\* BG color stored in some color


                                     
space \*/  

   DWORD spare[14];


}
VIEWMAP\_DATASET\_RECORD;


 


**Description :**



The
VIEWMAP\_DATASET\_RECORD stores the settings and defaults for a Navigator.  The
fields in this structure are:


 


Header           
Defines this composite data item as a


                 
VIEWMAP\_DATASET\_RECORD item.


Version          
Version number of this structure.


ViewNameLen      
Length of the inital view name;  may be 0.


Gridsize          Size
of any displayed grid, in pixels.


Flags            
Option flags (see VM\_DSET\_xxx).


bAutoAdjust       If
TRUE, automatically adjust the display to


                  show
as much of the Navigator as possible.


BGColor          
Background color for the Navigator.


SeqNums           Each
type of graphical object is numbered in


                 
sequence.  This array stores the highest number


                 
assigned in this navigator.


StyleDefaults    
Structure containing the default settings for


                 
graphical elements.


NumPaletteEntries
Number of color palette entries required to


                 
display this Navigator.


ViewDesignType   
Design type of the initial view.


BGColorValue


spare            
Reserved; must be 0.


 


 **See Also :**


**[VM\_MAX\_OBJTYPES](VM_MAX_OBJTYPES.md)**


**[VIEWMAP\_STYLE\_DEFAULTS](VIEWMAP_STYLE_DEFAULTS.md)**


**[VIEWMAP\_VERSION](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/E13066D4308549648525626100700530)**


**[VM\_DSET\_xxx](VM_DSET_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





