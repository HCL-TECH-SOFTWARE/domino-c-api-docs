




<!--
 /\* Font Definitions \*/
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




 


**Function : Compound Text**



**CompoundTextAddDocLink** **- Inserts a
DocLink in a CompoundText context**


**----------------------------------------------------------------------------------------------------------**



**#include <easycd.h>**



STATUS
LNPUBLIC **CompoundTextAddDocLink(**  

      DHANDLE  hCompound,  

      TIMEDATE  DBReplicaID,  

      UNID  ViewUNID,  

      UNID  NoteUNID,  

      char far \*pszComment,  

      DWORD  dwFlags**);**



**Description :**



This
function inserts a DocLink in a CompoundText context.


 


**Parameters :**



Input :  

hCompound  -  Handle to the CompoundText context.  

  

DBReplicaID  -  Replica ID of the database that contains the note (document)
pointed to by the DocLink.  

  

ViewUNID  -  UNID of the view that contains the note (document) pointed to by
the DocLink.  

  

NoteUNID  -  UNID of the note (document) pointed to by the DocLink.  

  

pszComment  -  Pointer to a NULL terminated string.  This string appears when
the DocLink is selected (clicked on).  

  

dwFlags  -  Flags reserved for future use.  Set this parameter to 0L.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully added the DocLink to the CompoundText context.  

ERR\_xxx - Errors returned by lower level functions: (memory management, file
operations, network errors, etc.).  There are so many possible causes, that it
is best to use the code in a call to OSLoadString and display/log the error for
the user as your default error handling.  

  

  

  




 **See Also :**


**[CDLINK2](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/00A50061002B004585255E7D0081902C)**


**[CDLINKEXPORT2](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255D2800785F80)**


**[NOTELINK](NOTELINK.md)**



----------------------------------------------------------------------------------------------------------


 





