##### Function : XML
##### DXLExportACL - DXL export ACL
---
```
#include <xml.h>
STATUS LNPUBLIC DXLExportACL(

	DXLEXPORTHANDLE  hDXLExport,
	XML_WRITE_FUNCTION  pDXLWriteFunc,
	DBHANDLE  hDB,
	void far *pExAction);
```
**Description :**

This function exports Domino ACL (Access Control List) data into XML data.

**Parameters :**
Input :
hDXLExport  -  allocated DXL Export Handle, allocated calling the function DXLCreateExporter(..)

pDXLWriteFunc  -  The routine which is called once for each block of data to be exported.  This routine is user defined.

hDB  -  allocated handle to the Domino Database where the ACL resides

pExAction  -  user defined parameter passed to the XML_WRITE_FUNCTION.  This data can be a means for keeping track of information during the export process.  For example a structure can be defined that can keep track of the amount of data exported and information on the exported file if the exported data is to be written to a file.

Output :
(routine)  -  Return status from this call: 

NOERROR - Successfully exported ACL (Access Control List) into XML format.

ERR_xxx - Other errors returned by this function and includes errors returned by lower level functions. Call OSLoadString to obtain a string to display to the user.



**See Also :**
[DBHANDLE](/reference/Data/DBHANDLE)
[DXLEXPORTHANDLE](/reference/Data/DXLEXPORTHANDLE)
[XML_WRITE_FUNCTION](/reference/Data/XML_WRITE_FUNCTION)
---
