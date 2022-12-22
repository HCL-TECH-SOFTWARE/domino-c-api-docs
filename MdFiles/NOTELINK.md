




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
@font-face
 {font-family:"Tms Rmn";
 panose-1:2 2 6 3 4 5 5 2 3 4;}
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




 


**Data Type : IDs**



**NOTELINK** **-** The
structure that uniquely describes a note in a document link.


**----------------------------------------------------------------------------------------------------------**



**#include
<nsfdata.h>**



**Definition :**



typedef struct {  

   TIMEDATE File;  /\* File's replica ID \*/  

   UNID     View;  /\* View's Note Creation TIMEDATE \*/  

   UNID     Note;  /\* Note's Creation TIMEDATE \*/  

} NOTELINK;


 


**Description :**



This
structure uniquely describes a particular instance of a note.  It is a
component of a CDLINKEXPORT2 record, which constitutes a document link in a
rich text field.  The members of this structure   

specify the target ("linked-to") document.


 **Sample Usage :**


    /\*  

     \* Create the IDs for both of the Notes (view and data)  

     \*/  

  

    NoteUNID.File = NoteOID.File;  

    NoteUNID.Note = NoteOID.Note;  

  

    ViewUNID.File = ViewOID.File;  

    ViewUNID.Note = ViewOID.Note;  

  

    /\*  

     \* Fill in the CDLINKEXPORT2 structure  

     \*/  

  

    /\* 1. File's replica ID \*/  

      

    pCDLink->NoteLink.File = DBReplica.ID;  

  

    /\* 2. View Note's UNID (contains the Creation TIMEDATE) \*/  

  

    memmove(&pCDLink->NoteLink.View, &ViewUNID, sizeof(UNID));  

      

    /\* 3. Note's UNID (contains the Creation TIMEDATE) \*/  

  

    memmove(&pCDLink->NoteLink.Note, &NoteUNID, sizeof(UNID));


 **See Also :**


**[CompoundTextAddDocLink](CompoundTextAddDocLink.md)**


**[CDLINKEXPORT2](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255D2800785F80)**


**[TIMEDATE](TIMEDATE.md)**


**[UNID](UNID.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**



----------------------------------------------------------------------------------------------------------


 





