




<!--
 /\* Font Definitions \*/
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




**Initial Release 4.5**



**Function : OLE**



**NSFNoteDeleteOLE2Object** **- Delete an
OLE2 structured storage object.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfole.h>**



STATUS
LNPUBLIC **NSFNoteDeleteOLE2Object(**  

      NOTEHANDLE  hNote,  

      char \*pszObjectName,  

      BOOL  fDeleteObjInfo,  

      ENCRYPTION\_KEY \*pEncryptionKey,  

      DWORD  dwFlags**);**



**Description :**



Delete an
OLE2 structured storage object stored in a note as an extendable file object. 
Also, optionally delete the associated $OLEOBJINFO item.


 


**Parameters :**



Input :  

hNote  -  Note handle of open note  

  

pszObjectName  -  Name of the OLE $FILE object which is the "master"
extendable file object ("ext\*\*\*") in the set of $FILE objects that
comprise this OLE object.  

  

fDeleteObjInfo  -  True if the associated $OLEOBJINFO with this object should
also be deleted.  

  

pEncryptionKey  -  The note's bulk data encryption key, acquired from
NSFNoteDecrypt(...). Necessary to decrypt the $FILE extent table.  

  

dwFlags  -  Additional flags, unused at this time, must be 0.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_NSF\_NOT\_SUPPORTED - This function is not supported on this platform.  In
Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on
Windows 32-bit platforms only.  As of Release 5.0.8, this function is supported
on all Domino and Notes platforms.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  Use
OSLoadString and display/log the error.  

  

  




 **See Also :**


**[NSFNoteAttachOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70A324C757A4B187852563B1006D80A4)**


**[NSFNoteExtractOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1C15F3B7BC6C9E11852563B1006BD694)**



----------------------------------------------------------------------------------------------------------


 





