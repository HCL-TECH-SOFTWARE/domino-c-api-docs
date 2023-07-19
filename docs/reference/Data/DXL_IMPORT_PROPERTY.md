##### Data Type : XML
##### DXL_IMPORT_PROPERTY - DXL import property values
---
```
#include <xml.h>
```

**Definition :**

typedef enum
{
	iACLImportOption=1,     /* WORD, Assign to value defined in 
DXLIMPORTOPTION */
	iDesignImportOption=2,    /* WORD, Assign to value defined in 
DXLIMPORTOPTION */
	iDocumentsImportOption=3,    /* WORD, Assign to value defined in 
DXLIMPORTOPTION */
	iCreateFullTextIndex=4,    /* BOOL, TRUE = create full text index, 
FALSE Do NOT create full text index */
	iReplaceDbProperties=5,    /* BOOL, TRUE = replace database properties, 
FALSE Do NOT replace database properties */
	iInputValidationOption=6,    /* Xml_Validation_Option, Values defined 
in Xml_Validation_Option, 
	       /*    ...Validate_Never, ...Validate_Always, ...Validate_Auto */
	iReplicaRequiredForReplaceOrUpdate=7, /* BOOL, TRUE = skip 
replace/update ops if target DB and import DXL do not have same                
/* replicaid's */
	         /* ... FALSE = allow replace/update ops even if target DB 
	         /* and import DXL do not have same replicaid's */
	iExitOnFirstFatalError=8,   /* BOOL, TRUE = importer exits on first 
fatal error, 
	      /* FALSE = importer continues even if fatal error found */
	iUnknownTokenLogOption=9,   /* WORD, Assign to value defined in 
DXLLOGOPTION. Specifies what to do if DXL contains an 
	      /* unknown element or attribute */
	iResultLogComment=10,   /* char*(i)/MEMHANDLE(o)  LMBCS string to be 
added as comment to top of result log */  
	iResultLog=11,    /* MEMHANDLE, (readonly) The result log from the last 
import */
	iImportedNoteList=12    /* HANDLE, (readonly) An IDTABLE listing the 
notes imported by the last import operation */"

} DXL_IMPORT_PROPERTY;

**Description :**

DXL_IMPORT_PROPERTY default values are set as follows:<br>
 <br>
 Note:	(i) = can input new value into the importer.<br>
 	(o) = can get current value out of importer.<br>
 	(io) = can do both. <br>
 <br>
 	iACLImportOption			= (io) DXLIMPORTOPTION_IGNORE<br>
 	iDesignImportOption			= (io) DXLIMPORTOPTION_IGNORE<br>
 	iDocumentsImportOption		= (io) DXLIMPOROPTION_CREATE<br>
 	iCreateFullTextIndex			= (io) FALSE<br>
<br>
		note:	To create a Full Text Index on a database, the iCreateFullTextIndex must be set to TRUE,<br>
		          	the iReplaceDbProperties must be set to TRUE and a schema element named &lt;fulltextsettings&gt;<br>
		        	 must be defined.<br>
<br>
 	iReplaceDbProperties			= (io) FALSE<br>
 	iInputValidationOption			= (io) Xml_Validate_Auto<br>
 	iReplicaRequiredForReplaceOrUpdate	= (io) TRUE<br>
 	iExitOnFirstFatalError			= (io) TRUE<br>
 	iUnknownTokenLogOption		= (io) DXLLOGOPTION_FATALERROR<br>
 	iResultLogComment			= (io) NULLMEMHANDLE<br>
 	iResultLog				= (o)  NULLMEMHANDLE<br>
	iImportedNoteList			= (o)  NULLHANDLE


**See Also :**
[DXLGetImporterProperty](/domino-c-api-docs/reference/Func/DXLGetImporterProperty)
[DXLIMPORTOPTION](/domino-c-api-docs/reference/Data/DXLIMPORTOPTION)
[DXLLOGOPTION](/domino-c-api-docs/reference/Data/DXLLOGOPTION)
[DXLSetImporterProperty](/domino-c-api-docs/reference/Func/DXLSetImporterProperty)
[Xml_Validation_Option](/domino-c-api-docs/reference/Data/Xml_Validation_Option)
---
