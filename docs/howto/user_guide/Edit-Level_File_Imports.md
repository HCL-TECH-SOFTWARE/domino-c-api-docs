##### Chapter 7-5
##### Edit-Level File Imports

Importing files into a rich-text field in a note is a two step process.<br>

<ol type="1">
<li>The file must be converted from its native format to a series of Notes Composite Data records (CD records) and stored on disk as a temporary file. One of the Notes Import DLLs performs this conversion.
<li>You must read the series of CD records into a buffer and use NSFItemAppend to append the buffer to a rich-text field in a note.</ol>
<br>
NOTE: The largest buffer you can append using NSFItemAppend is slightly smaller than 64 kilobytes. Handle larger files by breaking up the series of CD records (on CD record boundaries) into smaller sections and appending each section separately. We recommend that you hold buffer sizes to roughly 40 kilobytes (40,960 bytes). 
<ul>
<ul></ul>
</ul>
This chapter examines two sample programs, IMPORTER and LGIMPORT, that import files into a note. IMPORTER assumes that the file being imported is less than 40 kilobytes in length after being converted to a series of CD records. LGIMPORT divides the series of CD records into sections and appends them separately, so it can import files larger than 64 kilobytes.<br>
<br>
<br>
<b><font size="5" color="#000080">Notes Import DLLs</font></b><br>
<br>
Notes lets you import a number of file formats, including (among others):<br>

<ul type="disc">
<li>Ami Pro<font color="#FF0000"> </font>documents
<li>Character text files
<li>ANSI Metafiles
<li>Tagged Image File Format (TIFF) files
<li>Windows bitmap files
<li>PCX image files</ul>
<br>
A different<font color="#FF0000"> </font>Notes Dynamic Link Library (DLL) file handles each supported file format.  You can determine which Notes DLL supports a particular file format by examining the notes.ini file. For details, see the readme.txt files accompanying the IMPORTER and LGIMPORT example programs.  <br>
<br>
<br>
<b><font size="5" color="#000080">The IMPORTER Sample Program</font></b><br>
<br>
The sample program IMPORTER creates a note that contains a representation of the imported file in its rich-text field. The program takes three or four command line arguments:<br>

<ul type="disc">
<li>The filename of the database to which the note is to be added
<li>The fully qualified pathname to the DLL appropriate for the format of the graphic being imported
<li>The filename of the file to be imported
<li>The name of a second DLL that the import DLL will use to import a word-processing document.  If the file being imported is not a word-processing document, this parameter is omitted. 
<ul></ul>
</ul>
<br>
<b><font size="4" color="#000080">Converting the File To Domino Format</font></b><br>
<br>
IMPORTER first calls the subroutine IMPORTCD, which loads into memory the DLL specified on the command line, and then gets the address of the import function defined in the DLL.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>IMPORTER: Loading the Appropriate DLL, Getting Address of Import Function</b></td></tr>
</table>
<tt><font size="2">&nbsp;</font></tt><tt><font size="2">STATUS (LNCALLBACKPTR ProcAddress)(VOID *IXContext, WORD Flags, <br>
 &nbsp; &nbsp; &nbsp; &nbsp;HMODULE hModule, CHAR *AltLibraryName, CHAR *PathName); &nbsp; &nbsp;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; EDITIMPORTDATA EditImportData; &nbsp;/* Import DLL data structure &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;HMODULE hmod; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* module handle &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;STATUS Error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Return status from Notes calls */<br>
 &nbsp; &nbsp;CHAR *FileName; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* File name to be imported &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;CHAR TempName[] = &quot;DEFAULT.CD&quot;; /* Temp Filename for import. &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;CHAR *ModuleName; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* pointer to DLL module name &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;CHAR *DLLName &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* 2nd DLL for import of &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp; word-processing documents. &nbsp; */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; ModuleName = szModulePath;<br>
 &nbsp; &nbsp;FileName &nbsp; = szFileName;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; DLLName = szDLL;<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;/* Use OSLoadLibrary to load the import DLL and return a pointer to */<br>
 &nbsp; &nbsp;/* the main entry point. &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; <br>
 &nbsp; &nbsp;if (Error = OSLoadLibrary (ModuleName, (DWORD)0, &amp;hmod, &amp;ProcAddress))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;OSLoadLibrary failed.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
The call to OSLoadLibrary loads into memory the DLL specified on the command line and returns the address of the import function. <br>
<br>
Next, the program sets up an EditImportData structure, containing a filename and some default font information. The import function will create a temporary file with this name. The file will contain a sequence of Notes Composite Data records that corresponds to the original image.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Invoking the Conversion Function in Sample IMPORTER</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; STATUS (LNCALLBACKPTR ProcAddress)(VOID *IXContext, WORD Flags, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; HMODULE hModule, CHAR *AltLibraryName, CHAR *PathName); &nbsp; &nbsp;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; EDITIMPORTDATA EditImportData; &nbsp;/* Import DLL data structure &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;STATUS Error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Return status from Notes calls */<br>
 &nbsp; &nbsp;CHAR *FileName; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* File name to be imported &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;CHAR *DLLName &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* 2nd DLL for import of &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp; word-processing documents. &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Call the ProcAddress() function whose address we located within &nbsp;*/<br>
 &nbsp; &nbsp;/* the DLL loaded above. &nbsp;This is the SAME argument set that would &nbsp;*/<br>
 &nbsp; &nbsp;/* be used by an import/export DLL written to handle a non-standard */<br>
 &nbsp; &nbsp;/* file format. &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;/* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp;/* The ProcAddress() function can import multiple files. &nbsp;Since &nbsp; &nbsp; */<br>
 &nbsp; &nbsp;/* only one file is being imported in this example, the flags will &nbsp;*/<br>
 &nbsp; &nbsp;/* indicate that the file is the first (and also last) file to be &nbsp; */<br>
 &nbsp; &nbsp;/* imported. &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (Error = (*ProcAddress) (&amp;EditImportData, &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;IXFLAG_FIRST | IXFLAG_LAST, &nbsp; &nbsp; &nbsp; &nbsp; /* Both 1st and last import */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;0, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Use default hmodule &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;DLLName, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* 2nd DLL, if needed. &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;FileName)) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* File to import. &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Call to DLL Entry point failed.\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;goto Done;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
The call to (*ProcAddress)() invokes the import function. The parameter &quot;filename&quot; contains the name of the file being imported, while the EditImportData structure contains the name of the temporary file to create. <br>
<br>
When you import more than one file, the import DLLs may perform some special processing for the first or last file in the series. The code above sets the flags IX_FIRST and IX_LAST to indicate that only one file is to be imported; it is both the first and the last file. If the file being imported is a word-processing document, the DLLName parameter specifies the name of an additional DLL used to import that particular file format. For details, see the readme.txt  file for either  IMPORTER or LGIMPORT.<br>
<br>
If the call is successful, the name of the temporary file must be returned to the calling routine.<font color="#FF0000"> </font><br>
<br>
<br>
<b><font size="4" color="#000080">Placing the Imported Data in a Rich Text Field</font></b><br>
<br>
IMPORTER then calls the subroutine LOADCD, which opens the temporary file and calculates how large a buffer is needed to hold the file contents. If a buffer larger than MAX_ALLOC is needed, the program exits with an error message. Otherwise, LOADCD allocates a buffer of the proper size, reads the entire file into the buffer, and returns the buffers handle and the buffer length to the calling routine.<br>
<br>
IMPORTER then calls the subroutine AddRichText to create a rich text field containing the information imported from the file. AddRichText allocates a buffer in which to construct the rich text item and then adds to the buffer a CDPARAGRAPH, a CDPABDEFINITION, and a CDPABREFERENCE. For information about these structures, see &quot;Introduction to Rich Text.&quot;<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Appending the Imported Data to the Note in Sample IMPORTER</b></td></tr>
</table>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Lock down the Import buffer and get a pointer to it. &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pImpBuffer = (CHAR *) OSLockObject(hImpBuffer) + sizeof(WORD);<br>
 &nbsp; &nbsp;dwItemBufLen = dwBufLen - sizeof(WORD);<br>
 &nbsp; &nbsp;if ((dwCDBufLen + dwItemBufLen) &gt; dwCDMaxBuf)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;\nCD Buffer not big enough for import file. &nbsp;&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;Terminating...\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hImpBuffer); /* Unlock Import buffer. &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hCDBuffer); &nbsp;/* Unlock &nbsp;CD buffer. &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(hCDBuffer); &nbsp; &nbsp; &nbsp; /* Free up the CD buffer. &nbsp;*/ <br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Move the imported data into CD buffer &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; memmove(&amp;pCDBuffer[dwCDBufLen], pImpBuffer, (WORD) dwItemBufLen);<br>
 &nbsp; &nbsp;dwCDBufLen += dwItemBufLen;<br>
 &nbsp; &nbsp;if (dwCDBufLen % 2) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* if len is odd, &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;dwCDBufLen++; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp; make it even &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* Append the &quot;Body&quot; item to the note */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (rError = NSFItemAppend(hNote,0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &quot;Body&quot;, strlen(&quot;Body&quot;),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_COMPOSITE,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pCDBuffer, dwCDBufLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf(&quot;\nError adding 'Body' item. Terminating...\n&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hImpBuffer); /* Unlock Import buffer. &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSUnlockObject(hCDBuffer); &nbsp;/* Unlock &nbsp;CD buffer. &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSMemFree(hCDBuffer); &nbsp; &nbsp; &nbsp; /* Free up the CD buffer. &nbsp; &nbsp;*/ <br>
 &nbsp; &nbsp; &nbsp; &nbsp;goto Done;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
The code fragment above copies the buffer containing the imported data into the rich text buffer. It then uses the function NSFItemAppend to append the rich text buffer to the field in the note called &quot;Body,&quot; as a record of type TYPE_COMPOSITE. <br>
<br>
The code then unlocks and frees all buffers and returns to the calling routine. IMPORTER then saves the note to disk, cleans up, and ends.<br>
<br>
<br>
<b><font size="5" color="#000080">The LGIMPORT Sample Program</font></b><br>
<br>
LGIMPORT is similar to IMPORTER, except it is not restricted to importing files smaller than 64 kilobytes. The program takes three or four command line arguments:<br>

<ul type="disc">
<li>The filename of the database to which the note is to be added
<li>The fully qualified pathname to the DLL appropriate for the format of the graphic being imported
<li>The filename of the graphic file to be imported
<li>The name of a second DLL that the import DLL will use to import a word-processing document. If the file being imported is not a word-processing document, this parameter is omitted. 
<ul></ul>
</ul>
<br>
<b><font size="4" color="#000080">Converting the File to Domino or Notes Format</font></b><br>
<br>
LGIMPORT first calls the subroutine ImportCD, which loads into memory the DLL specified on the command line, and then gets the address of the import function defined in the DLL. ImportCD is identical to the subroutine of the same name in the sample program IMPORTER.<br>
<br>
<br>
<b><font size="4" color="#000080">Appending the Imported Data to the Note</font></b><br>
<br>
After LGIMPORT creates a note in the database specified on the command line and writes a couple of simple data fields in the note, it calls the subroutine AppendImportItem to append the image (now in Notes CD record format).<br>
<br>
AppendImportItem opens the temporary file containing the imported<font color="#FF0000"> </font>data<font color="#FF0000"> </font>and allocates a 64,000 byte buffer in which to construct the rich-text item. The function places a CDPARAGRAPH, a CDPABDEFINITION, and a CDPABREFERENCE into the buffer. The contents of the temporary file are then read into the buffer. <br>
<br>
If the entire contents of the temporary file fit into the buffer, LGIMPORT appends the buffer to the note, unlocks and frees buffers, and returns to the main routine. If the file is too big to fit into the buffer, LGIMPORT parses the buffer one CD record at a time, adding up the lengths of the CD records parsed. When the length approaches CD_HIGH_WATER_MARK, LGIMPORT appends the buffer to the note. It then resets the file pointer to the first CD record not parsed, reads from the temporary file into the buffer again, and repeats the process of reading, parsing, and appending to the note until it has processed the entire file. After unlocking and freeing buffers, LGIMPORT returns to the main program, writes the note to disk, cleans up, and ends.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Appending the Imported Data to the Note in Sample LGIMPORT</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; /* Keep on writing items until entire CD file has been appended &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; while (bFlag == FALSE)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* Seek file to end of previous CD record &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (lseek (CDFileFD, longpos, SEEK_SET) != longpos)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Leave if error returned... &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; free (pCDBuffer);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;close (CDFileFD);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;unlink (pszCDFile);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (ERR_APPEND_RICHTEXT_ERROR);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><tt><font size="2">&nbsp; &nbsp; /* Read the contents of the file into memory &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; wReadLength = read(CDFileFD, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;pCDBuffer[wItemLength], <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD)(wCDBufferLength - wItemLength));</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* check for error &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (wReadLength == 0xffff)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Leave if error returned... &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; free (pCDBuffer);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;close (CDFileFD);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;unlink (pszCDFile);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (ERR_APPEND_RICHTEXT_ERROR);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2"><br>
 &nbsp; &nbsp; &nbsp; &nbsp;/* See whether the contents will fit in current item.... &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (wReadLength &lt; CD_HIGH_WATER_MARK)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* fit what is left in a single buffer and leave loop */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; bFlag = TRUE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wItemLength += wReadLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;else<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * Parse the buffer one CD record at a time, adding up the lengths<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * of the CD records. &nbsp;When the length approaches CD_HIGH_WATER_MARK,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * append the buffer to the note. &nbsp;Set the file pointer to the first <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * record not parsed, read from the temp file into the buffer again,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * and repeat until end of temp file.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * All CD records begin with a signature word that indicates its<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * type and record length. &nbsp;The low-order byte is the type and <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * the high-order byte is the length. &nbsp;If the indicated length is 0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * the next DWORD (32 bits) contains the record length. &nbsp;If the <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * indicated length is 0xff, the next WORD (16 bits) contains the <br>
 &nbsp; &nbsp; &nbsp; &nbsp; * record length. &nbsp;Otherwise, the high order BYTE itself contains &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * the record length.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wCDRecordLength = 0 ;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;lLength = 0 ;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;lCombinedLength = wItemLength + wCDRecordLength ;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while (lCombinedLength &lt; CD_HIGH_WATER_MARK)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pbSig = &amp;pCDBuffer[wItemLength];<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wSig = &nbsp;*(WORD*)pbSig;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pbSig++;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* find length of CD record. &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (*pbSig == 0) &nbsp; &nbsp;	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* record length is a DWORD &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pbSig++;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wCDRecordLength = (WORD)*(DWORD*)pbSig;				<br>
	 &nbsp; &nbsp; &nbsp; &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else if (*pbSig == 0xFF) &nbsp; &nbsp; &nbsp; /* record length is a WORD &nbsp;*/<br>
 &nbsp; 		 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pbSig++;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wCDRecordLength = *(WORD*)pbSig;				<br>
		 &nbsp; }</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;else	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* record length is the BYTE */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wCDRecordLength = (WORD)*pbSig;				<br>
				<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (wCDRecordLength % 2) &nbsp; &nbsp; &nbsp; /* if len is odd, make it even */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wCDRecordLength++;</font></tt><br>
<br>
<tt><font size="2">		 &nbsp; /* update CD buffer pointers */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;lLength = lLength + (long)wCDRecordLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ltmpItemLength = (long)wItemLength + (long)wCDRecordLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (ltmpItemLength &lt; CD_BUFFER_LENGTH)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wItemLength += wCDRecordLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; lCombinedLength = (long)ltmpItemLength + (long)wCDRecordLength;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /* </font></tt><tt><font size="2">Append the imported item to the note &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; if (wItemLength &gt; 0)<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (sError = NSFItemAppend(hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD) 0, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pszItemName, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD) strlen(pszItemName),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_COMPOSITE, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pCDBuffer, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (DWORD)wItemLength))<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Leave if error returned... &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; free (pCDBuffer);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;close (CDFileFD);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;unlink (pszCDFile);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;return (ERR(sError));<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp;	 &nbsp;/* update import file position and reset next item length */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; longpos += lLength ;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;wItemLength = 0;<br>
 &nbsp; &nbsp;}</font></tt>
---
