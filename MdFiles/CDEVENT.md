




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



**Data Type : Composite Data; Rich
Text**



**CDEVENT** **-** Structure
which defines simple actions, fromulas or LotusScript for an image map..


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {


   WSIG  Header;


   DWORD Flags;


   WORD 
EventType;       /\* one of HTML\_EVENT\_xxx \*/


   WORD 
ActionType;      /\* one of ACTION\_TYPE\_xxx \*/


   DWORD
ActionLength;    /\* length of actions that follows \*/


    WORD    SignatureLength;
/\* length of signature, if any \*/


   BYTE  Reserved[14];


/\*  Action follows here
\*/


/\* Signature follows
here \*/


} CDEVENT;


 


**Description :**



This CD
structure defines simple actions, formulas or LotusScript within a given image
map.


 


Header                   Signature
defining CDEVENT.


Flags                      See
EVENT\_HAS\_LIBRARIES.


EventType              See
HTML\_EVENT\_xxx and HTML\_EVENT\_CLIENT\_xxx for values.


ActionType             See
ACTION\_TYPE\_xxx for values.


ActionLength


SignatureLength


Reserved[14]


 


 


If the **ActionType** is **ACTION\_TYPE\_JAVASCRIPT**, the
ActionLength indicates the total length of the JavaScript code.  The CDEVENT
record is followed by one or more CDBLOBPART records, each one of them is
followed by a section of the JavaScript code.  Loop through all the CDBLOBPART
records to read in the complete JavaScript code.


 **See Also :**


**[ACTION\_TYPE\_xxx](ACTION_TYPE_xxx.md)**


**[CDBLOBPART](CDBLOBPART.md)**


**[EVENT\_HAS\_LIBRARIES](EVENT_HAS_LIBRARIES.md)**


**[HTML\_EVENT\_CLIENT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EF32EDB179A1471A85256983004C2207)**


**[HTML\_EVENT\_xxx](HTML_EVENT_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





