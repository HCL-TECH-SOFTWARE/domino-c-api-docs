##### Chapter 7-8
##### Embedding and Extracting OLE 2 Objects

This chapter describes how to embed in a rich text field an OLE 2 object that has been streamed to a structured storage file and how to extract an embedded OLE 2 object to a structured storage file.<br>
<br>
<b><font size="5" color="#000080">Embedding an OLE 2 Object in a Note</font></b><br>
<br>
The basic steps to embedding an OLE 2 object in a note are: create a root structured storage file; create a substorage for the object; create an object on the substorage; save the object to its persistent storage (structured storage file); use the function NSFNoteAttachOLE2Object to attach the OLE 2 structured storage file to the note; and then add a sequence of CD records that refer to the OLE 2 file to the note's rich text field.  The sequence of CD records starts with a CDOLEBEGIN record and ends with a CDOLEEND record.  Between these two data structures are other CD records that form a visual representation of the embedded object. <br>
<br>
<br>
<b><font size="4" color="#000080">CDOLEBEGIN</font></b><br>
<br>
The CDOLEBEGIN record is a variable-length structure containing the following information:<br>

<ul type="disc">
<li>Header information specifying that this is a CDOLEBEGIN data record
<li>The Notes OLE implementation version number
<li>Flags (defined in editods.h) specifying whether the object is embedded or linked
<li>The Clipboard format in which the data is rendered
<li>The name of the attached file
<li>Optionally, the name of  the object's class<br>
</ul>
<br>
<b><font size="4" color="#000080">Other CD Records</font></b><br>
<br>
Between the CDOLEBEGIN and CDOLEEND structures is a sequence of CD records that represent the data contained in the OLE object.  The specific sequence of records depends on the type of object being embedded.<br>
<br>
<b><font size="4" color="#000080">CDOLEEEND</font></b><br>
<br>
The CDOLEEND structure contains only header information and a DWORD of currently unused flags.  It delimits the end of the OLE object .<br>
<br>
<br>
<b><font size="5" color="#000080">Discussion of OLE2\ATTACH Sample</font></b><br>
<br>
The OLE2\ATTACH sample program creates a note in which the rich text field contains an embedded Windows Paint (Bitmap) object.  Clicking on the embedded object from the user interface invokes the Paint program (launching it if it is not already running) and displays a Notes icon on the Paint workspace.<br>
<br>
<br>
<b><font size="4" color="#000080">attach.c</font></b><br>
<br>
The program OLE2\ATTACH creates a temporary, root structured storage file; creates a substorage for the embedded object; calls OleCreateFromFile specifying the full path to the bitmap file from which the object is created and the newly created substorage; saves the object to its persistent storage (this will create all necessary streams in the structured storage file); opens the database embedole.nsf and creates in it a new note using the form &quot;Simple Form&quot;.  It then calls the function NSFNoteAttachOLE2Object to attach the structured storage file to the note. OLE2\ATTACH then calls the subroutine AppendRichText (found in cdrecord.c), passing it all the information needed to define the OLE object.  After returning from AppendRichText, the program updates the note, closes the database, and ends.<br>
<br>
<br>
<b><font size="4" color="#000080">cdrecord.c</font></b><br>
<br>
AppendRichText calls the subroutine PutOLEBegin to construct the CDOLEBEGIN record.  AppendRichText then calls PutText to insert a string of text as a temporary visualization of the object's data.  Finally, AppendRichText calls PutOLEEnd to construct the CDOLEEnd CD record. <br>
<br>
<br>
<b><font size="5" color="#000080">Extracting an OLE 2 Object in a Note</font></b><br>
<br>
The function NSFNoteExtractOLE2Object is used to extract an OLE 2 object in a note to a structured storage file.<br>
<br>
<br>
<b><font size="5" color="#000080">Discussion of OLE2\EXTRACT Sample</font></b><br>
<br>
The OLE2\EXTRACT sample program finds all of the notes in the database embedole.nsf that contain an embedded OLE2 object and extracts the first object in each of these notes to a separate structured storage file.<br>
<br>
<b><font size="4" color="#000080">extract.c</font></b><br>
<br>
The program OLE2\EXTRACT calls ProcessOneNote for each data note in the database embedole.nsf that contains an embedded OLE 2 object which, in turn, calls ProcessOneCDRecord for the first embedded object in the note.  ProcessCDRecord constructs a structured storage file name from the extendable $FILE name referenced in the CDOLEOBJ_INFO structure, then calls NSFNoteExtractOLE2Object to extract the object to a structured storage file of this name.  Then, using OLE API calls, it opens the structured storage file and dumps the 'Contents' stream.
---
