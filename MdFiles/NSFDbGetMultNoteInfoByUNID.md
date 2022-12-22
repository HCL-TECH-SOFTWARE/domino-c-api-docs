




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



**NSFDbGetMultNoteInfoByUNID** **- Get
information for a number documents in a database from their UNIDs in a single
call.**


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdb.h>**



STATUS
LNPUBLIC **NSFDbGetMultNoteInfoByUNID(**  

      DBHANDLE  hDB,  

      WORD  Count,  

      WORD  Options,  

      DHANDLE  hInBuf,  

      DWORD \*retSize,  

      DHANDLE \*rethOutBuf**);**



**Description :**



NSFDbGetMultNoteInfoByUNID
may used to get information for a number documents in a database from their
UNIDs in a single call. The caller provides a handle to an array of UNIDs in
CANONICAL form and a count of the number of UNIDs in that array. The caller
also specifies what information they would like returned for each of these
documents. This may include the note id, the sequence time, the sequence number
and the OID. If the OID is requested then requests for the sequence time and
sequence number are ignored as they are included in the OID. A handle is
returned to a buffer with entries for the documents composed of the requested
information in the same order as the UNIDs in the input  array. Each component
of the entry is in canonical form and the order of the information in the
entries is note id, OID, sequence time and sequence number; although the actual
information returned is dependent on the request.


 


For
documents that do not exist in the database the returned data will be zeroed
unless the compress option (fINFO\_COMPRESS) is used with a request for note
ids. In that case a count of the number of consecutive nonexistent documents
always less than 


NOTEID\_MIN
will be returned encoded as a note id. The returned buffer will contain no
other information for those UNIDs.


 


If
the preserve reserved (fINFO\_PRESERVE\_RESERVED) option is requested then
deleted documents will have NOTEID\_RESERVED set in the returned note id.


 


The
number UNIDs passed in must be less than 32767 and the total size of the output
buffer must not exceed 64k.


 


**Parameters :**



Input :  

hDB  -  A handle to an open Domino database.  

  

Count  -  The number of UNIDs in the input array.  

  

Options  -  Specify the infomation to return:  

  

            fINFO\_NOTEID - Return NoteID   

            fINFO\_SEQTIME          - Return SequenceTime from OID   

            fINFO\_SEQNUM           - Return Sequence number from OID   

            fINFO\_OID       - Return OID (disables SeqTime & number &
UNID)  

            fINFO\_COMPRESS      - Compress non-existent UNIDs  

  

hInBuf  -  Handle to the array of UNIDS.  

  




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


**[NSFDbGetMultNoteInfo](NSFDbGetMultNoteInfo.md)**


**[NSFDbGetNoteInfo](NSFDbGetNoteInfo.md)**


**[NSFDbGetNoteInfoByUNID](NSFDbGetNoteInfoByUNID.md)**


**[OID](OID.md)**


**[ORIGINATORID](ORIGINATORID.md)**


**[UNID](UNID.md)**


**[UNIVERSALNOTEID](UNIVERSALNOTEID.md)**



----------------------------------------------------------------------------------------------------------


 





