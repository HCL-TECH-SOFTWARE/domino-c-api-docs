##### Chapter 1-2
##### New Features in HCL C API Toolkit for Notes/Domino 12.0.2 

This section lists the new and changed features in the HCL C API Toolkit for Notes/Domino 12.0.2<font color="#242424" face="Segoe UI">.</font> See the <i>What's New view</i> in the <i>HCL C API Reference </i>for details.<br>
<b><font size="5" color="#000080"> </font></b><br>
<b><font size="5" color="#000080">NSF Database Functions</font></b><br>
<br>
Some new and changed functions of database have been added tonsfmime.h ,nsfsear.h
<ul type="disc">
<li><font size="4" face="Times New Roman">NSFIsFileItemMimePart</font><font size="4"> </font>	<font size="4" face="Times New Roman">Searches all TYPE_MIME_PART items on the note to see if the given $File item contains MIME part data. If $File item has MIME part then it returns TRUE, FALSE otherwise.</font> 
<li><font size="4" face="Times New Roman">NSFIsMimePartInFile</font><font size="4"> </font>   <b><font size="4" color="#242424" face="Segoe UI"> </font></b><font size="4">Checks to see if the given MIME part's content is in a file in the given note handle. It checks that the given MIME part is stored in the file content, and when it is true it returns the file name of the MIME part's content.</font>
<li><font size="4" face="Times New Roman">NSFSearchExt2</font><font size="4"> </font>	            Uses an associated timer to control the duration of the database search operation.<br>
</ul>
<br>
<b><font size="5" color="#000080">Operating System Functions</font></b><br>
<br>
A new function of OS has been added toosfile.h
<ul type="disc">
<li><font size="4" face="Times New Roman">OSPathAddTrailingPathSeparator</font><font size="4"> </font>    Adds a trailing path separator, if the last character in the path is not a separator. </ul>
<br>
<b><font size="5" color="#000080">Notes Index Facility Functions</font></b><br>
<br>
Some new functions of NIF have been added tonif.h.
<ul type="disc">
<li><font size="4" face="Times New Roman">NIFIsUpdateInProgress</font><font size="4"> </font>	Can be called by callers who want to find out if the collection is being updated and don't want to perform the update themselves.
<li><font size="4">NIFGetCollectionViewNoteIDAndDB</font><b><font size="4">   </font></b>This routine defines if the given user structure is valid. It then validates and dereferences the handle, returning a specific error if it is an invalid or null handle.
<li><font size="4" face="Times New Roman">NIFFindByKeyExtended4</font><font size="4">     </font>Identical to NIFFindByKeyExtended3 with the addition of an associated timer for search operation (avoids hanging the collection).</ul>
<br>
<b><font size="5" color="#000080">IDTable</font></b><b><font size="5" color="#000080">Functions</font></b><br>
<br>
Some new and changed functions of id table have been added toidtable.h.
<ul type="disc">
<li><font size="4" face="Times New Roman">IDTableReplaceExt</font><font size="4"> </font>	Replaces the ID table content from the another ID table. This routine validates the ID table headers for new format and replaces the content accordingly<font size="4" face="Times New Roman">.</font>
<li><font size="4" face="Times New Roman">IDInsertRange</font><font size="4"> </font>	<font size="4" face="Times New Roman">            </font>This function inserts a range of IDs into a given ID table. The range is inclusive. Also, if the &quot;AddtoEnd&quot; parameter is set to TRUE, it guarantees that the ID range does not overlap any IDs in the table and are the largest IDs in the table.
<li><font face="Times New Roman">IDTableSplitDeleted</font><font size="4">           </font>Splits out deleted noteIDs from the source table and returns the deleted IDs as an output. <font size="4"> </font><br>
</ul>
<br>
<b><font size="5" color="#000080">LDAPFunctions</font></b><br>
<br>
A new function of id table has been added toldap.h
<ul type="disc">
<li><font size="4" face="Times New Roman">ldap_sslinit </font><font size="4">                    </font>Initializes a secure session with an LDAP server and returns a &quot;session handle,&quot; a pointer to an opaque structure that MUST be passed to subsequent calls pertaining to the session. This routine returns a NULL if the session cannot be initialized.  <br>
</ul>
<br>
<b><font size="5" color="#000080">MIMEFunctions</font></b><font size="4">   </font><br>
<font size="4">     </font><br>
A new function of id table has been added tomime.h
<ul type="disc">
<li><font size="4" face="Times New Roman">MIMEEMLExport3</font><font size="4"> </font>   Exports the MIME content (e-mail messages) of the given noteID into the eml file.<font size="4"> </font><br>
</ul>
<br>
<b><font size="5" color="#000080">RFCTIMEDATE Functions</font></b><br>
<br>
Some new functions of id table have been added tomish.h.
<ul type="disc">
<li><font size="4" face="Times New Roman">ConvertRFC3339DateToTIMEDATE</font><font size="4">      </font>Converts a date/time string from RFC3339 format to Notes TimeDate format. 
<li><font size="4" face="Times New Roman">ConvertTIMEDATEtoRFC3339Date</font><font size="4">       </font>Converts a time/date string from Notes TimeDate format to RFC3339 format.<br>
<font size="4"> </font></ul>

---
