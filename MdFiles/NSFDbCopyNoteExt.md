




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




**Initial Release 5.0**



**Function : Database**



**NSFDbCopyNoteExt** **- Copy a
single note from one database to another.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbCopyNoteExt(**  

      DBHANDLE  hSrcDB,  

      DBID far \*SrcDbID,  

      DBID far \*SrcReplicaID,  

      NOTEID  SrcNoteID,  

      DBHANDLE  hDstDB,  

      DBID far \*DstDbID,  

      DBID far \*DstReplicaID,  

      DWORD  dwOpenFlags,  

      DWORD  dwUpdateFlags,  

      NOTEID far \*retDstNoteID,  

      WORD far \*retNoteClass**);**



**Description :**



This
function copies a single note from a source database to the destination
database.  This routine detects if the source and destination databases are
replicas of each other, and sets ID information in reference items in notes
appropriately.  This routine is similar to NSFDbCopyNote, but it also allows
you to specify flags that control the manner in which the source note is opened
and flags which specify how the destination note is updated. This function
allows using extended 32-bit DWORD update options, as described in the entries
OPEN\_xxx and UPDATE\_xxx.


 


**Parameters :**



Input :  

hSrcDB  -  A database handle to the source database.  

  

SrcDbID  -  Not used.  Pass NULL for this parameter.  

  

SrcReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the
source database.  NULL may be used for this pointer.  If you pass in NULL for
this value, SrcReplicaID will be determined by using the hSrcDb.  Pass in a
pointer to the replica ID of the source database, if you happen to already have
the ID, to optimize this call.  

  

SrcNoteID  -  The NOTEID of the source note.  

  

hDstDB  -  A database handle to the destination database.  

  

DstDbID  -  Not used.  Pass NULL for this parameter.  

  

DstReplicaID  -  Optional.  A pointer to the replica ID (also a DBID) of the
destination database.  NULL may be used for this pointer.  

  

dwOpenFlags  -  Flags that control the manner in which the source note is
opened. This, in turn, controls what information about the note is available to
you and how it is structured. The flags are defined in OPEN\_xxx (note) and may
be or'ed together to combine functionality.  

  

dwUpdateFlags  -  Flags that control the manner in which the destination note
is updated. The flags are defined in UPDATE\_xxx and may be or'ed together to
combine functionality.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

NOERROR - Successfully copied note to destination database.  

ERR\_NOTE\_DELETED - Document has been deleted.  

ERR\_xxx - Errors returned by lower level functions.  There are so many possible
causes, that It is best to use the code in a call to OSLoadString and
display/log the error for the user.  

  

  

retDstNoteID  -  Optional.  The address of a NOTEID in which the Note ID of the
newly copied note is returned.  Use NULL if you do not need this returned
information.  If the Note copy is created in a non-replica database, a new
Originator ID (OID) will be generated, so that the copy appears as a unique new
note in the destination database.  

  

retNoteClass  -  Optional.  The address of a WORD in which the NOTE\_CLASS\_xxx of
the copy is returned.  Use NULL if you do not need this returned information.  

  




 **See Also :**


**[NSFDbCopy](NSFDbCopy.md)**


**[NSFDbCopyNote](NSFDbCopyNote.md)**


**[NSFDbIDGet](NSFDbIDGet.md)**


**[OPEN\_xxx (note)](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B660055DC1F)**


**[UPDATE\_xxx](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/85255D56004D3F6385255B4A0056976E)**



----------------------------------------------------------------------------------------------------------


 





