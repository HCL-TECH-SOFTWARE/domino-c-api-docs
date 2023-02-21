##### Data Type : Composite Data
##### CDLINKEXPORT2 - Used in creating a document link in a rich text field.
---
```
#include <editods.h>
```
**Description :**

This structure is used to create a document link in a rich text field.  It 
contains all the information necessary to open the specified document from any 
database on any server. 

Use CompoundTextAddDocLink to add a document link to a rich text field.

Notes creates two different types of Doc Links.  The first type consists of a 
CDLINK2 record and a Doc Link Reference.  The second type consists of a 
CDLINKEXPORT2 record.

When a Notes user initially creates a Doc Link from the Notes user interface, 
the first type of Doc Link (CDLINK2) is created. The CDLINK2 record requires 
the Doc Link Reference List ($Links) item in order to resolve the link.

When a Doc Link is exported to the clipboard, Notes converts the CDLINK2 record 
to a CDLINKEXPORT2.  Notes performs this conversion because a CDLINKEXPORT2 
record contains the NOTELINK information that a CDLINK2 structure does not 
have. A CDLINKEXPORT2 will function properly in the context of other documents 
or databases where the original Doc Link Reference List ($Links) item is not 
avaliable.

   The CDLINKEXPORT2 record is then followed by two or three consecutive 
null-terminated strings.  The first string contains the display comment for the 
link, identifying the source database, view, and document title.  The second 
string, called for obscure reasons the "hint", contains the name of the Lotus 
Domino server where the link originated;  this string may be empty, in which 
case the null terminator must be present.  The third string, if present, 
contains the anchor text for the target CDANCHOR record for this link.  If the 
third string is present, the target document is searched for a CDANCHOR record 
with the matching text string.  If a CDANCHOR record with a matching string is 
found, Notes displays the target document beginning at the location of hte 
CDANCHOR record.

**Sample Usage :**
```
STATUS AddDocLink (DBHANDLE hDB, NOTEID IDNote, 
                   ORIGINATORID ViewOID, HANDLE hCompound)

/* AddDocLink  - Demonstrates how to use CompoundTextAddDocLink to
 *               insert a DocLink into a CompoundTextContext
 * Inputs:
 *   hDB       - handle to database that contains the note pointed to by 
 *               the Doc Link
 *   hCompound - handle to a compound text context
 *   IDNote    - ID of the note pointed to by the Doc Link
 *   ViewOID   - OID of view that contains the note pointed to by the 
 *               Doc Link
 *
 * Return:
 *   error status from API calls
 */

{
   STATUS nErr;                    /* return code from API calls */
   NOTEHANDLE hOldNote;
   ORIGINATORID OldNoteOID;        /* OID of note Doc Link points to */
   DBREPLICAINFO DBReplica;        /* DB Replica of DB containing the
                                      note that the Doc Link points to. */
   UNID ViewUNID;                  /* UNID of view containing the
                                      note that the Doc Link points to -
                                      obtained from OID of view note. */
   UNID OldNoteUNID;               /* UNID of note that the Doc Link
                                      points to - obtained from note's 
                                      OID. */
   /* open the note */
   nErr = NSFNoteOpen (hDB, IDNote, 0, &hOldNote);
   if (nErr != NOERROR)
      return (nErr);

   /* Get the OID from the note */
   NSFNoteGetInfo (hOldNote, _NOTE_OID, &OldNoteOID);

   /* Close the note. */
   NSFNoteClose (hOldNote);

   /* Get the Database replica - used for the Doc Link */
   nErr = NSFDbReplicaInfoGet (hDB, &DBReplica);
   if (nErr != NOERROR)
      return (nErr);

   /* Use the View OID and Note OID to fill in the UNID
      structures used in CompoundTextAddDocLink */
   ViewUNID.File = ViewOID.File;
   ViewUNID.Note = ViewOID.Note;

   OldNoteUNID.File = OldNoteOID.File;
   OldNoteUNID.Note = OldNoteOID.Note;

   /* Add the DocLink to the CompoundText context */

   nErr = CompoundTextAddDocLink (
             hCompound,              /* handle to CompoundText context */
             DBReplica.ID,           /* DB Replica ID */
             ViewUNID,
             OldNoteUNID,
             "Doc Link to first Note",  /* comment to appear when DocLink
                                           is selected. */
             0L);                       /* reserved */

   return (nErr);
}
```
**See Also :**
[CompoundTextAddDocLink](/domino-c-api-docs/reference/Func/CompoundTextAddDocLink)
[NOTELINK](/domino-c-api-docs/reference/Data/NOTELINK)
[CDLINK2](/domino-c-api-docs/reference/Data/CDLINK2)
[CDANCHOR](/domino-c-api-docs/reference/Data/CDANCHOR)
---
