




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




**Initial Release 8.5.3**



**Function : Database**



**NSFDbGetMultNoteInfo** **- Get
information for a number documents in a database from their note ids in a
single call.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetMultNoteInfo(**  

      DBHANDLE  hDb,  

      WORD  Count,  

      WORD  Options,  

      DHANDLE  hInBuf,  

      DWORD \*retSize,  

      DHANDLE \*rethOutBuf**);**



**Description :**



NSFDbGetMultNoteInfo
may used to get information for a number documents in a database from their
note ids in a single call.The caller provides a handle to an array of note ids
in CANONICAL form and a count of the number of note ids in that array. The 


caller
also specifies what information they would like returned for each of these
documents. This may include the OID, the UNID,  the note modified time, the
note class and the bs flags. A handle is returned to a buffer with entries for
the documents composed


of
the note id  and the requested information in the same order as the note ids in
the input array. Each component of the entry is in canonical form and the order
of the information in the entries is note id, OID, UNID, modified time, note
class and bs flags. although the actual information returned is dependent on
the request.


 


The
returned data will always include the note id, zeroed if the document does not
exist in the database or with NOTEID\_RESERVED set if the document is deleted.


 


**Parameters :**



Input :  

hDb  -  A handle to an open Domino database.  

  

Count  -  The number of note ids in the input array.  

  

Options  -  Specify the infomation to return:  

  

            fINFO\_UNID                             Note's UNID  

            fINFO\_OID                               Note's OID (disables UNID)  

            fINFO\_ALLOW\_HUGE              Allow the returned buffer to exceed
64k.  

  

  

hInBuf  -  Handle to the array of note ids.  

  




Output :  

(routine)  -  Return status from this call -- indicates either success or what
the error is. The return codes include:  

  

            NOERROR - Successfully retrieved the note information.  

  

            ERR\_xxx - Errors returned by lower level functions.  There are so
many possible causes, that It is best to use the code in a call to OSLoadString
and display/log the error for the user.  

  

  

retSize  -  Size of the information in the returned buffer.  

  

rethOutBuf  -  Handle for returned data.  

  




 **See Also :**


**[fINFO\_XXX](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/C056BF434138A17A482579130030CBF3)**


**[NOTEID](NOTEID.md)**


**[NSFDbGetMultNoteInfoByUNID](NSFDbGetMultNoteInfoByUNID.md)**


**[NSFDbGetNoteInfo](NSFDbGetNoteInfo.md)**


**[NSFDbGetNoteInfoByUNID](NSFDbGetNoteInfoByUNID.md)**


**[OID](OID.md)**


**[ORIGINATORID](ORIGINATORID.md)**


**[UNID](UNID.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**



----------------------------------------------------------------------------------------------------------


 





