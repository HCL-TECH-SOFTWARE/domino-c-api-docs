




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



**NSFNoteAttachOLE2Object** **- Attach an
OLE structured storage object to the specified Note, creating the OLE $FILE
objects using the specified storage file.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfole.h>**



STATUS
LNPUBLIC **NSFNoteAttachOLE2Object(**  

      NOTEHANDLE  hNote,  

      char \*pszFileName,  

      char \*pszObjectName,  

      BOOL  fCreateInfoItem,  

      char \*pszObjDescription,  

      char \*pszFieldName,  

      OLE\_GUID \*pOleObjClassID,  

      WORD  wDisplayFormat,  

      BOOL  fScripted,  

      BOOL  fOleControl,  

      DWORD  dwFlags**);**



**Description :**



Attach an
OLE structured storage object to the specified Note, creating the OLE $FILE
objects using the specified storage file.  Also, optionally create an
$OLEOBJINFO note item using the specified parameters.


 


**Parameters :**



Input :  

hNote  -  NSF Note Handle to open note  

  

pszFileName  -  Input file name containing the OLE structured storage file  

  

pszObjectName  -  The name of the NSF $FILE extendable file object to create.
This MUST match the one created in the CDOLEBEGIN record in the body of the
document.  

  

fCreateInfoItem  -  TRUE to create a $OLEOBJINFO item.  The remaining
parameters are propogated to the OLEOBJINFO item.  

  

pszObjDescription  -  Object user description, i.e. "My Worksheet"  

  

pszFieldName  -  Field name in which the OLE object resides within the
document.  

  

pOleObjClassID  -  The OLE object's GUID  

  

wDisplayFormat  -  Visual rendering format, like bitmap, metafile, 
DDEFORMAT\_xxx from editods.h  

  

fScripted  -  True if object is scripted (for ActiveX).  If this is true, it's
up to the caller to attach the associated Lotus script source and object code
to this note, using the following naming convention <xxxx>.lso for the
Lotus Script compiled object code and <xxxx>.lss for the LotusScript
source, where "xxxx" is identical to the the ObjectName used above. 
If Object name is "foo" then "foo.lss" has the lotus script
source, and "foo.lso" has the lotus script object code.  

  

fOleControl  -  True if this object is registered an OLE ActiveX  

  

dwFlags  -  see OLE\_xxxISTORAGE\_SUPPORTED  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return
codes include:   

  

NOERROR - Operation was successful.  

  

ERR\_NSF\_NOT\_SUPPORTED - This function is not supported on this platform.  In
Release 5.0 through 5.0.7 of Domino and Notes, this function was supported on
Windows 32-bit platforms only.  As of Release 5.0.8, this function is supported
on all Domino and Notes platforms.  

  

ERR\_xxx - STATUS returned from a lower level Notes function call.  Use OSLoadString
and display/log the error.  

  

  




 **See Also :**


**[NSFNoteDeleteOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/BA9F71ED059D87E0852563B1006C9522)**


**[NSFNoteExtractOLE2Object](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/1C15F3B7BC6C9E11852563B1006BD694)**


**[OLE\_xxxISTORAGE\_SUPPORTED](OLE_xxxISTORAGE_SUPPORTED.md)**



----------------------------------------------------------------------------------------------------------


 





