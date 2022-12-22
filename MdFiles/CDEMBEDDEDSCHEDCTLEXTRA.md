




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



**Data Type : Composite Data; Rich
Text**



**CDEMBEDDEDSCHEDCTLEXTRA** **-** Extended
field attributes for CDEMBEDDEDSCHEDCTL.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct


        {


        WSIG           Header;


        WORD           FixedPartLength;              /\*
bytes of this structure \*/


        DWORD          Flags;                                /\*
EMBEDDEDSCHEDEXT\_FLAG\_xxx from above \*/


 


        /\*
Colors used for the scheduler ODLists \*/


 


        COLOR\_VALUE    SchedHdrBkgndColor;           /\*
Bkgnd color for the Scheduler ODList headers \*/


        COLOR\_VALUE
SchedHdrFontColor;               /\* Font color for the Scheduler ODList headers
\*/


 


        COLOR\_VALUE    SchedBkgndColor;  
           /\* Bkgnd color for the scheduler ODList \*/


 


        COLOR\_VALUE    NameHdrBkgndColor;            /\*
Bkgnd color for name ODList header area\*/


        COLOR\_VALUE
NameHdrFontColor;         /\* Font color for name ODList header area \*/


 


        COLOR\_VALUE    NameBkgndColor;               /\*
Normal bkgnd color for attendee names \*/


        COLOR\_VALUE    NameMouseBkgndColor;   /\*
Mouse over bkgnd color for attendee names \*/


        COLOR\_VALUE    NameSelectBkgndColor;  /\*
Select bkgnd color for attendee names \*/


 


        COLOR\_VALUE    NameFontColor;                /\*
Normal font color for attendee names \*/


        COLOR\_VALUE    NameMouseFontColor;           /\*
Mouse over font color for attendee names \*/


        COLOR\_VALUE    NameSelectFontColor;   /\*
Select font color for attendee names \*/


 


        /\*
Formula & text lengths \*/


        WORD           OptPeopleItemsFormulaLength;


        WORD           ReqRoomsItemsFormulaLength;


        WORD           OptRoomsItemsFormulaLength;


        WORD           ReqResourcesItemsFormulaLength;


        WORD           OptResourcesItemsFormulaLength;


        WORD           IntervalStartDTItemFormulaLength;


        WORD           IntervalEndDTItemFormulaLength;


        WORD           SchedulerNameLength;


        WORD           PeopleTitleLength;


        WORD           RoomsTitleLength;


        WORD           ResourcesTitleLength;


        WORD           IntervalChangeEventFormulaLength;


        COLOR\_VALUE
ProfileColor;     /\* Color used to paint busy times (due to freetime
availability from calendar profile) \*/


        WORD           SchedDetailItemsFormulaLength;


 


        COLOR\_VALUE    SuggBkgndColor;                       /\*
bkgnd colors for suggestions odlist \*/


        COLOR\_VALUE
SuggMouseBkgndColor;


        COLOR\_VALUE
SuggSelectBkgndColor;


 


        WORD           DetailDisplayFormFormulaLength;


        WORD           SuggestionsAvailEventFormulaLength;


        WORD           wReserved[2];


 


        DWORD          dwReserved[6];                /\*
Reserved for future use, must be zero \*/


 


        /\*
Variable length data follows if specified \*/


        /\*
OptionalPeopleItems formula (if any) \*/


        /\*
RequiredRoomsItems formula (if any) \*/


        /\*
OptionalRoomsItems formula (if any) \*/


        /\*
RequiredResourcesItems formula (if any) \*/


        /\*
OptionalResourcesItems formula (if any) \*/


        /\*
IntervalStartDT formula (if any) \*/


        /\*
IntervalEndDT formula (if any) \*/


        /\*
SchedulerName (if any) \*/


        /\*
People Title (if any) \*/


        /\*
Rooms Title (if any) \*/


        /\*
Resources Title (if any) \*/


        /\*
Appointment Interval Change Event Formula (if any) \*/


        /\*
SchedDetailItemsFormula (if any) \*/


        /\*
DetailDisplayFormFormula (if any) \*/


        /\*
SuggestionsAvailEventFormula (if any) \*/


        }
CDEMBEDDEDSCHEDCTLEXTRA;


 


 


**Description :**




New
field attributes have been added in Notes/Domino 6.  To preserve compatibility
with existing applications, the new attributes have been placed in this
extension to the CDEMBEDDEDSCHEDCTL record.  This record is optional, and may
not be present in the $Body item of the form note.


  

The fields in this structure are:


 


Header
- Signature and length of this CD record


FixedPartLength
- Length in bytes of this structure


Flags
- See EMBEDDEDSCHEDEXT\_FLAG\_xxx


SchedHdrBkgndColor
- Background color of scheduler headers  

SchedHdrFontColor - Font color of scheduler headers


SchedBkgndColor
- Background color of scheduler 


NameHdrBkgndColor
- Background color of name header area   

NameHdrFontColor - Font color of name header area


NameBkgndColor
- Normal background color of attendee names  

NameMouseBkgndColor - Mouse over background color of attendee names  

NameSelectBkgndColor - Select background color of attendee names


NameFontColor
- Normal font color of attendee names  

NameMouseFontColor - Mouse over font color of attendee names  

NameSelectFontColor - Select font color of attendee names


OptPeopleItemsFormulaLength
- Length of optional people items formula, value follows CD fixed portion


ReqRoomsItemsFormulaLength
- Length of required rooms items formula, value follows CD fixed portion


OptRoomsItemsFormulaLength
- Length of optional rooms items formula, value follows CD fixed portion


ReqResourcesItemsFormulaLength
- Length of required resources items formula, value follows CD fixed portion


OptResourcesItemsFormulaLength
- Length of optional resources items formula, value follows CD fixed portion


IntervalStartDTItemFormulaLength
- Length of interval start date time item formula, value follows CD fixed
portion


IntervalEndDTItemFormulaLength
- Length of interval end date time item formula, value follows CD fixed portion


SchedulerNameLength
- Length of scheduler name, value follows CD fixed portion


PeopleTitleLength
- Length of people title, values follows CD fixed portion


RoomsTitleLength
- Length of rooms title, values follows CD fixed portion


ResourcesTitleLength
- Length of resources title, value follows CD fixed portion


IntervalChangeEventFormulaLength
- Length of interval change event formula, value follows CD fixed portion


ProfileColor
- Color used to paint busy times (due to freetime availability from calendar
profile)


SchedDetailItemsFormulaLength
- Length of schedule detail items formula, value follows CD fixed portion


COLOR\_VALUE            SuggBkgndColor
- Suggested background color.


COLOR\_VALUE
SuggMouseBkgndColor - Suggested mouse background color.


COLOR\_VALUE
SuggSelectBkgndColor - Suggested selction background color.


DetailDisplayFormFormulaLength


wReserved[1]


dwReserved[7]
- Reserved for future use. Must be zero.


 


Note
that rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on CD record structures such as this when accessing
rich text item data in a note.


 


These
fields may be followed by optional items. If you plan to use them, you will
need to declare the variables and assign values to their lengths.


 **See Also :**


**[CDEMBEDDEDSCHEDCTL](CDEMBEDDEDSCHEDCTL.md)**


**[EMBEDDEDSCHEDEXT\_FLAG\_xxx](EMBEDDEDSCHEDEXT_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





