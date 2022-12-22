




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




**Initial Release 4.0**



**Function : Composite Data**



**EnumCompositeFile** **- Call
action routine for each Composite Data record in a file.**


**----------------------------------------------------------------------------------------------------------**



**#include <ods.h>**



STATUS
LNPUBLIC **EnumCompositeFile(**  

      char far \*Filename,  

      STATUS LNCALLBACKPTR  ActionRoutine,  

      void far \*vContext**);**



**Description :**



This
function parses a CD file containing an item of type TYPE\_COMPOSITE.  For each
CD record in this item, it calls an action routine specified by the user. 
Since each CD record may have a different header and a different length,
parsing a CD buffer is fairly complex.  Therefore, this function is the
recommended way to access the CD records that constitute a TYPE\_COMPOSITE item.  

  

This function takes, as input, the filename of a CD file, the address of an
Action Routine (the Action Routine is supplied by the user), and the address of
any data (for context) that is to be passed to the Action Routine.  It then
calls the Action Routine once for each CD record in the item, until the entire
item is processed.


 


**Parameters :**



Input :  

Filename  -  Filename of CD file.  

  

ActionRoutine  -  A pointer to an Action Routine.  The following is a template
for the action routine specification:     

  

ActionRoutine(char far \*RecordPtr, WORD RecordType, DWORD RecordLength, void
far \*vContext);  

  

EnumCompositeFile calls the Action Routine with arguments describing each
Composite Data record in the TYPE\_COMPOSITE (Rich Text) item.  

  

The first argument is a (char far \*) pointer to the current Composite Data
record. The second is a SIG\_CD\_xxx signature WORD.  The third argument is the
DWORD length of the object pointed to by the first argument.  The fourth
argument is a pointer to user data.  It is supplied as input to
EnumCompositeFile (fourth argument).  This provides a way to pass context data
to the Action Routine.  

  

vContext  -  A pointer to user data.  This pointer is then passed to the Action
Routine.  It provides a way to pass non-global data to the Action Routine.  

  




Output :  

(routine)  -  Return indicates either success or what the error is. The return codes
include:   

  

NOERROR - Composite Data successfully enumerated.  

ERR\_ODS\_ENUM\_COMPLETE - upon successful enumeration of all Composite Data (CD)
records in the file  

ERR\_DATATYPE - if file does not contain an item of TYPE\_COMPOSITE  

ERR\_xxx - STATUS returned from a lower-level Domino function called in the
action routine and passed back.  

  

  




 **Sample Usage :**


{  

  

/\*  

 \* typedef a pointer to the action routine.  

 \*/  

   

   typedef STATUS (LNCALLBACKPTR ActionRoutine)(char far \*,  

                                                WORD,  

                                                DWORD,  

                                                void far \*);  

   

  

   ActionRoutine Action;  /\* Pointer to action routine for  

                             EnumCompositeFile.           \*/  

   char CDFileName[] = "myfile.cd";  

  

/\*  

 \* Get pointer to the action routine to be invoked by  

 \* EnumCompositeFile.  

 \*/  

  

   Action = (ActionRoutine) MakeProcInstance(FormFields, hInst);  

      

/\*  

 \* For each CD record found in the Body of the Form note,  

 \* EnumCompositeFile will invoke the action routine FormFields.  

 \*/  

  

   sError = EnumCompositeFile( CDFileName,  

                               Action,  

                               pOutputBuffer);  

  

}


 **See Also :**


**[ConvertItemToCompositeExt](ConvertItemToCompositeExt.md)**


**[EnumCompositeBuffer](EnumCompositeBuffer.md)**



----------------------------------------------------------------------------------------------------------


 





