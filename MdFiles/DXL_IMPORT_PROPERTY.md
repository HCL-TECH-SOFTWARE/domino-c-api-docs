




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



**DXL\_IMPORT\_PROPERTY** **-** DXL import
property values


**----------------------------------------------------------------------------------------------------------**



**#include
<xml.h>**



**Definition :**



typedef enum


{


        iACLImportOption=1,           
              /\* WORD, Assign to value defined in DXLIMPORTOPTION \*/


        iDesignImportOption=2, 
              /\* WORD, Assign to value defined in DXLIMPORTOPTION \*/


        iDocumentsImportOption=3,     
              /\* WORD, Assign to value defined in DXLIMPORTOPTION \*/


        iCreateFullTextIndex=4,       
              /\* BOOL, TRUE = create full text index, FALSE Do NOT create full
text index \*/


        iReplaceDbProperties=5,       
              /\* BOOL, TRUE = replace database properties, FALSE Do NOT replace
database properties \*/


        iInputValidationOption=6,     
              /\* Xml\_Validation\_Option, Values defined in
Xml\_Validation\_Option, 


                                                     /\*   
...Validate\_Never, ...Validate\_Always, ...Validate\_Auto \*/


        iReplicaRequiredForReplaceOrUpdate=7, /\*
BOOL, TRUE = skip replace/update ops if target DB and import DXL do not have
same                                                                                            /\*
replicaid's \*/


                                               
     /\* ... FALSE = allow replace/update ops even if target DB 


                                               
     /\* and import DXL do not have same replicaid's \*/


        iExitOnFirstFatalError=8,                    /\*
BOOL, TRUE = importer exits on first fatal error, 


                                                     /\*
FALSE = importer continues even if fatal error found \*/


        iUnknownTokenLogOption=9,                     /\*
WORD, Assign to value defined in DXLLOGOPTION. Specifies what to do if DXL
contains an 


                                                     /\*
unknown element or attribute \*/


        iResultLogComment=10,                 /\*
char\*(i)/MEMHANDLE(o)  LMBCS string to be added as comment to top of result log
\*/  


        iResultLog=11,                        /\*
MEMHANDLE, (readonly) The result log from the last import \*/


            iImportedNoteList=12                         /\*
HANDLE, (readonly) An IDTABLE listing the notes imported by the last import
operation \*/"


 


}
DXL\_IMPORT\_PROPERTY;


 


**Description :**



DXL\_IMPORT\_PROPERTY
default values are set as follows:


 


 Note:   (i)
= can input new value into the importer.


            (o)
= can get current value out of importer.


            (io)
= can do both. 


 


            iACLImportOption                                 =
(io) DXLIMPORTOPTION\_IGNORE


            iDesignImportOption                             =
(io) DXLIMPORTOPTION\_IGNORE


            iDocumentsImportOption                       =
(io) DXLIMPOROPTION\_CREATE


            iCreateFullTextIndex                             =
(io) FALSE


 


                        note:     To
create a Full Text Index on a database, the iCreateFullTextIndex must be set to
TRUE,


                                 
         the iReplaceDbProperties must be set to TRUE and a schema element
named <fulltextsettings>


                               
  must be defined.


 


            iReplaceDbProperties                           =
(io) FALSE


            iInputValidationOption                           =
(io) Xml\_Validate\_Auto


            iReplicaRequiredForReplaceOrUpdate   =
(io) TRUE


            iExitOnFirstFatalError                           =
(io) TRUE


            iUnknownTokenLogOption                     =
(io) DXLLOGOPTION\_FATALERROR


            iResultLogComment                              =
(io) NULLMEMHANDLE


            iResultLog                                            =
(o)  NULLMEMHANDLE


            iImportedNoteList                                  =
(o)  NULLHANDLE


 


 **See Also :**


**[DXLGetImporterProperty](DXLGetImporterProperty.md)**


**[DXLIMPORTOPTION](DXLIMPORTOPTION.md)**


**[DXLLOGOPTION](DXLLOGOPTION.md)**


**[DXLSetImporterProperty](DXLSetImporterProperty.md)**


**[Xml\_Validation\_Option](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/B4BEC1AB6DE5693C85256B29005F7317)**



----------------------------------------------------------------------------------------------------------


 





