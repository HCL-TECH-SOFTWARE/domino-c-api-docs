##### Function : XML
##### DXLExportNote - DXL export Note
---
```
#include <xml.h>
STATUS LNPUBLIC DXLExportNote(

	DXLEXPORTHANDLE  hDXLExport,
	XML_WRITE_FUNCTION  pDXLWriteFunc,
	NOTEHANDLE  hNote,
	void far *pExAction);
```
**Description :**

Export a single Note into XML format.

**Parameters :**
Input :
hDXLExport  -  allocated DXL Export Handle, allocated calling the function DXLCreateExporter(..)

pDXLWriteFunc  -  The routine which is called once for each block of data to be exported.  This routine is user defined.

hNote  -  allocated Note Handle 

pExAction  -  user defined parameter passed to the XML_WRITE_FUNCTION.  This data can be a means for keeping track of information during the export process.  For example a structure can be defined that can keep track of the amount of data exported and information on the exported file if the exported data is to be written to a file.


Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully exported the Note into XML format.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**Sample Usage :**
```
	STATUS  error = NOERROR;
	DBHANDLE db_handle;
	NOTEHANDLE noteHandle;

	DXLEXPORTHANDLE   hDXLExport;
	DXL_EXPORT_PROPERTY  propValue;
	BOOL     setGetValue;
	

	char       pname[MAXPATH] = "";         /* buffer to store the input 
path to database */
	char       *path_name;                  /* pathname of database */

	path_name = NoteInfo->commonInfo.databaseName;
	if (strcmp(NoteInfo->commonInfo.serverName, ""))
         {
            if (error = OSPathNetConstruct( NULL, 
NoteInfo->commonInfo.serverName, NoteInfo->commonInfo.databaseName, pname))
            {
               return (ERR(error));
            }
            path_name = pname;
         }

	/* Open the database. */

    if (error = NSFDbOpen (path_name, &db_handle))
        return (ERR(error));

	/* Open this Note to get access to the noteHandle */
	if(error = NSFNoteOpen(db_handle, NoteInfo->expNote, 0, &noteHandle))
	{
	 NSFDbClose(db_handle);
	 return (ERR(error));
	}

	/* Export this note */
	if( error = DXLCreateExporter (&hDXLExport))
	{
	 NSFNoteClose(noteHandle);
	 NSFDbClose(db_handle);
	 return (ERR(error));
	}

	propValue = eForceNoteFormat;
	setGetValue = FALSE;

	if(error = DXLSetExporterProperty(hDXLExport, propValue, &setGetValue))
	{
	 DXLDeleteExporter(hDXLExport);
	 NSFNoteClose(noteHandle);
	 return(ERR(error));
	}

	memset(&NoteInfo->commonInfo.exportContext, 0, 
sizeof(NoteInfo->commonInfo.exportContext));
	 
	if(error = DXLExportNote(hDXLExport, DXLExportStreamFunc, noteHandle, 
	       (void far *)&NoteInfo->commonInfo.exportContext))
	{
	 DXLDeleteExporter(hDXLExport);
	 NSFNoteClose(noteHandle);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}

	DXLDeleteExporter(hDXLExport);

	/* Close the note. */
    if (error = NSFNoteClose (noteHandle))
	{
	 NSFDbClose(db_handle);
        return (ERR(error));
	}
	/* Close the database */
	if(error = NSFDbClose(db_handle))
	 return (ERR(error));
```
**See Also :**
[DXLEXPORTHANDLE](/reference/Data/DXLEXPORTHANDLE)
[NOTEHANDLE](/reference/Data/NOTEHANDLE)
[XML_WRITE_FUNCTION](/reference/Data/XML_WRITE_FUNCTION)
---
