##### Chapter 12-1
##### Import and Export Libraries

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This document explains how to use the HCL C API for Domino and Notes to create custom import/export libraries and how to install custom libraries in the Notes user interface.<br>
<br>
On Windows 32-bit platforms, Notes let you import and export data from and to a variety of non-Domino file formats, including 1-2-3, Ami Pro, and others. For each supported file format, Notes provide executable program libraries that convert between that<font color="#FF0000"> </font>format and Domino format.  If Notes does not support the file format you require, you can use the API to create a custom import or export library for your format.<br>
<br>
<br>
<b><font size="5" color="#000080">Edit-Level versus View-Level</font></b><br>
<br>
From the Notes user interface, there are two levels at which you may import and export data, Edit-Level and View-Level. Since you can import or export at either level, four types of import/export libraries are defined.<br>
<br>
<b><font color="#000080">Edit-Level Import Libraries</font></b><br>
<br>
An Edit-Level Import Library imports one or more files into the rich text field of a single Domino document. To perform an edit-level import from the Notes user interface, you must put the focus on an open document, the document must be open in edit mode, and the cursor must be positioned in a rich text field. <br>
<br>
<b><font color="#000080">Edit-Level Export Libraries</font></b><br>
<br>
An Edit-Level Export Library exports a single complete Domino document to a single external file. To perform an edit-level export from the Notes user interface, you must put the focus on an open Domino document, either by opening an existing Domino document or composing a new one. The external file you create displays all the fields of the exported Domino document as rendered by the form, including static text.<br>
<br>
<b><font color="#000080">View-Level Import Libraries</font></b><br>
<br>
A View-Level Import Library imports one or more non-Domino documents into a Domino database. A single view-level import operation can create any number of new Domino documents in the database. To perform a view-level import from the Notes user interface, the focus must be on a view window. At the view level, you can only import files whose format supports multiple records, such as 1-2-3 or Structured Text files.<br>
<br>
<b><font color="#000080">View-Level Export Libraries</font></b><br>
<br>
A View-Level Export Library exports one or more Domino documents into a non-Domino file. A single view-level export can store the data from many Domino documents in a single external file. To perform a view-level export from the Notes user interface, you must put the focus on an open view of a database. You may select one or more documents in the view before you issue the File - Export command. The resulting external file receives the data from all the selected Domino documents in the view.<br>
<br>
<br>
<b><font size="5" color="#000080">The Main Entry Point</font></b><br>
<br>
All import/export libraries consist of executable program libraries. When a user imports or exports data, Notes loads the appropriate library and calls the main entry point provided by the library.<br>
<br>
Every import/export library must provide a function to serve as the main entry point. This function must conform to the syntax shown in the next section. Notes calls this function after the user chooses the file or files to act on and the format of the files.<br>
<br>
The syntax of the main entry point function is defined by IXENTRYPROC. See the typedef in the C API header file ixport.h. Under Windows, this function may have any name, but must be the first function exported by the library, as defined in the module definition file.<br>
<br>
<br>
<b><font size="5" color="#000080">Edit-Level Import Libraries</font></b><br>
<br>
The main entry point for an edit-level import library must conform to the syntax shown below.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>MainEntryPoint for Edit-Level Import Libraries</b></ul>
</td></tr>
</table>
<tt><font size="2">STATUS LNPUBLIC &nbsp;MainEntryPoint(EDITIMPORTDATA *EditorData,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; WORD Flags,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;HMODULE hModule,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char *AltLibraryName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char *FileName)</font></tt><br>
<br>
<br>
The main function of an edit-level import library must open and read the external file selected by the user and convert this data to Domino rich text format. The library must store this rich text data in a temporary disk file, whose name is specified by Notes. Once the entry point function returns NOERROR, Notes reads the temporary file, inserts the data into the rich text field being edited by the user, and deletes the temporary file.<br>
<br>
Notes specifies the name of the temporary file in the OutputFileName member of the EDITIMPORTDATA structure. This data structure also provides the FONTID of text at the caret position in the rich text field. <br>
<br>
The FileName parameter provides the fully expanded path name of the file to import.<br>
<br>
If the user selects more than one file to import in the File Import dialog box, Notes calls the main entry point function once for each input file. The Flags parameter tells this function whether it is processing the first or last input file. The function should create the temporary file only if it is processing the first input file. Otherwise, the temporary file already exists, so the function should open the temporary file and append new data.<br>
<br>
<br>
<b><font size="5" color="#000080">Edit-Level Export Libraries</font></b><br>
<br>
The main entry point for an edit-level export library must conform to the syntax shown below.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>MainEntryPoint for Edit-Level Export Libraries</b></ul>
</td></tr>
</table>
<tt><font size="2">STATUS LNPUBLIC &nbsp;MainEntryPoint(EDITEXPORTDATA *EditorData,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; WORD Flags,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;HMODULE hModule,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char *AltLibraryName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char *FileName)</font></tt><br>
<br>
The main entry point function of an edit-level export library must convert data from Domino rich text format to the format supported by the library and write this data to the external file specified. The Domino rich text data resides in the temporary file provided by Notes. Notes specifies the name of this temporary file in the InputFileName member of the EDITEXPORTDATA structure. <br>
<br>
The sample program XEDIT, is an edit-level export library.  Its source code is in the directory \samples\client\xedit.<br>
<br>
The main routine of xedit.c is ExpAsciiText which queries the user  at<b><font color="#FF0000"> </font></b>the start of the export<b><font color="#FF0000"> </font></b>process for instructions on how to handle line delimiters, how many characters are on a line, and whether to remove tabs.<br>
<br>
XEDIT displays debugging messages on the Notes title bar when conversion begins and when it is writing<b><font color="#FF0000"> </font></b>the export file.<br>
<br>
XEDIT uses ConvertItemToText to convert the data in the temporary file provided by Notes from rich text format to character text. In preparation, XEDIT calls OSMemAlloc to get a block of memory that it can pass as input to ConvertItemToText. It locks the memory to get a pointer and reads the composite data from the temporary file into the memory. Since the memory is locked, XEDIT must unlock<b><font color="#FF0000"> </font></b>it before calling ConvertItemToText.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>xedit.c: Converting Composite to Text</b></ul>
</td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; /* Convert the Object associated with the BID to a plain text &nbsp;<br>
 &nbsp; &nbsp; &nbsp; buffer. ConvertItemToText throws away CD Records that don't <br>
 &nbsp; &nbsp; &nbsp; map to text: Document Links, DDE Links, Graphics, and so on.<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (Error_Status = ConvertItemToText (<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; bidTmpCD,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TmpCDLen,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; LineDelimiter,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; CharsPerLine,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;hExpBuffer,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;ExpBufferLength,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fStripTabs))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto Exit;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;CleanUp_State += FREE_EXPBUFFER; &nbsp;/* Flag our progress so far. */</font></tt><br>
<br>
In this use of ConvertItemToText, hExpBuffer gets the handle of the created text buffer. Note the user-supplied arguments for line delimiter, characters per line, and a boolean indicating whether to strip tabs. Before the .DLL returns it must free the exported buffer.<br>
<br>
<br>
<b><font size="5" color="#000080">View-Level Import Libraries</font></b><br>
<br>
The main entry point for a view-level import library must conform to the syntax shown below.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>MainEntryPoint for View-Level Import Libraries</b></ul>
</td></tr>
</table>
<tt><font size="2">STATUS LNPUBLIC &nbsp;MainEntryPoint(VIEWIXDATA *ViewData,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; WORD &nbsp; &nbsp;Flags,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;HMODULE hModule,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; char &nbsp; &nbsp;*AltLibraryName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char &nbsp; &nbsp;*FileName)</font></tt><br>
<br>
The main function of a view level import library must read the external data file specified by the FileName input argument and parse this file into individual records. It must create a new Domino document for each record in the input file, convert the data values from the external file to Domino format, and add data items to the new Domino documents.  <br>
<br>
Notes initializes the VIEWIXDATA structure with all the information the library needs to<b><font color="#FF0000"> </font></b>create new documents in the database.<br>
<br>
 <br>
<b><font size="5" color="#000080">View-Level Export Libraries</font></b><br>
<br>
The main entry point for a view-level export library must conform to the syntax shown below.
<table width="100%" border="1">
<tr valign="top"><td width="100%">
<ul><b>MainEntryPoint for View-Level Export Libraries</b></ul>
</td></tr>
</table>
<tt><font size="2">STATUS LNPUBLIC &nbsp;MainEntryPoint(VIEWIXDATA *ViewData,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD &nbsp; &nbsp;Flags,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;HMODULE hModule,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char &nbsp; &nbsp;*AltLibraryName,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char &nbsp; &nbsp;*FileName)</font></tt><br>
<br>
<br>
The main function of a view-level export library must convert data from documents in the view and write that data to the specified output file in the appropriate format. Notes initializes the VIEWIXDATA structure with extensive information about the database and view from which the user is exporting. Notes provides this VIEWIXDATA structure as input to the main entry point function, together with the name of the output file to which the library should write.<br>
<br>
The VIEWIXDATA structure contains all the information the library needs to access the documents in the view opened by the user, including a Note ID table of all the user-selected notes in the view and the Note ID of the current position in the view. A view-level export library may use the hSelectedList member of the VIEWIXDATA data structure to export only the currently selected notes in the view.<br>
<br>
<br>
<b><font size="5" color="#000080">The Import/Export Variables in notes.ini</font></b><br>
<br>
Before executing an import or export operation, the Notes user must select one file format from a set list. Variables in the notes.ini file tell Notes what library to load, given the file format selected by the user.<br>
<br>
The notes.ini file contains one line for each import/export library available to the Notes workstation. These lines begin with either EDITIMP, EDITEXP, VIEWIMP, or VIEWEXP, depending on whether they define an edit-level import library, edit-level export library, view-level import library, or view-level export library. Each line associates a particular file format with the name of the corresponding executable program library. <br>
<br>
For example, the notes.ini line that defines an edit-level import library has the form:<br>
<br>
EDITIMPxx=&lt;File Format Name&gt;,&lt;Export Param&gt;,&lt;Library Name&gt;,&lt;w4w arg&gt;,<extension>,...]

"EDITIMP" indicates that this line defines an edit-level import library. "xx" is a number that starts at 1 and is incremented for each successive edit-level import library. When you define a new edit-level import library, change the "xx" in "EDITIMPxx" to one number higher than that of the last EDITIMP reference.

Values to the right of the equals sign are separated by commas. 

<File Format Name> describes the file format this library handles. <File Format Name> is the string that appears in the List of File Types in the File - Import dialog box. 

<Export Param> provides Notes with information about certain export libraries. This parameter is always zero for imports. For edit-level exports, <Export Param> is normally two, indicating that Notes will create a temporary Compound Document file containing all the data to be exported.  A few Notes release 1.0 edit-level export libraries required the data from Notes in an in-memory buffer, which limited the data to 64K. <Export Param> should be zero for these buffer-based exports. For view-level exports, <Export Param> should be 1 if the export library can append data to the file being exported to. For file formats -- such as 1-2-3 worksheet files -- to which you cannot append data, <Export Param> must be zero, so that Notes will require the user to select a new file to export to instead of allowing the user to select an existing file to append to.

<Library Name> is the name of the executable program library file, prefixed by a platform-specific identifying character (see the "Platform-Specific Naming Conventions" chapter) without any file name extension. For example, the library name "__XTEXT" specifies that under Windows, Notes must use the library, NXTEXT.DLL.

<w4w arg> is used only when <Library Name> is "_W4W." The W4W library requires one of a number of alternate libraries; <w4w arg> provides the alternate library name.

<extension> is a file name extension that Notes should associate with this file format. If the Notes user selects a file for import that has a matching file name extension, Notes automatically highlights the corresponding file format in the List of File Types in the File - Import dialog box.

For example, the line

EDITIMP22=Sample ASCII Import,0,_IEDIT,,.TXT,.PRN,.C,.H,.RC,.DEF,

adds iedit to the list of file import libraries available. The string "Sample ASCII Import" appears in the List of File Types in the File - Import dialog box.

---
