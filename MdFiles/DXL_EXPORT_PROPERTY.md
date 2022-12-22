




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Courier;
 panose-1:2 7 4 9 2 2 5 2 4 4;}
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




**Initial Release 6**



**Data Type : XML**



**DXL\_EXPORT\_PROPERTY** **-** DXL export
property values


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


               /\*
non-boolean export properties \*/


 


        eDxlExportResultLog=1, /\*
MEMHANDLE,                         Readonly - the result log from the last
export. \*/


        eDefaultDoctypeSYSTEM=2,      /\*
MEMHANDLE,                         Readonly - filename of dtd/schema keyed to
current version of exporter \*/


        eDoctypeSYSTEM=3,             /\*
char\*(i)/MEMHANDLE(o),     What to use for the DOCTYPE SYSTEM value (if
emitted) \*/


                                      /\*                                                          NULL
or ""     = DOCTYPE should contain no SYSTEM info \*/


                                      /\*                                                          "filename"     =
filename of dtd or schema used as DOCTYPE SYSTEM value \*/


        eDXLBannerComments=4,  /\*
char\*(i)/MEMHANDLE(o),     One or more XML comments to output at top of the DXL
\*/


                                      /\*                                                          NULL
or ""     = no dxl banner comments \*/


                                      /\*                                                          "whatever"     =
zero or more nul-terminated strings capped by extra empty string \*/


        eDxlExportCharset=5,          /\*
DXL\_EXPORT\_CHARSET,        Specifies output charset. \*/


        eDxlRichtextOption=6,         /\*
DXL\_RICHTEXT\_OPTION,               Specifies rule for exporting richtext. \*/


        eDxlExportResultLogComment=7,
/\* char\*(i)/MEMHANDLE(o),     LMBCS string to be added as comment to top of
result log \*/


        eDxlValidationStyle=8,        /\*
DXL\_EXPORT\_VALIDATION\_STYLE,       Specifies style of validation info emitted
by exporter \*/


                                                            /\*                                                           Can
override other settings, eg - eOutputDOCTYPE \*/


        eDxlDefaultSchemaLocation=9, 
/\* MEMHANDLE,                         Readonly - default xsi:SchemaLocation
attribute value for current DXL version \*/


        eDxlSchemaLocation=10,        /\*
char\*(i)/MEMHANDLE(o),     LMBCS value of xsi:SchemaLocation attribute put into
DXL root element \*/


        eDxlMimeOption=11,                    /\*
DXL\_MIME\_OPTION,                   Specifies rule for exporting native MIME. \*/


        eAttachmentOmittedText=12,    /\*
char\*(i)/MEMHANDLE(o),     Text to insert within richtext where an
attachmentref \*/


                                                            /\*                             was
omitted; may contain XML markup but must be valid \*/


                                                            /\*                             DXL
richtext content \*/


        eOLEObjectOmittedText=13,     /\*
char\*(i)/MEMHANDLE(o),     Text to insert within richtext where an objectref \*/


                                                            /\*                                                   was
omitted; may contain XML markup but must be valid \*/


                                                            /\*                                                   DXL
richtext content \*/


        ePictureOmittedText=14,       /\*
char\*(i)/MEMHANDLE(o),     Text to insert within richtext where a picture \*/


                                      /\*                                                   was
omitted; may contain XML markup but must be valid \*/


                                      /\*                                                   DXL
richtext content \*/


        eOmitItemNames=15,            /\*
HANDLE of list                     List of item names to omit from DXL.  Use
Listxxx \*/


                                      /\*                                                   functions
to build list (use fPrefixDataType=FALSE) \*/


                                      /\*                                                   (i)API
makes a copy of list thus does not adopt HANDLE \*/


                                      /\*                                                   (o)API
returns copy of list thus caller must free \*/


        eRestrictToItemNames=16,      /\*
HANDLE of list                     List of item names; only items with one of
these names \*/


                                      /\*                                                   will
be included in the output DXL.  Use Listxxx \*/


                                      /\*                                                   functions
to build list (use fPrefixDataType=FALSE) \*/


                                      /\*                                                   (i)API
makes a copy of list thus does not adopt HANDLE \*/


                                      /\*                                                   (o)API
returns copy of list thus caller must free \*/


 


               /\*
boolean properties (gap allows for future definitions of other non-boolean
export properties) \*/


 


        eForceNoteFormat=30,          /\*
BOOL, TRUE = Export data as notes containing items, FALSE = export using a high
level of abstraction, \*/


        eExitOnFirstFatalError=31,    /\*
BOOL, TRUE = Abort on first fatal error, FALSE = try to continue to export \*/


        eOutputRootAttrs=32,          /\*
BOOL, TRUE = Root needs xmlns, version, and other common root attrs \*/


        eOutputXmlDecl=33,                    /\*
BOOL, TRUE = Emit a leading xml declaration statement (<?xml ...?>) \*/


        eOutputDOCTYPE=34,                    /\*
BOOL, TRUE = Emit a DOCTYPE statement (can be overridden by
dDxlValidationStyle) \*/


        eConvertNotesbitmapsToGIF=35, /\*
BOOL, TRUE = Convert Notesbitmaps embedded in richtext to GIFs, FALSE = blob
the Notesbitmap CD records \*/


        eOmitRichtextAttachments=36,/\*
BOOL, TRUE = omit attachments within documents: both the attachmentref \*/


                                      /\*      within
richtext and corresponding items that contain file objects \*/


        eOmitOLEObjects=37,                   /\*
BOOL, TRUE = omit OLE objects within documents: both the objectref \*/


                                            
/\*      within richtext and corresponding items that contain file objects \*/


        eOmitMiscFileObjects=38,      /\*
BOOL, TRUE = omit items within documents that are not normal attachments \*/


                                      /\*      (named
$FILE) and that contain file objects \*/


        eOmitPictures=39,             /\*
BOOL, TRUE = omit pictures that occur directly within document richtext and \*/


                                      /\*      contain
gif, jpeg, notesbitmap, or cgm--does not include picture within \*/


                                      /\*      attachmentref
or imagemap \*/


        eUncompressAttachments=40     /\*
BOOL, TRUE = uncompress attachments \*/


 


}
DXL\_EXPORT\_PROPERTY;


 


 


**Description :**



DXL\_EXPORT\_PROPERTY
default values are set as follows:


 


Note:    (i)
= can input new value into the exporter.


            (o)
= can get current value out of exporter.


            (io)
= can do both. 


 


            eDxlExportResultLog                =
(o)     NULLMEMHANDLE


            eDefaultDoctypeSYSTEM         =
(o)     default filename of dtd keyed to current version of DXL exporter."  

            eDoctypeSYSTEM                    = (io)    filename of dtd keyed
to current version of DXL exporter."


            eDXLBannerComments             =
(io)    NULLMEMHANDLE


            eDxlExportCharset                    =
(io)    eDxlExportUtf8


            eDxlRichtextOption                   =
(io)    eRichtextAsDxl


            eDxlExportResultLogComment  =
(io)    NULLMEMHANDLE


            eForceNoteFormat                    =
(io)    FALSE


            eExitOnFirstFatalError              =
(io)    TRUE


            eOutputRootAttrs                      =
(io)    TRUE


            eOutputXmlDecl                        =
(io)    TRUE


            eOutputDOCTYPE                    =
(io)    TRUE


            eConvertNotesbitmapToGIF      =
(io)    FALSE


            eDxlValidationStyle                   =
(io)    eDxlExportValidationStyle\_DTD"  

            eDxlDefaultSchemaLocation      = (o)     URI's of schema keyed to
current version of DLX exporter."  

            eDxlSchemaLocation                = (io)    filename of XML Schema
keyed to current version of DXL exporter."


 


 


 


 **See Also :**


**[DXLGetExporterProperty](DXLGetExporterProperty.md)**


**[DXLSetExporterProperty](DXLSetExporterProperty.md)**


**[DXL\_EXPORT\_CHARSET](DXL_EXPORT_CHARSET.md)**


**[DXL\_RICHTEXT\_OPTION](DXL_RICHTEXT_OPTION.md)**



----------------------------------------------------------------------------------------------------------


 





