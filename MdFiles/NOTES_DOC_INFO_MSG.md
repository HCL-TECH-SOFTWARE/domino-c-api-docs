




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




 


**Data Type : Notes/FX data**



**NOTES\_DOC\_INFO\_MSG** **-** Notes/FX
data sent by Notes to OLE server.


**----------------------------------------------------------------------------------------------------------**



**#include
<olenotes.h>**



**Definition :**



typedef struct


        {


        WORD
          Version;                      /\* Version of this structure \*/


        NOTELINK
      DocLink;               /\* Document in which OLE object resides \*/      


        WORD
          DocOpenMode;           /\* DOC\_OPENMODE\_??? flags below \*/


        WORD
          DocFlags;                     /\* DOC\_FLAGS\_??? flags below\*/


        WORD
          UserAccess;            /\* USER\_ACCESS\_??? flags below \*/


        HWND
          hDocWnd;                      /\* Notes document window handle \*/


        char
          UserName[MAXUSERNAME]; /\* Notes user name \*/


        NOTEHANDLE
    hNote;         /\* Handle to document's note: THIS IS READ ONLY! its
lifetime is only for duration of the SetData method \*/


        NOTEHANDLE
    hFXNote;               /\* Empty note, associated with document's DB. A
server should use this for writing items to be applied to hNote \*/


        WORD 
         cNumDocActions;        /\* Count of doc actions, if any. Only passed to
server if registered to support NotesDocAction GetData() \*/


        DHANDLE
               hDocActions;       /\* Notes OSMemAlloc() handle to
DOC\_ACTION\_INFO \*/


        DWORD
         dwUnused[2];


        }
NOTES\_DOC\_INFO\_MSG;


 


 


**Description :**



This is the
structure of the Notes/FX data sent from Notes to an OLE server's SetData
method.  The data in this structure allows data to be exchanged between an OLE
object embedded in a note and the note containing the object.


 **Sample Usage :**


 


 **See Also :**


**[DOC\_ACTION\_INFO](DOC_ACTION_INFO.md)**


**[DOC\_FLAGS\_xxx](DOC_FLAGS_xxx.md)**


**[DOC\_OPENMODE\_xxx](DOC_OPENMODE_xxx.md)**


**[NOTES\_DOC\_INFO\_VERSIONxxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/00330043005400B185255EC60071FB64)**


**[NSFDbReopen](NSFDbReopen.md)**


**[USER\_ACCESS\_xxx](USER_ACCESS_xxx.md)**



----------------------------------------------------------------------------------------------------------


 





