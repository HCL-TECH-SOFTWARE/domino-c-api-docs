




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




**Initial Release 7.0.2**



**Function : MIME**



**MIMEConvertMIMEPartCC** **- Converts
the input TYPE\_MIME\_PART item in an open note to a TYPE\_COMPOSITE item.**


**----------------------------------------------------------------------------------------------------------**



**#include <mime.h>**



STATUS
LNPUBLIC **MIMEConvertMIMEPartCC(**  

      NOTEHANDLE  hNote,  

      char \*pszItemName,  

      WORD  wItemNameLen,  

      BOOL  bCanonical,  

      CCHANDLE  hCC**);**



**Description :**



This
function converts the input TYPE\_MIME\_PART item in an open note to a
TYPE\_COMPOSITE item.    It does not update the Domino database; to update the
database, call NSFNoteUpdate.


 


You must
specify as input the handle to the open note, a pointer to the item name (an
ASCIIZ string), the length of the item name, a BOOLEAN value indicating if the
note was opened in canonical format (TRUE) or host format (FALSE), and
(optionally) a handle to the Conversion Controls settings.  The Conversion
Controls settings may be changed to override aspects of server-side or
client-side configuration; see MMSet\* and MMGet\* functions below and see also
the description of the CCHANDLE data type and the description of the
MMConvDefaults function.  If the hCC handle is NULL, MIMEConvertMIMEPartCC uses
its internal default settings (same as those set by MMConvDefaults).


 


For the
named TYPE\_MIME\_PART item (which may actually be several items -- e.g.,
'Body'), MIMEConvertMIMEPartCC performs a conversion to Composite Document (CD)
format.


 


(R6.x) Note
that the conversion is not performed with 100% fidelity.  MIMEConvertMIMEPartCC
supports HTML font effects specified as separate elements (e.g., <b> to
set bold face), but it does not support styles, whether specified as a CSS
document, a <style> element, or as a 'style=' parameter to other elements
(e.g., <div> or <span>).  MIMEConvertMIMEPartCC does not fully
support the conversion of multipart/related parts; image placement in the
converted document will not match the original placement in the source
document.  The rendering of tables and lists also may be somewhat different in
the converted document.  MIMEConvertMIMEPartCC also does not convert
"active content"; for example, Javascript contained in an
application/x-javascript part.  Such parts are retained as attachments in the
converted document.


 


(R7.x/R8)
Note that the conversion is not performed with 100% fidelity. 
MIMEConvertMIMEPartCC supports HTML font effects specified as separate elements
(e.g., <b> to set bold face), but it does not support styles, whether
specified as a CSS document, a <style> element, or as a 'style='
parameter to other elements (e.g., <div> or <span>).  The rendering
of tables and lists also may be somewhat different in the converted document. 
MIMEConvertMIMEPartCC also does not convert "active content"; for
example, Javascript contained in an application/x-javascript part.  Such parts
are retained as attachments in the converted document.


 


If
MIMEConvertMIMEPartCC is called on the Domino server, its actions are affected
by its configuration as specified in the Domino Server Configuration; see the
MIME pages of the Server Configuration for details.  If MIMEConvertMIMEPartCC
is called on the Notes client, its actions are affected by its configuration as
specified in the Personal Name and Address book; see the International MIME
Settings document for details.


 


**Parameters :**



Input :  

hNote  -  The handle to the open note to be converted.  

  

pszItemName  -  Pointer to the ASCIIZ item name  

  

wItemNameLen  -  The length of the item name (i.e., number of bytes, not
including the terminating NUL character).  

  

bCanonical  -  A boolean flag that is TRUE if the input note is in canonical
format,  FALSE otherwise.  

  

hCC  -  If non-NULL, the handle to the Conversion Controls settings.  If NULL,
the default settings are used (same as those set by MMConvDefaults).  

  




Output :  

(routine)  -  Return status from this call.  

     NOERROR - Successfully converted the note.  

     ERR\_MISC\_INVALID\_ARGS - Item is not a TYPE\_MIME\_PART item.   

     ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString
to interpret the error status as a string that you may display/log for the
user.  

  

  

  




 **Sample Usage :**


/\* get the notes flags,
determine if the note was opened in canonical format, \*/


   /\*  create the
default conversion control settings and then call MIMEConvertMIMEPartCC \*/


 


WORD wNoteFlags;


BOOL bCanonical;


CCHANDLE hCC =
NULLHANDLE;


STATUS error;


 


NSFNoteGetInfo(hNote,
\_NOTE\_FLAGS, &wNoteFlags);


 


bCanonical =
(wNoteFlags & NOTE\_FLAG\_CANONICAL) != 0;


 


if (error =
MMreateConvControls(&hCC)) {     /\* create the default conversion control
settings \*/


        goto exit;


}


 


MMSetReadReceipt(hCC,
1);             /\* 0 - Do not pass read receipt requests when importing or
exporting (default) \*/


                                      /\*
1 - Support read receipt requests (as Return-Receipt-To when exporting) \*/


                                      /\*
2 - Support read receipt requests (as Disposition-Notification-To when
exporting) \*/


 


if (error = MIMEConvertMIMEPartCC(hNote,
MAIL\_BODY\_ITEM, sizeof(MAIL\_BODY\_ITEM)-1, bCanonical, hCC)) {


        goto exit;


}


 


if (error =
MMDestroyConvControls(hCC)) {    /\* destroy the default conversion control
settings \*/


        goto exit;


}


 


 **See Also :**


**[MIMEConvertMIMEPartsCC](MIMEConvertMIMEPartsCC.md)**


**[TYPE\_xxx](notes:///852584E300582C9D/61FD4E9848264AD28525620B006BA8BD/002100600028002B85255E2D0079321C)**



----------------------------------------------------------------------------------------------------------


 





