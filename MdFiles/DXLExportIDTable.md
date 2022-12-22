




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



**DXLExportIDTable** **- DXL
export ID Table**


**----------------------------------------------------------------------------------------------------------**



**#include <xml.h>**



STATUS
LNPUBLIC **DXLExportIDTable(**  

      DXLEXPORTHANDLE  hDXLExport,  

      XML\_WRITE\_FUNCTION  pDXLWriteFunc,  

      DBHANDLE  hDB,  

      DHANDLE  hIDTable,  

      void far \*pExAction**);**



**Description :**



This DXL
Export function gives the ability to export a set of Notes into XML format. 
The Notes to be exported must be set up in an IDTABLE for exporting since an
argument into this function is an allocated Handle to an IDTABLE.


 


**Parameters :**



Input :  

hDXLExport  -  allocated DXL Export Handle, allocated calling the function
DXLCreateExporter(..)  

  

pDXLWriteFunc  -  The routine which is called once for each block of data to be
exported.  This routine is user defined.  

  

hDB  -  allocated handle to the Domino Database  

  

hIDTable  -  allocated handle to an IDTABLE which contains the Notes to be
exported  

  

pExAction  -  user defined parameter passed to the XML\_WRITE\_FUNCTION.  This
data can be a means for keeping track of information during the export
process.  For example a structure can be defined that can keep track of the
amount of data exported and information on the exported file if the exported
data is to be written to a file.  

  




Output :  

(routine)  -  Return status from this call:   

  

NOERROR - Successfully exported a set of Notes into XML format.  

  

ERR\_xxx - Other errors returned by this function and includes errors returned
by lower level functions. Call OSLoadString to obtain a string to display to
the user.  

  

  




 **Sample Usage :**



        STATUS  error
= NOERROR;


        DBHANDLE       db\_handle;


        FORMULAHANDLE   
formula\_handle;    /\* a compiled selection formula \*/


        WORD   
    wdc;            /\* a word we don't care about \*/


        DHANDLE     
hNoteIDTable;   /\* table of Note IDs to modify \*/


 


        DXLEXPORTHANDLE               hDXLExport;


        DXL\_EXPORT\_PROPERTY    propValue;


        BOOL                          setGetValue;


        


/\* Open the
database. \*/


 


    if
(error = NSFDbOpen (path\_name, &db\_handle))


       
return (ERR(error));


 


        /\* 
Create ID table. Later we will call NSFSearch to find all the


       data
notes. The action routine, AddIDUnique, will add the ID of 


       each
data note to this ID table.


    \*/


 


   if
(error = IDCreateTable(sizeof(NOTEID), &hNoteIDTable))


   {


     
NSFDbClose (db\_handle);


     
return(ERR(error));


   }


 


   /\*
Compile the selection formula. \*/


 


   if
(error = NSFFormulaCompile (


      
NULL,               /\* name of formula (none) \*/


      
0,                  /\* length of name \*/


      
szFormula,            /\* the ASCII formula \*/


      
(WORD) strlen(szFormula),    /\* length of ASCII formula \*/


      
&formula\_handle,    /\* handle to compiled formula \*/


      
&wdc,               /\* compiled formula length (don't care) \*/


      
&wdc,               /\* return code from compile (don't care) \*/


      
&wdc, &wdc, &wdc, &wdc)) /\* compile error info (don't care) \*/


        


      {


        
IDDestroyTable(hNoteIDTable);


        
NSFDbClose (db\_handle);


        
return(ERR(error));


      }


 


   /\* Call
NSFSearch to find the notes that match the selection criteria. 


      For
each note found, the routine AddIdUnique is called. \*/


 


   if
(error = NSFSearch (


      
db\_handle,          /\* database handle \*/


      
formula\_handle,     /\* selection formula \*/


      
NULL,               /\* title of view in selection formula \*/


      
0,                  /\* search flags \*/


      
IDTableInfo->noteClass,    /\* note class to find \*/


      
NULL,               /\* starting date (unused) \*/


      
AddIDUnique,        /\* call for each note found \*/


      
&hNoteIDTable,      /\* argument to AddIDUnique \*/


      
NULL))              /\* returned ending date (unused) \*/


 


   {


     
IDDestroyTable(hNoteIDTable);


     
NSFDbClose (db\_handle);


     
return(ERR(error));


   }


 


   /\* Free
the memory allocated to the compiled formula. \*/


 


  
OSMemFree (formula\_handle);


 


        if(error
= DXLCreateExporter(&hDXLExport))


        {


         
IDDestroyTable(hNoteIDTable);


     
NSFDbClose (db\_handle);


     
return(ERR(error));


        }


        propValue
= eForceNoteFormat;


        setGetValue
= FALSE;


 


        if(error
= DXLSetExporterProperty(hDXLExport, propValue, &setGetValue))


        {


               DXLDeleteExporter(hDXLExport);


               IDDestroyTable(hNoteIDTable);


               NSFDbClose
(db\_handle);


               return(ERR(error));


        }


 


        memset(&IDTableInfo->commonInfo.exportContext,
0, sizeof(IDTableInfo->commonInfo.exportContext));


        if(error
= DXLExportIDTable(hDXLExport, DXLExportStreamFunc, db\_handle, hNoteIDTable,                                                                      (void
far\*)&IDTableInfo->commonInfo.exportContext))


        {


               DXLDeleteExporter(hDXLExport);


               IDDestroyTable(hNoteIDTable);


               NSFDbClose
(db\_handle);


               return(ERR(error));


        }


 


        DXLDeleteExporter(hDXLExport);


   


   /\* Free
the memory containing the ID table \*/


 


  
IDDestroyTable(hNoteIDTable);


 


   /\* Close
the database. \*/


 


  
NSFDbClose (db\_handle) ;


 **See Also :**


**[DBHANDLE](DBHANDLE.md)**


**[DXLEXPORTHANDLE](DXLEXPORTHANDLE.md)**


**[HANDLE](HANDLE.md)**


**[XML\_WRITE\_FUNCTION](XML_WRITE_FUNCTION.md)**



----------------------------------------------------------------------------------------------------------


 





