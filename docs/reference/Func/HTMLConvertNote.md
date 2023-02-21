##### Function : HTML
##### HTMLConvertNote - convert notes to HTML
---
```
#include <htmlapi.h>
STATUS LNPUBLIC HTMLConvertNote(

	HTMLHANDLE  hHTML,
	DBHANDLE  hDB,
	NOTEHANDLE  hNote,
	DWORD  NumArgs,
	HTMLAPI_URLComponent *pArgs);
```
**Description :**

	1) This function is used to convert notes to HTML.  The results of the 
routine is retained in the converter object (until the next "convert") and are 
retrieved with GetText().

	2) Convert the hNote in the database hDB to HTML. Arguments can be 
supplied to that augment and modify the conversion. NumArgs indicates the 
number of arguments, while pArgs is a pointer to an array containing the 
arguments.  Only values from the HTMLAPI_URLComponent.Arg branch are valid.

	3) The type of the note indicated by the NOTEHANDLE determines the web 
engine conversion to be performed, as described in the following table.  Note 
that the equivalent "domino
         url command" is given for reference.  The HTML generated through this 
API is the same as that generated for the respective url command.

	Noteid                                        Conversion

	  0                                Database (OpenDatabase) - usually 
the list of views and folders available in the database.
   DEFAULT note of a given class      Depends on class (NOTE_CLASS_ICON -> 
OpenIcon, etc.)
	Document note                      Convert the contents of the document 
(OpenDocument).  The document's form is used to
                                          create a HTML presentation of the 
document.
       Form note                          Convert form (OpenForm - non-post 
HTML generated)
       Frameset note                      (OpenFrameset)
       Help note                          Convert the help document (OpenHelp)
  Help-about note                   Convert the about document (OpenAbout)
	Icon note                          Convert the database icon (OpenIcon)
  Navigator note                     (OpenNavigator)
  Page note                          Convert the page to HTML (OpenPage)
  View note                          Convert View (OpenView - unexpanded top 
level of view, all entries)
  Other types of notes               Returns error
	
	4) The arguments that are supplied via pArgs are the same as the ones 
available for the url command associated with the note type.  So for example, 
if a view note is provided, the  Start= argument could be provided using 
CmdArgID value CAI_Start.  In that case view contents would start at the given 
spot.


**Parameters :**
Input :
hHTML  -  handle to the converter

hDB  -  Handle to the database which is being converted

hNote  -  handle to the note which is being converted

NumArgs  -  number of arguments being used

pArgs  -  pointer to the arguments being used, please refer to the data structure HTMLAPI_URLComponent

Output :
(routine)  -  NOERROR - Successful.
 ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.



**Sample Usage :**
```
	if(rslt = HTMLCreateConverter(&cvtr))
	{
	 PrintLogInfo("Error in Creating HTMLConverter");
	 *ErrCode =  ERR_CREATE_CONVETOR;
	 return rslt;
	}
	
	if(rslt = HTMLSetHTMLOptions(cvtr, HTMLOption))
	{
	 PrintLogInfo("Error in Setting HTMLOption");
	 *ErrCode =  ERR_SET_HTMLOPT;
	 return rslt;
	}
	
	PrintSeperator();
	PrintLogInfo("Begin to Convert Note");
	
	if(rslt = HTMLConvertNote(cvtr, m_DBHandle, m_NoteHandle, 0, 0))
	{
	 PrintLogInfo("Error in Convertting Note");
	 *ErrCode =  ERR_CONVERT_NOTE;
	 return rslt;
	}
```
**See Also :**
[HTMLAPIReference](/domino-c-api-docs/reference/Data/HTMLAPIReference)
[HTMLConvertElement](/domino-c-api-docs/reference/Func/HTMLConvertElement)
[HTMLConvertImage](/domino-c-api-docs/reference/Func/HTMLConvertImage)
[HTMLConvertItem](/domino-c-api-docs/reference/Func/HTMLConvertItem)
[HTMLConvertNote](/domino-c-api-docs/reference/Func/HTMLConvertNote)
[HTMLCreateConverter](/domino-c-api-docs/reference/Func/HTMLCreateConverter)
[HTMLGetReference](/domino-c-api-docs/reference/Func/HTMLGetReference)
[HTMLGetText](/domino-c-api-docs/reference/Func/HTMLGetText)
---
