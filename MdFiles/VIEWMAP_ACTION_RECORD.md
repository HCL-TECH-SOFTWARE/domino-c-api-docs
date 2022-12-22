




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



**VIEWMAP\_ACTION\_RECORD** **-** Navigator
action CD record.


**----------------------------------------------------------------------------------------------------------**



**#include
<vmods.h>**



**Definition :**



typedef struct {  

   WSIG     Header;


   WORD    
bHighlightTouch;  

   WORD     bHighlightCurrent;


   WORD     HLOutlineColor;  

   WORD     HLFillColor;


   WORD    
ClickAction;


   WORD    
ActionStringLen;


   WORD    
HLOutlineWidth;  

   WORD     HLOutlineStyle;


   NOTELINK LinkInfo;


   WORD     ExtDataLen;
/\* length of extended action data, \*/


                       
/\* e.g. compiled script \*/


   WORD    
ActionDataDesignType; /\* design type for the named


                                    
folder or view named in the


                                     ActionString
\*/  

   DWORD    spare[2];   /\* reserved for future use \*/


           /\* Followed
by Action Name string \*/  

} VIEWMAP\_ACTION\_RECORD;


 


**Description :**



Identifies
an action to be performed from a Navigator.  This record is stored in items of
type TYPE\_VIEWMAP\_LAYOUT, the graphical layout of the Navigator, and are paired
with Navigator graphic CD records.  The fields in this structure are:


 


Header                         Defines
this composite data item as a VIEWMAP\_ACTION\_RECORD item.


bHighlightTouch           If
TRUE:  Highlight when touched.


bHighlightCurrent          If
TRUE:  Highlight when clicked.


HLOutlineColor             Color
for are outline.   Use NOTES\_COLOR\_xxx value.


HLFillColor                   Fill
color for area.   Use NOTES\_COLOR\_xxx value.


ClickAction                   Action
to perform;  must be a VM\_ACTION\_xxx value.


ActionStringLen            Length
of the name of the action to perform, or 0 if not applicable; used by
VM\_ACTION\_SWITCH\_VIEW, VM\_ACTION\_SWITCHNAV, and VM\_ACTION\_ALIAS\_FOLDER values. 


HLOutlineWidth             Line
width of area outline.


HLOutlineStyle              Style
of area outline.   Use VM\_LINE\_xxx value.


LinkInfo                        If
a note is associated with this action, a link to that note is stored in this
field, or 0 if not      applicable; used by VM\_ACTION\_GOTO\_LINK ClickAction
value.   See NOTELINK.


ExtDataLen                   Length
of extended action data, or 0 if not applicable; used by VM\_ACTION\_RUNFORMULA
and VM\_ACTION\_RUNSCRIPT values.


ActionDataDesignType Design
type for the object named in the Action String, or 0 if not applicable; used by
VM\_ACTION\_SWITCH\_VIEW, VM\_ACTION\_SWITCHNAV, and VM\_ACTION\_ALIAS\_FOLDER values. 
Use DESIGN\_TYPE\_xxx value.


spare                            Reserved; 
must be 0.


 


This record
is followed by the string containing the name of the action to be performed (if
any).


 


 **See Also :**


**[NOTELINK](NOTELINK.md)**


**[VM\_ACTION\_xxx](VM_ACTION_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





