




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




 


**Function : File Attachment**



**NSFNoteAttachFile** **- Attaches
a disk file to a note.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfnote.h>**



STATUS
LNPUBLIC **NSFNoteAttachFile(**  

      NOTEHANDLE  note\_handle,  

      const char far \*item\_name,  

      WORD  item\_name\_length,  

      const char far \*file\_name,  

      const char far \*orig\_path\_name,  

      WORD  encoding\_type**);**



**Description :**



Attaches a
disk file to a note.  To accomplish this, the function creates an item of
TYPE\_OBJECT, sub-category OBJECT\_FILE, whose ITEM\_xxx flag(s) are set to
ITEM\_SIGN | ITEM\_SEAL.  The item that is built by NSFNoteAttachFile contains
all relevant file information and the compressed file itself.  Since the Item
APIs offer no means of dealing with signed, sealed, or compressed item values,
the File Attachment API NSFNoteDetachFile must be used exclusively to access
these items.


 


**Parameters :**



Input :  

note\_handle  -  Handle of note to which the disk file will be attached.  

  

item\_name  -  Name of item in note into which file is to be placed.  This is
normally set  to ITEM\_NAME\_ATTACHMENT.  

  

item\_name\_length  -  Length of item\_name.  

  

file\_name  -  The address of a null-terminated file name string containing the
fully qualified file path specification for file being attached.  

  

orig\_path\_name  -  The address of a null-terminated string containing a
filename that will be stored internally with the attachment, displayed with the
atttachment icon when the document is viewed in the Notes user interface, and
subsequently used when selecting which attachment to Extract or Detach  and what
path to create for an Extracted file.  Note that these operations may be
carried out  both from the workstation application Attachments dialog box and
programmatically, so try to choose meaningful filenames as opposed to
attach.001, attach002, etc., whenever possible.  If attaching mulitiple files
that have the same filename but different content to a single document, make
sure this variable is unique in each call to NSFNoteAttachFile().  

  

encoding\_type  -  This WORD contains a COMPRESS\_xxx value that specifies the
compression method used to store the file in the note. The compression flag
value may optionally be bitwise OR'd with a HOST\_xxx value to define the type
of file being attached.  In most cases a HOST\_xxx value will not be specified,
and Domino or Notes will set the file type automatically.  See the chapter on
embedding OLE objects in the User Guide for more information on specifying the
HOST\_xxx of a file attachment.  This value also may optionally be bitwise OR'd
with an EFLAGS\_xxx value that specifies filename options.  This value also may
optionally be bitwise OR'd with an NTATT\_xxx value that specifies file types of
a file attachment.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR -  A successful call.   

  

ERR\_xxx - Errors returned by lower level functions.  Use the code in a call to
OSLoadString and display/log the error for the user.  

  

  




 **Sample Usage :**


error =
NSFNoteAttachFile (hMessage,  

    ITEM\_NAME\_ATTACHMENT,     

    strlen(ITEM\_NAME\_ATTACHMENT),   

    filename, pathname, COMPRESS\_HUFF);


 **See Also :**


**[COMPRESS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255BA40007DDB7)**


**[HOST\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/F212A554FF06C86F8525667800610D71)**


**[EFLAGS\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/7905EC4763E452FF8525622700639FE4)**


**[NTATT\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/D6A69CE4E14CA234852562700074AFB1)**


**[NSFNoteExtractFile](NSFNoteExtractFile.md)**


**[NSFNoteExtractFileExt](NSFNoteExtractFileExt.md)**



----------------------------------------------------------------------------------------------------------


 





