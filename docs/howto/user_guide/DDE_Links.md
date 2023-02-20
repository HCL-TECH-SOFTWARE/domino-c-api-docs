##### Chapter 7-4
##### DDE Links

This chapter describes how to place links to DDE server applications in a rich text field in a note.<br>
<br>
NOTE: DDE embedded documents are no longer supported by Notes. When you try to launch an embedded DDE object from the Notes user interface, Notes will ask if you would like to attach the embedded document to the note.<br>
<br>
<br>
<b><font size="5" color="#000080">Definitions</font></b><br>
<br>
DDE: Dynamic Data Exchange, a mechanism of interprocess communication supported under Windows.<br>
<br>
DDE Server: A program containing data that is of use to other programs.<br>
<br>
DDE Client: A program that obtains this data from the DDE server.<br>
<br>
OLE: Object Linking and Embedding, an improved protocol for interprocess communication supported under Windows and implemented using DDE. Notes automatically uses the OLE protocol if the application supports it, but this requires no changes from the C API or user interface point of view.<br>
<br>
<br>
<b><font size="5" color="#000080">Creating the Link</font></b><br>
<br>
A DDE link consists of a series of Composite Data records, beginning with CDDDEBEGIN and ending with CDDDEEND. Between these two data structures are other CD records describing the DDE link. <br>
<br>
<br>
<b><font size="4" color="#000080">CDDDEBEGIN</font></b><br>
<br>
The CDDDEBEGIN structure contains all the data necessary to forge a DDE link with a DDE server application. This data includes:<br>

<ul type="disc">
<li>Header information specifying that this is a CDDDEBEGIN data record
<li>The DDE server name (the name of the server application)
<li>The DDE topic name (usually the name of the file containing the data)
<li>The DDE item name, which specifies the range of data referenced in the link
<li>Flags (defined in editods.h) specifying the type of link to forge
<li>The filename of an attached file, if there is one
<li>Other flags</ul>
<br>
<br>
<b><font size="4" color="#000080">Application-Specific Data Structures</font></b><br>
<br>
Following the CDDDEBEGIN data structure are one or more Composite Data records that describe the data referenced by the link. The specific CD records vary depending on the DDE server application to which the note is linked.<br>
<br>
<br>
<b><font size="4" color="#000080">CDDDEEND</font></b><br>
<br>
The CDDDEEND structure contains only header information and a DWORD of currently unused flags. It delimits the end of the information in the DDE link.
---
