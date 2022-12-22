




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



**Function : XML**



**DXLExportNote** **- DXL
export Note**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLExportNote(**  

      DXLEXPORTHANDLE  hDXLExport,  

      XML\_WRITE\_FUNCTION  pDXLWriteFunc,  

      NOTEHANDLE  hNote,  

      void far \*pExAction**);**



**Description :**



Export a
single Note into XML format.


 


**Parameters :**



Input :  

hDXLExport  -  allocated DXL Export Handle, allocated calling the function
DXLCreateExporter(..)  

  

pDXLWriteFunc  -  The routine which is called once for each block of data to be
exported.  This routine is user defined.  

  

hNote  -  allocated Note Handle   

  

pExAction  -  user defined parameter passed to the XML\_WRITE\_FUNCTION.  This
data can be a means for keeping track of information during the export
process.  For example a structure can be defined that can keep track of the
amount of data exported and information on the exported file if the exported
data is to be written to a file.  

  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully exported the Note into XML format.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **Sample Usage :**


    STATUS         error
= NOERROR;


        DBHANDLE       db\_handle;


        NOTEHANDLE     noteHandle;


 


        DXLEXPORTHANDLE                       hDXLExport;


        DXL\_EXPORT\_PROPERTY           propValue;


        BOOL                                  setGetValue;


        


 


        char      
pname[MAXPATH] = "";         /\* buffer to store the input path to
database \*/


        char      
\*path\_name;                  /\* pathname of database \*/


 


        path\_name
= NoteInfo->commonInfo.databaseName;


        if
(strcmp(NoteInfo->commonInfo.serverName, ""))


         {


           
if (error = OSPathNetConstruct( NULL, NoteInfo->commonInfo.serverName,
NoteInfo->commonInfo.databaseName, pname))


           
{


              
return (ERR(error));


           
}


            path\_name
= pname;


         }


 


        /\*
Open the database. \*/


 


    if
(error = NSFDbOpen (path\_name, &db\_handle))


       
return (ERR(error));


 


        /\*
Open this Note to get access to the noteHandle \*/


        if(error
= NSFNoteOpen(db\_handle, NoteInfo->expNote, 0, &noteHandle))


        {


               NSFDbClose(db\_handle);


               return
(ERR(error));


        }


 


        /\*
Export this note \*/


        if(
error = DXLCreateExporter (&hDXLExport))


        {


               NSFNoteClose(noteHandle);


               NSFDbClose(db\_handle);


               return
(ERR(error));


        }


 


        propValue
= eForceNoteFormat;


        setGetValue
= FALSE;


 


        if(error
= DXLSetExporterProperty(hDXLExport, propValue, &setGetValue))


        {


               DXLDeleteExporter(hDXLExport);


               NSFNoteClose(noteHandle);


               return(ERR(error));


        }


 


        memset(&NoteInfo->commonInfo.exportContext,
0, sizeof(NoteInfo->commonInfo.exportContext));


               


        if(error
= DXLExportNote(hDXLExport, DXLExportStreamFunc, noteHandle, 


                                                            (void
far \*)&NoteInfo->commonInfo.exportContext))


        {


               DXLDeleteExporter(hDXLExport);


               NSFNoteClose(noteHandle);


               NSFDbClose(db\_handle);


               return(ERR(error));


        }


 


        DXLDeleteExporter(hDXLExport);


 


        /\*
Close the note. \*/


    if
(error = NSFNoteClose (noteHandle))


        {


               NSFDbClose(db\_handle);


       
return (ERR(error));


        }


        /\*
Close the database \*/


        if(error
= NSFDbClose(db\_handle))


               return
(ERR(error));


 **See Also :**


**[DXLEXPORTHANDLE](DXLEXPORTHANDLE.md)**


**[NOTEHANDLE](NOTEHANDLE.md)**


**[XML\_WRITE\_FUNCTION](XML_WRITE_FUNCTION.md)**



----------------------------------------------------------------------------------------------------------


 





