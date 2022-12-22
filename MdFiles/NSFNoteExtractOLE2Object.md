




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



**NSFNoteExtractOLE2Object** **- Create a
copy of an OLE2 object structured storage file, serialized to an On-disk file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfole.h>**



STATUS
LNPUBLIC **NSFNoteExtractOLE2Object(**  

      NOTEHANDLE  hNote,  

      char \*pszObjectName,  

      char \*pszFileName,  

      ENCRYPTION\_KEY \*pEncryptionKey,  

      BOOL  fOverwrite,  

      DWORD  dwFlags**);**



**Description :**



This is the
OLE2 structured storage file that Domino uses to contain a single OLE object. 
The resulting structured storage file contains the "normal" OLE
streams and a single child sub-storage for the OLE object.  The child storage
is named by it's OLE ProgID which is what Domino uses to locate the storage
when loading the object.


 


**Parameters :**



Input :  

hNote  -  Note handle of open note.  

  

pszObjectName  -  Name of the OLE $FILE object which is the "master"
extendable file object ("ext\*\*\*") in the set of $FILE objects that
comprise this OLE object.  

  

pszFileName  -  The file name, including path, into which the Storage file will
be dumped.  

  

pEncryptionKey  -  The Note's bulk data encryption key, acquired from
NSFNoteDecrypt.  

  

fOverwrite  -  TRUE to overwrite the file, if it already exists.  

  

dwFlags  -  Additional flags, unused at this time, must be 0.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_NSF\_NOT\_SUPPORTED - This function is not supported on this platform.  In
Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on Windows
32-bit platforms only.  As of Release 5.0.8, this function is supported on all
Domino and Notes platforms.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  Use
OSLoadString and display/log the error.  

  

  




 **See Also :**


**[NSFNoteAttachOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/70A324C757A4B187852563B1006D80A4)**


**[NSFNoteDeleteOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BA9F71ED059D87E0852563B1006C9522)**



----------------------------------------------------------------------------------------------------------


 





