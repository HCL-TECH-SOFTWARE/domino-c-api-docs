##### Function : MIME
##### MIMEEMLExport3 - Exports the MIME content (e-mail messages) of given noteid into the eml file.
---
##### #include <mime.h>
STATUS **MIMEEMLExport3(**

	char*dbName,
	NOTEID  NoteID,
	const char*pFileName,
	BOOL  bOverWrite);
**Description :**
This routine is called to export the contents of a given NOTEID to an EML file. 
It reads the content of the mail from the given database, which is passed as an 
argument to this routine and converts the MIME mail message into EML(Electronic 
Mail) format. Standard EML file name is "<fileName>.eml".
**Parameters :**
Input :
dbName  -  Database Name on which MIME mail exists.

NoteID  -  Message ID in the DB for processing. 

pFileName  -  Name of the EML file. 

bOverWrite  -   Boolean flag TRUE that given file can be over written other wise not.

Output :
(routine)  -  NOERROR on successful conversion. ERR_EXISTS - If bOverWrite is false and file exists. ERR_FILE_INVALID - File extension is not "eml". ERR_MISC_INVALID_ARGS - Invalid Args error msg. Notes Error on failure.  


**Sample Usage :**
```
char EMLFileName[MAXPATH]="sample.eml";
char dbName[MAXPATH]="DominoServer/HCL";
 NOTEID noteID = {0}; 
NOTEHANDLE hNote ; //This is open note handle from open DB 
NSFNoteGetInfo(hNote, _NOTE_ID, &noteID);
 STATUS error = MIMEEMLExport3(dbName, NoteID, EMLFileName, TRUE);
if (error)
return error;

```
**See Also :**
[](D:/md_files/.md)
---
