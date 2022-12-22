




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



**CDEMBEDDEDSCHEDCTL** **-** Specifies an
embedded scheduling control.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    WSIG           Header;        /\* Signature and length of this record. \*/  

    DWORD   Flags;         /\* EMBEDDEDSCHED\_FLAG\_xxx from above \*/  

    WORD           TargetFrameLength;  

    WORD           DisplayStartDTItemFormulaLength;  

    WORD           HrsPerDayItemFormulaLength;  

    WORD           ReqPeopleItemsFormulaLength;  

    COLOR\_VALUE    BusyTimeColor; /\* Color used for busy times (due to calendar
entry) \*/  

    COLOR\_VALUE FreeTimeColor;    /\* Color used for non-busy times \*/  

    COLOR\_VALUE    NoDataColor;   /\* Color used for no busy time data found \*/  

    COLOR\_VALUE DataRestrictedColor;      /\* Color used for busy time data
restricted \*/  

    COLOR\_VALUE GridLineColor;    /\* Color used to paint grid lines in
scheduler \*/


    WORD           NameColWidth;  /\*
width of the left side of the control where attendee names are displayed \*/  

    WORD           PeopleLines;   /\* Max items in People area if
EMBEDDEDSCHED\_FLAG\_PEOPLE\_FIXEDHEIGHT \*/  

    WORD           RoomsLines;            /\* Max items in Rooms area if
EMBEDDEDSCHED\_FLAG\_ROOMS\_FIXEDHEIGHT \*/  

    WORD           ResourcesLines;        /\* Max items in Resources area if
EMBEDDEDSCHED\_RESOURCES\_PEOPLE\_FIXEDHEIGHT \*/


    WORD           SpareWORD[5];  

    DWORD          SpareDWORD[13];


 


    /\* Target Frame
Name (if any) \*/  

    /\* DisplayStartDTItem formula (if any) \*/  

    /\* HrsPerDayItem formula (if any) \*/  

    /\* RequiredPeopleItems formula (if any) \*/  

} CDEMBEDDEDSCHEDCTL;


 


**Description :**



This CD
record defines an embedded element of type 'group scheduler'.   It is preceded
by a CDHOTSPOTBEGIN and a CDPLACEHOLDER.  The CD record, CDPLACEHOLDER, further
defines the CDEMBEDDEDSCHEDCTL. 


 


WSIG                     Header                                                 Signature
and length of this CD record


DWORD                 Flags                                                    see
EMBEDDEDSCHED\_FLAG\_xxx


WORD                   TargetFrameLength                              Length
of Target Frame, values follows CD fixed portion


WORD                   DisplayStartDTItemFormulaLength        Length
of start date time item information, value follows CD fixed portion


WORD                   HrsPerDayItemFormulaLength              Length
of duration item information, value follows CD fixed portion


WORD                   ReqPeopleItemsFormulaLength             Length
of group member item information, value follows CD fixed portion


COLOR\_VALUE      BusyTimeColor                                     Color
used for busy times (due to calendar entry)


COLOR\_VALUE      FreeTimeColor                                      Color
used for non-busy times


COLOR\_VALUE      NoDataColor                                         Color
used for no busy time data found


COLOR\_VALUE      DataRestrictedColor                              Color
used for busy time data restricted


COLOR\_VALUE      GridLineColor                                       Color
used to paint grid lines in scheduler


WORD                   NameColWidth                                      Width
of the left side of the control where attendee names are displayed  

WORD                   PeopleLines                                          Max
items in People area if EMBEDDEDSCHED\_FLAG\_PEOPLE\_FIXEDHEIGHT  

WORD                   RoomsLines                                         Max
items in Rooms area if EMBEDDEDSCHED\_FLAG\_ROOMS\_FIXEDHEIGHT  

WORD                   ResourcesLines                        Max items in
Resources area if 


                                                                                    EMBEDDEDSCHED\_RESOURCES\_PEOPLE\_FIXEDHEIGHT


WORD                   SpareWORD[5];  

DWORD                 SpareDWORD[13]


 


Note that
rich text fields are items of type TYPE\_COMPOSITE.  Therefore, API programs
that run on non-Intel architecture platforms must perform host/canonical
conversion on CD record structures such as this when accessing rich text item
data in a note.


 


These fields
may be followed by optional items. If you plan to use them, you will need to
declare the variables and assign values to their lengths.


 **See Also :**


**[CDEMBEDDEDSCHEDCTLEXTRA](CDEMBEDDEDSCHEDCTLEXTRA.md)**


**[CDPLACEHOLDER](CDPLACEHOLDER.md)**


**[COLOR\_VALUE](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/467F745F92ADB624852566B80068DCFE)**


**[EMBEDDEDSCHED\_FLAG\_xxx](EMBEDDEDSCHED_FLAG_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





