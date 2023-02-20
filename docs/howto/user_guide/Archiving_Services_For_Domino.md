##### Chapter 12-17
##### Archiving Services For Domino

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
The Archiving Services API allow you to:
<ul>
<ul type="disc">
<li>Stream notes document and attachment data from a notes database directly to an archive repository. 
<li>Restore notes document and attachment data back to its original state with no fidelity loss. 
<li>Generate index data based on exported content. 
<li>Optimize storage of redundant data such as message body and attachments.</ul>
</ul>
<br>
<b><font size="5" color="#000080">Exporting Documents</font></b><br>
<br>
The ArchiveExportDatabase function copies notes and their related attachments from a database and passes the exported data to callers via a set of callback functions. Attachments are decompressed so that they may be consumed by programs that understand their native format. Notes documents are encoded into a canonical format that is opaque to the caller but can be manipulated in a limited way by the Archiving Services API.<br>
<br>
ArchiveExportDatabase is able to copy many notes and attachments in a single client/server interaction which provides benefits in terms of network overhead, but it requires the caller implement 4 callback functions that represent the state of the note streaming operation. The signature of the ArchiveExportDatabaseFunction:<br>
<br>
<tt>STATUS LNPUBLIC </tt><tt>ArchiveExportDatabase</tt><tt>(	</tt><br>
<tt>						DBHANDLE hDb,	</tt><br>
<tt>						DHANDLE hIDTable,	</tt><br>
<tt>						DWORD Flags,</tt><br>
<tt>						NOTEINITCALLBACK 	NoteInitCallback,		</tt><br>
<tt>						ARCHIVEATTACHINIT AttachInitCallback,		</tt><br>
<tt>						ARCHIVEATTACHOUTPUT AttachOutputCallback,					</tt><br>
<tt>	 &nbsp; 					ARCHIVEDOCUMENTCALLBACK ArchiveDocumentCallback,		</tt><br>
<tt>						KFHANDLE hKFC, 			</tt><br>
<tt><b><font color="#000080">						</font></b></tt><tt>void</tt><tt>&nbsp;</tt><tt>*</tt><tt>pUserCtx);</tt><br>
<br>
 The first two pararameters indicate which database and what documents are to be exported. Flags is currently unused (see the API reference guide for the latest details). <br>
<br>
<b><font size="4" color="#000080">NoteInitCallback</font></b><br>
<br>
NoteInitCallback is called for every note that is copied by ArchiveExportDatabase. This function marks the start of the copy process for every document and is typically used to initialize some sort of storage location for the exported document. The signature of NoteInitCallback:<br>
<br>
<tt>typedef</tt><tt>&nbsp;</tt><tt>STATUS </tt><tt>(LNCALLBACKPTR NOTEINITCALLBACK)</tt><br>
<tt>	(</tt><br>
<tt>	NOTEHANDLE hNote,</tt><br>
<tt>	STATUS retError,	</tt><br>
<tt>	void</tt><tt>&nbsp;</tt><tt>*</tt><tt>pUserCtx	</tt><br>
<tt>	);</tt><br>
<br>
The hNote is a handle to an open note (assuming retError is NOERROR) which can be used to gather metadata useful for archiving. One must not invoke a function that will cause a remote call to a server in this function. The result will be a panic from code where this function is called. Implementers should check the retError value as it indicates the error status of the streaming operation. It can be the case that IDTable passed to ArchiveExportDatabase references a note that doesnt exist or has since been deleted, in which case retError will indicate ERR_NOEXIST or ERR_NOTE_DELETED respectively. Implementors can return NOERROR in these cases to keep processing the remaining notes in hIDTable. <br>
<br>
<b><font size="4" color="#000080">AttachInitCallback</font></b><br>
<br>
If there are attachments in a note, AttachInitCallback will be invoked next. AttachInitCallback indicates that attachment data is about to be sent. The signature of the callback: <br>
<br>
<tt>typedef</tt><tt>&nbsp;</tt><tt>STATUS </tt><tt>(LNCALLBACKPTR ARCHIVEATTACHINIT)		</tt><br>
<tt>	(	</tt><br>
<tt>	</tt><tt>const</tt><tt>&nbsp;</tt><tt>char</tt><tt>&nbsp;</tt><tt>*</tt><tt>szFileName,</tt><br>
<tt>	DWORD dwFlags,		</tt><br>
<tt>	DWORD dwDupIdx,		</tt><br>
<tt>	STATUS retError,		</tt><br>
<tt>	void</tt><tt>&nbsp;</tt><tt>*</tt><tt>pUserCtx</tt><br>
<tt>	);</tt><br>
<br>
szFileName is the original filename of the attachment when it was added to the database. Implementors should check dwFlags as they indicate some important aspects about the data that will be sent. There are currently 3 flags that can be passed: ARCHIVE_ATTACH_ENCRYPTED, ARCHIVE_ATTACH_MACBIN_RAW, and ARCHIVE_ATTACH_RAW<br>
<br>
ARCHIVE_ATTACH_ENCRYPTED indicates that an attachment is going to be passed encrypted and therefore cannot be consumed by its originating application without being restored back to a Notes database. <br>
<br>
ARCHIVE_ATTACH_MACBIN_RAW indicates that the attachment is a Mac binary attachment as it is stored in NSF. It is therefore not consumable as a Mac binary file unless it is restored to a Notes database and extracted with NSFNoteExtractFile (or with the Notes client). <br>
<br>
ARCHIVE_ATTACH_RAW indicates that the file is an object stored by NSF that is only known to Notes. Implementers must store this object and return it to the database when restoring the associated note. <br>
<br>
dwDupIdx is used to differentiate attachments that have the same file name. <br>
<br>
Implementers should examine retError for possible error conditions that may occur during the streaming operation. While there are no known recoverable errors, it will be considerably easier to track down issues if the calling code is aware of when an error condition arises and reports it accordingly. Returning a non-zero error status will cause ArchiveExportDatabase to stop.  <br>
<br>
<b><font size="4" color="#000080">AttachOutputCallback</font></b><br>
<br>
<tt>Attachment data is passed via the AttachOutputCallback function provided by the caller. &nbsp;The signature of the callback:</tt><br>
<br>
<tt>typedef</tt><tt>&nbsp;</tt><tt>STATUS </tt><tt>(LNCALLBACKPTR ARCHIVEATTACHOUTPUT)		</tt><br>
<tt>	(</tt><br>
<tt>	</tt><tt>const</tt><tt>&nbsp;BYTE </tt><tt>*</tt><tt>Buffer,		</tt><br>
<tt>	DWORD BufferSize,		</tt><br>
<tt>	BOOL bLastBuffer,		</tt><br>
<tt>	STATUS retError,		</tt><br>
<tt>	void</tt><tt>&nbsp;</tt><tt>*</tt><tt>pUserCtx</tt><br>
<tt>	);</tt><br>
<br>
Data is passed through the Buffer parameter. The amount of data is indicated by BufferSize. When bLastBuffer is true, implementers know to clean up resources that may have been allocated to receive the data. Callers should examine retError to ensure that there are no errors in the streaming operation. There is one recoverable error passed by retError, ERR_ARCHIVE_DECOMPRESSION_RETRY. This indicates that there was a problem decompressing the data just passed (since the AttachInitFunction). It is recommended that implementors delete any resources created with this data and return NOERROR. This will allow the streaming operation to retry decompression with a different algorithm. There can be up to 2 retries after which the attachment will be considered unreadable. It should be noted that the AttachInitCallback function will not be called before each retry. <br>
<br>
<b><font size="4" color="#000080">ArchiveDocumentCallback</font></b><br>
<br>
Once all attachments have been received, the notes document in its archived form is passed to the caller. The signature of the callback:<br>
<br>
<tt>typedef</tt><tt>&nbsp;</tt><tt>STATUS </tt><tt>(LNCALLBACKPTR ARCHIVEDOCUMENTCALLBACK)	</tt><br>
<tt>	(		</tt><br>
<tt>	HARCHIVEDOCUMENT hArchDoc,		</tt><br>
<tt>	void</tt><tt>&nbsp;</tt><tt>*</tt><tt>pUserCtx</tt><br>
<tt>	);</tt><br>
<br>
hArchDoc is a handle to an Archive Document object which provides the caller with a few functions to implement common archiving and storage management operations. <br>
<br>
Callers should free the hArchDoc object when they are done with it using ArchiveDocumentDestroy. <br>
<br>
<b><font size="4" color="#000080">Encryption/Decryption Support</font></b><br>
<br>
Documents and their related attachments that are encrypted can be exported in their encrypted form and later returned to a notes database without fidelity loss. It is possible to access the non-encrypted parts of a document (sender, recipients for example) but the encrypted portions remain inaccessible and can only be transferred to and from a database in their encrypted state. <br>
<br>
It is possible to decrypt documents and attachments using ArchiveExportDatabase and passing a non-NULL KFHANDLE,  but the resulting exported document cannot be restored to a database. The most likely scenario for utilizing this decryption method is when the mail journal is used as a source for archiving common parts of a message (for example body item and attachments). These parts can be re-assembled into a complete document that may have originated from a users mail file for example.  <br>
<br>
<b><font size="5" color="#000080">Archive Document</font></b><br>
<br>
The ArchiveDocument abstraction gives users of the API the ability to access the archived data to produce textual renderings of selected fields and optimize storage by allowing a document to be decomposed into parts.<br>
 <br>
Callers are passed an ArchiveDocument handle via the ARCHIVEDOCUMENTCALLBACK of ArchiveExportDatabase (example below in section Database Level Export) . One can also create an ArchiveDocument from a previously exported document using the ArchiveDocumentImport function:<br>
<br>
HARCHIVEDOCUMENT hArchDoc;<br>
ArchiveDocumentImport(NoteImportCallback, &amp;hArchDoc);<br>
<br>
<b><font size="4" color="#000080">Extracting/Inserting Items</font></b><br>
<br>
Items can be extracted from an ArchiveDocument before it is exported. A placeholder is left in the export stream to ensure that the document is complete before attempting to restore it to a database. The data format of the extracted item is internal but it can be compared to previously extracted items from other documents for equality.  If there are multiple items with the same name, all of the items are concatenated to a single data stream and extracted. <br>
<br>
Extracting:<br>
<tt>// Define a program context struct</tt><br>
<tt>typedef struct {</tt><br>
<tt>	FILE *bodyfile;	</tt><br>
<tt>} CTX;</tt><br>
<tt>// </tt><br>
<tt></tt><br>
<tt>CTX myctx;</tt><br>
<tt>DWORD StreamLen;</tt><br>
<tt>// Create a file to accept the data</tt><br>
<tt>myctx.bodyfile = fopen(body.dat, wb);</tt><br>
<br>
<tt>// Extract the item named body from the archive</tt><br>
<tt>// document. </tt><br>
<tt>ArchiveDocumentExtractItem(hArchDoc, Body, strlen(Body), ItemExtractCallback, &amp;myctx);</tt><br>
<br>
<tt></tt><br>
<br>
<tt>}</tt><br>
<br>
<tt>// The callback function that accepts the data from</tt><br>
<tt>// ArchiveDocumentExtractItem</tt><br>
<tt>STATUS far PASCAL ItemExtractCallback(const BYTE *Buffer, DWORD BufLen, BOOL bLastBuffer, STATUS retError, void *pUserCtx)</tt><br>
<tt>{</tt><br>
<tt>CTX *pMyCtx = (CTX *) pUserCtx;</tt><br>
<tt>// If retError is non-zero, it indicates that there was</tt><br>
<tt>//internal error in processing. </tt><br>
<tt>if(retError)</tt><br>
<tt>	{</tt>
<ul>
<ul><tt>fclose(pMyCtx-&gt;bodyfile);</tt></ul>
</ul>
<tt>	return retError;</tt><br>
<tt>	}</tt><br>
<tt>fwrite(Buffer, BufLen, 1, pMyCtx-&gt;bodyfile);</tt><br>
<tt>if(bLastBuffer)</tt><br>
<tt>	fclose(pMyCtx-&gt;bodyfile);</tt><br>
<tt>}</tt><br>
<br>
Inserting:<br>
<tt>&nbsp;{</tt><br>
<tt>CTX ctx;</tt><br>
<tt>// Open the file where the body item was stored</tt><br>
<tt>ctx-&gt;bodyfile = fopen(body.dat, rb);</tt><br>
<br>
<tt>// Create the archive document from its serialized form</tt><br>
<tt>// See samples for more details on importing</tt><br>
<tt>ArchiveDocumentImport(0, NoteImportCallback, pCtx, &amp;hArchDoc);</tt><br>
<br>
<tt>// Put the body field back</tt><br>
<tt>// Note that the name of the item is stored</tt><br>
<tt>// in the extracted item data so it does not </tt><br>
<tt>// need to be specified. </tt><br>
<tt>ArchiveDocumentInsertItem(hArchDoc, ItemInsertCallback, &amp;ctx);</tt><br>
<br>
<tt>fclose(ctx-&gt;bodyfile);</tt><br>
<br>
<tt>}</tt><br>
<br>
<tt>//The callback function that ArchiveDocumentInsertItem</tt><br>
<tt>// will use to read data </tt><br>
<tt>DWORD far PASCAL ItemInsertCallbackCallback(BYTE *pBuffer, DWORD MaxToRead, void *pUserCtx)</tt><br>
<tt>{</tt><br>
<tt>CTX *pCtx = (CTX *)pUserCtx;</tt><br>
<tt>fread(pBuffer, MaxToRead, 1, pCtx-&gt;bodyfile);</tt><br>
<tt>}</tt><br>
<br>
<b><font size="4" color="#000080">Text Conversion</font></b><br>
<br>
It is possible to convert items of an Archive Document to text (for supported types see NSFItemConvertToText). As well, all MIME subtypes of type text (i.e text/plain, text/html)  are returned when an item contains MIME.<br>
See ArchiveDocumentGetText in the API reference for details. <br>
<br>
<b><font size="4" color="#000080">Importing Documents</font></b><br>
<br>
There are two functions provided for returning an exported document back to the Notes environment. ArchiveRestoreDocument writes a note and its related attachments to the caller-specified database replacing any note that may currently exist with the same UNID. ArchiveRestoreDocumentToNote returns the exported note data to an open note supplied by the caller. It does not restore attachments and thus care needs to be taken to ensure that either the note is not saved to the database or attachments are restored and references to attachments in the note are adjusted accordingly. <br>
<br>
Restoration happens in two steps. First the ArchiveDocument must be imported from its external storage (vendor specific):<br>
<br>
<tt>HARCHIVEDOCUMENT hArchDoc</tt><br>
<tt>// Create an archive document from its serialized format</tt><br>
<tt>ArchiveDocumentImport(0, NoteImportCallback, pUserCtx, &amp;hArchDoc)</tt><br>
<br>
Then ArchiveRestoreDocument is called to return the document and its attachments to the database. <br>
<tt>// Pass the imported ArchiveDocument to </tt>ArchiveRestoreDocument<tt>&nbsp;</tt><br>
<tt>STATUS far PASCAL </tt>ArchiveRestoreDocument<tt>(	</tt><br>
<tt>						 	hDb,</tt><br>
<tt>						0,// No flags	</tt><br>
<tt>						hArchDoc, &nbsp;	</tt><br>
<tt>						AttachImportCallback,	</tt><br>
<tt>						pUserCtx,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 					&amp;hNote);</tt><br>
<br>
Callers pass a handle to the target database and a pointer to a callback function that will be used to stream attachment data back to the database. The imported document will replace any document with the same UNID that exists in the target database. <br>
<br>
See the samples for more details on importing documents. <br>
<br>
<b><font size="5" color="#000080">Import/Export fidelity</font></b><br>
<br>
A note that is exported by ArchiveExportDatabase is restored to a database exactly as it existed when it was export with a few exceptions. There are a few fields that are updated by NSF internals that must change whenever a note is written to a database. These are $Revisions and $UpdatedBy. Signatures however, are preserved as is all rich text formatting.<br>
<br>
<b><font size="5" color="#000080">Trace/Debug</font></b><br>
<br>
The archiving functions have the ability to output trace information to the file specified in the DEBUG_OUTFILE notes ini setting. Tracing is enabled via the LOG_ARCHSVC notes ini variable. There are 3 flags that enable various aspects of tracing:<br>
1  	Enables tracing on all error returns so that callers can see the origin of a low level API error. <br>
2 - 	Enables the debug dump of key data structures during the export/import process.<br>
4 -	Logs the entry/exit of all archiving service functions along with argument and return values. This will help support pinpoint the cause of any errors that may occur. <br>
         <br>
Flags can be combined to yield the desired amount of trace information.
---
