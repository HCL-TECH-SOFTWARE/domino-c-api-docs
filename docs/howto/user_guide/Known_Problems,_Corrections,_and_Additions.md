##### Chapter 0-3
##### Known Problems, Corrections, and Additions

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter lists known problems and last-minute corrections and additions.<br>
<br>
<b><font size="5" color="#000080">All Platforms</font></b><br>
<br>
The following problems exist in HCL Notes/Domino 12.0.2 for all platforms. These problems are visible during C API function calls. They are not problems with the HCL C API Toolkit for Domino and Notes itself but with the underlying Domino and Notes core routines that implement C API functions.<br>
<br>
Future releases of Domino and Notes may fix these problems. When they are fixed (and you install the new version of Domino or Notes) your C API programs will automatically receive the fixes. You will not have to recompile your C API applications, since C API programs link to the Domino or Notes core routines at run time.<br>
<br>
The known problems with the C API on all platforms are:<br>

<ul><b><font size="4" color="#000080">Creating a Database</font></b><br>
There is an issue with the size of the pathname that is specified when creating a database with the C API.  The functions affected include NSFDbCreate, NSFDbCreateExtended, NSFDbCreateAndCopy and NSFDbCreateAndCopyExtended.  If you are creating a database from a client to a server, this pathname is limited to 100 bytes.    This problem also occurs when creating a database with the Notes client and with Domino Designer.<br>
<br>
<b><font size="4" color="#000080">CompoundTextAssimilateItem</font></b><br>
This function does not handle features of rich text that depend on special items that reside outside the rich text field specified by the &quot;pszItemName&quot; parameter.<br>
<br>
Two such features of rich text include doc links that depend on the special $Links item, and font faces that depend on the special $Fonts item. These special items in the note reside outside the specified rich text field.  Therefore, when CompoundTextAssimilateItem merges a rich text field containing doc links consisting of CDLINK2 records into a Compound Text context, the doc link in the resulting compound text does not function. A work-around to this problem is demonstrated by sample program HISTORY in the RICHTEXT directory. <br>
<br>
Also, when CompoundTextAssimilateItem merges a rich text field containing font faces that require a font table (a $Fonts item in the note)  the resulting compound text does not reflect the font face used in the original field.<br>
<br>
<b><font size="4" color="#000080">SMTP Extension Managers</font></b><br>
In the extension manager callback routine, SMTPCommandEMCallback, you can reject the command for the SMTPConnect event with a return STATUS value other than ERR_EM_CONTINUE and NOERROR from the EM_BEFORE notification.  When you reject the MAIL command, the server prevents the client from sending mail.  However, the SMTP server allows intervening commands to succeed, such as VRFY and EXPN, when it should not (SPR LGIE46AQ6U).<br>
<br>
<b><font size="4" color="#000080">Note Creation Time in web.nsf</font></b><br>
The &quot;Note&quot; field in the ORIGINATORID structure for notes created in the InterNotes database web.nsf does not contain the creation date and time for the note.  This database stores information about Universal Reference Locators (URLs) for Web documents.  Instead, this field contains a hash key based on the URL.  Applications should first check a note for the existence of the item $CREATED.  If this item exists, it contains the date and time the note was created.  If this item does not exist, the &quot;Note&quot; field of the ORIGINATORID structure contains the date and time the note was created.<br>
<br>
<b><font size="4" color="#000080">1-2-3 File Import</font></b><br>
Character-mode C API programs cannot use the iwske import library included with Notes to import a Lotus 1-2-3 worksheet into Notes. The import function in this DLL returns error code 0x9D0E, which is STS_DISPLAYED | PKG_IMPORT | ERR_IWKSE_USER_ABORT. The function returns this error because it cannot display a dialog box asking the user if a range or the whole file is being imported. <br>
<br>
<b><font size="4" color="#000080">FTSearch</font></b><br>
Using FTSearch with the multiple database search option will not work correctly if the program is not in the Domino or Notes executable directory.  <br>
<br>
<b><font size="4" color="#000080">CDEVENTENTRY</font></b><br>
The possible values for the wActionType member of the CDEVENTENTRY structure have not been exposed in the HCL C API Toolkit for Notes/Domino, but are documented in the Reference for this entry.  Also, all possible values for the wEventId member have not been exposed. <br>
</ul>
<font size="2">   </font><br>
<b><font size="5" color="#000080">Windows</font></b>
<ul><br>
<b><font size="4" color="#000080">Windows NT Services</font></b><br>
HCL C API applications for Domino and Notes can be run as a Windows NT Service.  A system environment variable, NOTESNTSERVICE=1, must be set before running a C API application as a Windows NT Service.  If this environment variable is not set, calls to the Domino or Notes C API which require any user authentication (for example, NSFDbOpen()) made after the user starting the service logs off will fail.   For more information on Windows NT Services, please refer to the Microsoft Win32 documentation.</ul>
<font size="2">    </font><br>
<br>
<b><font size="5" color="#000080">Unix</font></b><br>

<ul><b><font size="4" color="#000080">Linux and the </font></b><b><i><font size="4" color="#000080">gets(..)</font></i></b><b><font size="4" color="#000080"> function.</font></b><br>
Please be advised there is a known bug in the function <i>gets(..)</i> under Linux Red Hat.  Linux Red Hat recommends using <i>fgets(..) </i>instead.  Our samples which use <i>gets(..) </i>will compile with a warning concerning the bug in <i>gets(..)</i>.  At this point in time we have not run into any problems with our samples that use the <i>gets(..)</i>function.  We anticipate the bug to <i>gets(..)</i> will be resolved in a newer version of Linux Red Hat.</ul>
<br>
<br>
<b><font size="5" color="#000080">Sample Programs</font></b>
<ul><br>
Chapter 2-3 of this <i>User Guide</i> lists the sample programs included in this toolkit and the planned supported platforms. <br>
<br>
<b><font size="4" color="#000080">tracker</font></b>
<ul>Tracker should be removed from the notes.ini file before returning to normal use of Domino or Notes.<br>
<br>
Tracker does not check the OpenFlags parameter for the OPEN_CANONICAL flag in its TrackerNoteOpen routine.  Tracker assumes that the entire note has not been opened with the OPEN_CANONICAL flag.  This assumption is true as long as the note's item information is not transmitted over a network.  If a database hook driver accesses a note's item over a network, it should check the OPEN-CANONICAL flag in its NoteOpen routine and, if set, use ODSReadMemory to convert any canonical data to host data.<br>
</ul>
<b><font size="4" color="#000080">ragents</font></b>
<ul>Currently when attempting to execute a Java Agent using the HCL C API for Domino and Notes, Java console errors are displayed.  For this reason the ragents sample has not been enhanced to include execution of the Java Agent.  Instead, the Java Agent is executed manually from the Notes UI.  <br>
  </ul>
<b><font size="4" color="#000080">ftsearch</font></b>
<ul>Be sure to check for 0 in the parameter retNumDocs (i.e. no document returned) after calling the FTSearch API.  When there is no document returned, the value of the parameter rethResults will be NULLHANDLE, and trying to do OSLock on a NULLHANDLE will cause a crash.<br>
</ul>
<b><font size="4" color="#000080">sel_rep, namelook, uiaddin, iedit, xedit, and xview</font></b>
<ul>These samples require a Notes client and are not supported on server-only platforms (UNIX).<br>
</ul>
<b><font size="4" color="#000080">backup</font></b>
<ul>The &quot;dbrecs&quot; sample may fail when run with the &quot;RECOVER&quot; option and given a root directory as an input file (i.e. &quot;dbrecs RECOVER e:\&quot;).</ul>
</ul>

---
