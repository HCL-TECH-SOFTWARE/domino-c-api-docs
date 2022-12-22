




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



**CDEVENTENTRY** **-** Contains
additional event information for Notes/Domino 6.


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

    WSIG    Header;        /\* Signature and length of this record \*/  

    WORD    wPlatform;             /\* Platform type \*/  

    WORD    wEventId;              /\* Event id. The event that this will run
on... OnClick, Exit, etc. \*/  

    WORD    wActionType;   /\* Action type (the language... LotusScript,
Javascript, Formula, etc. \*/  

    WORD    wReserved;             /\* future use \*/  

    DWORD   dwReserved;            /\* future use \*/  

} CDEVENTENTRY;


 


**Description :**



Contains
additional event information for Notes/Domino 6.


  

The fields in this structure are:  

  




    Header -
Signature and length of this record.


    


   
wPlatform - Platform type (see PLATFORM\_TYPE\_xxx).


 


    wEventId
- Event id:   HTML\_EVENT\_XXX, HTML\_EVENT\_CLIENT\_XXX, . The event that this will
run on... onClick, Exit, etc. 


 


   
wActionType - Action type (the language... LotusScript, Javascript, Formula,
etc.)


                          Use
the following enumerated data type for the values of the wActionType field:


                          


typedef enum ACTION\_TYPE


  {


  ACTION\_FORMULA = 0,


  ACTION\_CANNED\_ACTION,


  ACTION\_LOTUS\_SCRIPT,


  ACTION\_MISC,


  ACTION\_COLLECTION\_RULE,


  ACTION\_JAVA\_FILE,


  ACTION\_JAVA,


  ACTION\_JAVASCRIPT,


  ACTION\_JAVASCRIPT\_COMMON, // Use same javascript for both client
and web


  ACTION\_UNUSED,            // UNUSED


  ACTION\_SECTION\_EDIT,      // fullpack search on 12/10/00 showed
no use of this


  ACTION\_NULL, 


  ACTION\_PROPERTIES,        // Obj properties (initially for OLE
properties)


  ACTION\_JSP,               // The code is jsp code


  ACTION\_HTML,                    // The code is HTML


  ACTION\_MAX,               // The end of the 'real' types


  ACTION\_OTHER = 98,


  ACTION\_UNKNOWN


  } ACTION\_TYPE;


 


   
wReserved - Future use.


 


    dwReserved
- Future use.


 


Note that
CDEVENTENTRY records reside in items of type TYPE\_COMPOSITE. Therefore, API
programs that run on non-Intel architecture platforms must perform
host/canonical conversion on structures of this type when accessing these records
in an item in a note.


 **See Also :**


**[CDEVENT](CDEVENT.md)**


**[HTML\_EVENT\_CLIENT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/EF32EDB179A1471A85256983004C2207)**


**[HTML\_EVENT\_xxx](HTML_EVENT_xxx.md)**


**[PLATFORM\_TYPE\_xxx](PLATFORM_TYPE_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





