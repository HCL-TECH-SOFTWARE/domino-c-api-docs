##### Function : XML
##### DXLImport - DXL import
---
##### #include <xml.h>
STATUS LNPUBLIC **DXLImport(**

	DXLIMPORTHANDLE  hDXLImport,
	XML_READ_FUNCTION  pDXLReaderFunc,
	DBHANDLE  hDB,
	void far *pImAction);
**Description :**
This function imports XML data into Domino Data based on the 
DXL_IMPORT_PROPERTY options set.
**Parameters :**
Input :
hDXLImport  -  allocated DXL import handle, allocated calling the function DXLCreateImporter(..)

pDXLReaderFunc  -  The routine which is called once for each block of data to be imported.  This routine is user defined.

hDB  -  allocated handle to the Domino database that is to be imported

pImAction  -  user defined parameter passed to the XML_READ_FUNCTION.  This data can be a means for keeping track of information during the import process.  For example a structure can be defined that can keep track of the amount of data imported and information on the import file if the imported data is to be read from a file.


Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully imported XML data into Domino data based on the options set in DXL_IMPORT_PROPERTY.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.


**Sample Usage :**
```
	
	DXLIMPORTHANDLE  hDXLImport;  /* Declare a DXL Import Handle */
	DXL_IMPORT_PROPERTY propValue;  /* Property Value to Set and Get */
	DXLIMPORTOPTION  setGetValue;
	struct ImportContext impCtx;
	BOOL    setGetValueBool;

/* Open the database. */
	
    if (error = NSFDbOpen (path_name, &db_handle))
        return (ERR(error));

   if(error = DXLCreateImporter (&hDXLImport))
	{
	 NSFDbClose(db_handle);
	 return (ERR(error));
	}
	propValue = eDesignImportOption;
	setGetValue = DXLIMPORTOPTION_IGNORE;
	if(error = DXLSetImporterProperty(hDXLImport, propValue, &setGetValue))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}
	
	propValue = eACLImportOption;
	setGetValue = DXLIMPORTOPTION_IGNORE;
	if(error = DXLSetImporterProperty(hDXLImport, propValue, &setGetValue))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}
	
	propValue = eDocumentsImportOption;
	setGetValue = DXLIMPORTOPTION_UPDATE;
	if(error = DXLSetImporterProperty(hDXLImport, propValue, &setGetValue))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}
	
	propValue = eCreateFullTextIndex;
	setGetValueBool = FALSE;

	
	if(error = DXLSetImporterProperty(hDXLImport, propValue, 
&setGetValueBool))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}

	propValue = eReplaceDbProperties;
	setGetValueBool = FALSE;
	if(error = DXLSetImporterProperty(hDXLImport, propValue, 
&setGetValueBool))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}


	/* Initialize our Import Context, this will be keeping track of 
information needed
	 * in the Reader Function.
	 */
	memset(&impCtx, 0, sizeof(impCtx));
	if(error = DXLImport( hDXLImport, DXLReaderFunc, db_handle, (void far 
*)&impCtx ))
	{
	 DXLDeleteImporter(hDXLImport);
	 NSFDbClose(db_handle);
	 return(ERR(error));
	}

    /* Close the database. */

    if (error = NSFDbClose (db_handle))
        return (ERR(error));
	DXLDeleteImporter(hDXLImport);
```
**See Also :**
[DBHANDLE](D:/md_files/DBHANDLE.md)
[DXLIMPORTHANDLE](D:/md_files/DXLIMPORTHANDLE.md)
[XML_READ_FUNCTION](D:/md_files/XML_READ_FUNCTION.md)
---
