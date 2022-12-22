




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



**CDEXTFIELD** **-** Extended
field attributes


**----------------------------------------------------------------------------------------------------------**



**#include
<editods.h>**



**Definition :**



typedef struct {  

   WSIG  Header;  

   DWORD Flags1;            /\* Field Flags (see FEXT\_xxx) \*/  

   DWORD Flags2;  

   WORD  EntryHelper;       /\* Field entry helper type  

                              (see FIELD\_HELPER\_xxx) \*/  

   WORD  EntryDBNameLen;    /\* Entry helper DB name length \*/  

   WORD  EntryViewNameLen;  /\* Entry helper View name length \*/  

   WORD  EntryColumnNumber; /\* Entry helper column number \*/  

   /\* Now comes the variable part of the struct... \*/  

} CDEXTFIELD;


 


**Description :**



New field
attributes have been added in Release 4.0 of Notes.  To preserve compatibility
with existing applications, the new attributes have been placed in this
extension to the CDFIELD record.  This record is optional, and may not be
present in the $Body item of the form note.


  

The fields in this structure are:  

  




    Header -
Defines this composite data item as a CDEXTFIELD item.


  

    Flags1 - Extended field flags;  see entry for FEXT\_xxx (CDEXTFIELD -
Flags1)  

  




    Flags2 -
Optional extended field flags.  May be set to 0 or FEXT\_xxx (CDEXTFIELD -
Flags2)  

  




    EntryHelper
- Field entry helper type;  see entry for FIELD\_HELPER\_xxx  

  




   
EntryDBNameLen - Length of helper database name  

  




   
EntryViewNameLen - Length of helper view name  

  




   
EntryColumnNumber - Column number of helper  

  




The
structure is followed by the name of the helper database (if any) and the name
of the helper view (if any).  These names are stored in LMBCS with no NULL
delimter.  The total size of the CDEXTFIELD record includes these strings.


 **See Also :**


**[CDEXTFIELD\_xxxHELPER](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B80DB5F91264821985256203006B899C)**


**[CDFIELD](CDFIELD.md)**


**[FIELD\_HELPER\_xxx](FIELD_HELPER_xxx.md)**


**[FEXT\_xxx (Flags1)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/6F0AB05C5349E00685256203006A4803)**


**[FEXT\_xxx (Flags2)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B92406B45370DA9985256A2A006555DD)**



----------------------------------------------------------------------------------------------------------


 





