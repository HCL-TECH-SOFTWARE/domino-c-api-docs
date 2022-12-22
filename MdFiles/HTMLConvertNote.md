




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




**Initial Release 7.0.2**



**Function : HTML**



**HTMLConvertNote** **- convert
notes to HTML**


**----------------------------------------------------------------------------------------------------------**



**#include <htmlapi.h>**



STATUS
LNPUBLIC **HTMLConvertNote(**  

      HTMLHANDLE  hHTML,  

      DBHANDLE  hDB,  

      NOTEHANDLE  hNote,  

      DWORD  NumArgs,  

      HTMLAPI\_URLComponent \*pArgs**);**



**Description :**




      1)
This function is used to convert notes to HTML.  The results of the routine is
retained in the converter object (until the next "convert") and are
retrieved with GetText().


 


      2)
Convert the hNote in the database hDB to HTML. Arguments can be supplied to
that augment and modify the conversion. NumArgs indicates the number of
arguments, while pArgs is a pointer to an array containing the arguments.  Only
values from the HTMLAPI\_URLComponent.Arg branch are valid.


 


      3) The
type of the note indicated by the NOTEHANDLE determines the web engine
conversion to be performed, as described in the following table.  Note that the
equivalent "domino


        
url command" is given for reference.  The HTML generated through this API
is the same as that generated for the respective url command.


 


            Noteid                                       
Conversion


 


             
0                                Database (OpenDatabase) - usually the list of
views and folders available in the database.


 
         DEFAULT note of a given class      Depends on class (NOTE\_CLASS\_ICON
-> OpenIcon, etc.)


            Document
note                      Convert the contents of the document (OpenDocument). 
The document's form is used to  

                                          create a HTML presentation of the
document.


      
Form note                          Convert form (OpenForm - non-post HTML
generated)


      
Frameset note                      (OpenFrameset)


      
Help note                          Convert the help document (OpenHelp)


            Help-about
note                             Convert the about document (OpenAbout)


            Icon
note                          Convert the database icon (OpenIcon)


            Navigator
note                     (OpenNavigator)


            Page
note                          Convert the page to HTML (OpenPage)


            View
note                          Convert View (OpenView - unexpanded top level of
view, all entries)


            Other
types of notes               Returns error


            


            4)
The arguments that are supplied via pArgs are the same as the ones available
for the url command associated with the note type.  So for example, if a view
note is provided, the       Start= argument could be provided using CmdArgID
value CAI\_Start.  In that case view contents would start at the given spot.


 


 


**Parameters :**



Input :  

hHTML  -  handle to the converter  

  

hDB  -  Handle to the database which is being converted  

  

hNote  -  handle to the note which is being converted  

  

NumArgs  -  number of arguments being used  

  

pArgs  -  pointer to the arguments being used, please refer to the data
structure HTMLAPI\_URLComponent  

  




Output :  

(routine)  -  NOERROR - Successful.  

 ERR\_xxx - Errors returned by lower level functions.  Call to OSLoadString to
interpret the error status as a string that you may display/log for the user.  

  

  




 **Sample Usage :**



        if(rslt
= HTMLCreateConverter(&cvtr))


        {


               PrintLogInfo("Error
in Creating HTMLConverter");


               \*ErrCode
=  ERR\_CREATE\_CONVETOR;


               return
rslt;


        }


        


        if(rslt
= HTMLSetHTMLOptions(cvtr, HTMLOption))


        {


               PrintLogInfo("Error
in Setting HTMLOption");


               \*ErrCode
=  ERR\_SET\_HTMLOPT;


               return
rslt;


        }


        


        PrintSeperator();


        PrintLogInfo("Begin
to Convert Note");


        


        if(rslt
= HTMLConvertNote(cvtr, m\_DBHandle, m\_NoteHandle, 0, 0))


        {


               PrintLogInfo("Error
in Convertting Note");


               \*ErrCode
=  ERR\_CONVERT\_NOTE;


               return
rslt;


        }


 **See Also :**


**[HTMLAPIReference](HTMLAPIReference.md)**


**[HTMLConvertElement](HTMLConvertElement.md)**


**[HTMLConvertImage](HTMLConvertImage.md)**


**[HTMLConvertItem](HTMLConvertItem.md)**


**[HTMLConvertNote](HTMLConvertNote.md)**


**[HTMLCreateConverter](HTMLCreateConverter.md)**


**[HTMLGetReference](HTMLGetReference.md)**


**[HTMLGetText](HTMLGetText.md)**



----------------------------------------------------------------------------------------------------------


 





