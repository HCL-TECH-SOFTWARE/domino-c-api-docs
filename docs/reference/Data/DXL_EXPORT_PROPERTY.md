##### Data Type : XML
##### DXL_EXPORT_PROPERTY - DXL export property values
---
```
#include <xml.h>
```

**Definition :**
```
typedef enum
{
	 /* non-boolean export properties */

	eDxlExportResultLog=1, /* MEMHANDLE,    Readonly - the result log from 
the last export. */
	eDefaultDoctypeSYSTEM=2, /* MEMHANDLE,    Readonly - filename of 
dtd/schema keyed to current version of exporter */
	eDoctypeSYSTEM=3,  /* char*(i)/MEMHANDLE(o), What to use for the 
DOCTYPE SYSTEM value (if emitted) */
	    /*        NULL or ""  = DOCTYPE should contain no SYSTEM info */
	    /*        "filename" = filename of dtd or schema used as DOCTYPE 
SYSTEM value */
	eDXLBannerComments=4, /* char*(i)/MEMHANDLE(o), One or more XML 
comments to output at top of the DXL */
	    /*        NULL or "" = no dxl banner comments */
	    /*        "whatever" = zero or more nul-terminated strings capped 
by extra empty string */
	eDxlExportCharset=5,  /* DXL_EXPORT_CHARSET,  Specifies output charset. 
*/
	eDxlRichtextOption=6,  /* DXL_RICHTEXT_OPTION,  Specifies rule for 
exporting richtext. */
	eDxlExportResultLogComment=7, /* char*(i)/MEMHANDLE(o), LMBCS string to 
be added as comment to top of result log */
	eDxlValidationStyle=8,  /* DXL_EXPORT_VALIDATION_STYLE, Specifies style 
of validation info emitted by exporter */
	       /*        Can override other settings, eg - eOutputDOCTYPE */
	eDxlDefaultSchemaLocation=9,  /* MEMHANDLE,    Readonly - default 
xsi:SchemaLocation attribute value for current DXL version */
	eDxlSchemaLocation=10,  /* char*(i)/MEMHANDLE(o), LMBCS value of 
xsi:SchemaLocation attribute put into DXL root element */
	eDxlMimeOption=11,   /* DXL_MIME_OPTION,   Specifies rule for exporting 
native MIME. */
	eAttachmentOmittedText=12, /* char*(i)/MEMHANDLE(o), Text to insert 
within richtext where an attachmentref */
	       /*    was omitted; may contain XML markup but must be valid */
	       /*    DXL richtext content */
	eOLEObjectOmittedText=13, /* char*(i)/MEMHANDLE(o), Text to insert 
within richtext where an objectref */
	       /*       was omitted; may contain XML markup but must be valid */
	       /*       DXL richtext content */
	ePictureOmittedText=14, /* char*(i)/MEMHANDLE(o), Text to insert within 
richtext where a picture */
	    /*       was omitted; may contain XML markup but must be valid */
	    /*       DXL richtext content */
	eOmitItemNames=15,  /* HANDLE of list   List of item names to omit from 
DXL.  Use Listxxx */
	    /*       functions to build list (use fPrefixDataType=FALSE) */
	    /*       (i)API makes a copy of list thus does not adopt HANDLE */
	    /*       (o)API returns copy of list thus caller must free */
	eRestrictToItemNames=16, /* HANDLE of list   List of item names; only 
items with one of these names */
	    /*       will be included in the output DXL.  Use Listxxx */
	    /*       functions to build list (use fPrefixDataType=FALSE) */
	    /*       (i)API makes a copy of list thus does not adopt HANDLE */
	    /*       (o)API returns copy of list thus caller must free */

	 /* boolean properties (gap allows for future definitions of other 
non-boolean export properties) */

	eForceNoteFormat=30,  /* BOOL, TRUE = Export data as notes containing 
items, FALSE = export using a high level of abstraction, */
	eExitOnFirstFatalError=31, /* BOOL, TRUE = Abort on first fatal error, 
FALSE = try to continue to export */
	eOutputRootAttrs=32,  /* BOOL, TRUE = Root needs xmlns, version, and 
other common root attrs */
	eOutputXmlDecl=33,   /* BOOL, TRUE = Emit a leading xml declaration 
statement (<?xml ...?>) */
	eOutputDOCTYPE=34,   /* BOOL, TRUE = Emit a DOCTYPE statement (can be 
overridden by dDxlValidationStyle) */
	eConvertNotesbitmapsToGIF=35, /* BOOL, TRUE = Convert Notesbitmaps 
embedded in richtext to GIFs, FALSE = blob the Notesbitmap CD records */
	eOmitRichtextAttachments=36,/* BOOL, TRUE = omit attachments within 
documents: both the attachmentref */
	    /* within richtext and corresponding items that contain file 
objects */
	eOmitOLEObjects=37,   /* BOOL, TRUE = omit OLE objects within 
documents: both the objectref */
	           /* within richtext and corresponding items that contain file 
objects */
	eOmitMiscFileObjects=38, /* BOOL, TRUE = omit items within documents 
that are not normal attachments */
	    /* (named $FILE) and that contain file objects */
	eOmitPictures=39,  /* BOOL, TRUE = omit pictures that occur directly 
within document richtext and */
	    /* contain gif, jpeg, notesbitmap, or cgm--does not include picture 
within */
	    /* attachmentref or imagemap */
	eUncompressAttachments=40 /* BOOL, TRUE = uncompress attachments */

} DXL_EXPORT_PROPERTY;

```

**Description :**

DXL_EXPORT_PROPERTY default values are set as follows:<br>
 <br>
Note:	(i) = can input new value into the exporter.<br>
 	(o) = can get current value out of exporter.<br>
 	(io) = can do both. <br>
 <br>
 	eDxlExportResultLog		= (o)	NULLMEMHANDLE<br>
	eDefaultDoctypeSYSTEM	= (o)	default filename of dtd keyed to current version of DXL exporter.&quot;<br>
	eDoctypeSYSTEM		= (io)	filename of dtd keyed to current version of DXL exporter.&quot;<br>
 	eDXLBannerComments		= (io)	NULLMEMHANDLE<br>
 	eDxlExportCharset		= (io)	eDxlExportUtf8<br>
 	eDxlRichtextOption		= (io)	eRichtextAsDxl<br>
	eDxlExportResultLogComment	= (io)	NULLMEMHANDLE<br>
 	eForceNoteFormat		= (io)	FALSE<br>
 	eExitOnFirstFatalError		= (io)	TRUE<br>
 	eOutputRootAttrs		= (io)	TRUE<br>
 	eOutputXmlDecl		= (io)	TRUE<br>
 	eOutputDOCTYPE		= (io)	TRUE<br>
	eConvertNotesbitmapToGIF	= (io) 	FALSE<br>
	eDxlValidationStyle		= (io)	eDxlExportValidationStyle_DTD&quot;<br>
	eDxlDefaultSchemaLocation	= (o)	URI's of schema keyed to current version of DLX exporter.&quot;<br>
	eDxlSchemaLocation		= (io)	filename of XML Schema keyed to current version of DXL exporter.&quot;<br>
<br>
<br>
 


**See Also :**
[DXLGetExporterProperty](/domino-c-api-docs/reference/Func/DXLGetExporterProperty)
[DXLSetExporterProperty](/domino-c-api-docs/reference/Func/DXLSetExporterProperty)
[DXL_EXPORT_CHARSET](/domino-c-api-docs/reference/Data/DXL_EXPORT_CHARSET)
[DXL_RICHTEXT_OPTION](/domino-c-api-docs/reference/Data/DXL_RICHTEXT_OPTION)
---
