##### Chapter 15-1
##### Domino Canonical Format

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
C API programs that run on non-Intel based platforms such as Macintosh and UNIX must convert certain types of data between host-specific format and Domino canonical format when accessing item data. This chapter explains when and how to perform this conversion.<br>
<br>
C API programs for Windows do not need to perform host/canonical conversion. However, all API programs should perform host/canonical conversion because it makes the code more portable and does not increase the complexity of the code significantly. API programs for Windows can perform host/canonical conversion with no adverse side effects.<br>
<br>
<br>
<b><font size="5" color="#000080">Audience</font></b><br>
<br>
You should read this chapter if:<br>

<ol type="1">
<li>You develop or plan to develop API programs for any platform other than Windows
<li>You are porting or plan to port API programs from OS/2 or Windows to any non-Intel platform, such as Unix.
<li>You would like to make your API programs portable to other platforms.<br>
</ol>
<br>
<b><font size="5" color="#000080">Domino Canonical Format</font></b><br>
<br>
Domino canonical format is defined as Intel 8086 byte ordering with no pad bytes<i>.</i><br>
<br>
Domino and Notes store all data on disk in Domino canonical format. Domino and Notes also transmit all data over network communications links in Domino canonical format. This way, Domino running on one platform can communicate transparently with Domino or Notes running on a different platform. Since all NSF files have the same binary format regardless of the platform on which the file was created, a UNIX server (for example) can read an .NSF file created on a Windows workstation. <br>
<br>
Generally, Domino insulates API programs from the details of canonical format. However, for certain data types, portable API programs must convert from host to canonical format before writing data to a Domino database and convert from canonical to host format after reading data from a Domino database.<br>
<br>
<br>
<b><font size="5" color="#000080">Data Types that Require Conversion</font></b><br>
<br>
The following data types require conversion:<br>
<br>
TYPE_COMPOSITE<br>
TYPE_COLLATION<br>
TYPE_OBJECT<br>
TYPE_VIEW_FORMAT<br>
TYPE_ICON<br>
TYPE_SIGNATURE<br>
TYPE_SEAL<br>
TYPE_SEALDATA<br>
TYPE_SEAL_LIST<br>
TYPE_WORKSHEET_DATA<br>
TYPE_USERDATA<br>
TYPE_QUERY<br>
TYPE_ACTION<br>
TYPE_ASSISTANT_INFO<br>
TYPE_VIEWMAP_DATASET<br>
TYPE_VIEWMAP_LAYOUT<br>
TYPE_CALENDAR_FORMAT<br>
<br>
For all other data types, the NSF subsystem performs the conversion automatically. <br>
<br>
For example, let's say that the following structure is to be written out to an item of TYPE_COMPOSITE:<br>
<br>
<tt>typedef struct {</tt><br>
<tt>&nbsp; &nbsp; WORD &nbsp; &nbsp;mem1;</tt><br>
<tt>&nbsp; &nbsp; DWORD mem2;</tt><br>
<tt>} CDSTRUCT;</tt><br>
<tt>...</tt><br>
<br>
<tt>CDSTRUCT DNStruct;</tt><br>
<br>
On a UNIX, the mem2 member of DNStruct is aligned on a DWORD boundary.  If you do not convert this structure to canonical format when copying it to the item buffer that is to be written to disk, then when Domino or Notes attempts to read this item, there will be two nonsense bytes where Domino expects to find the mem2 data.<br>
<br>
<br>
<b><font size="5" color="#000080">When to Convert</font></b><br>
<br>
Given item data of one of the above types:<br>

<ul type="disc">
<li>Portable API programs must convert the item data to canonical format before calling NSFItemAppend or any function that appends item data to a note.
<li>After calling NSFItemInfo or any equivalent function to read item data from a note, the API program must convert the item data from canonical format to host format before accessing the item data.</ul>
<br>
API programs generally do not need to perform host/canonical conversion when using higher-level functions such as NSFItemGetText, NSFItemSetText, or NSFItemGetNumber, which do not manipulate any of the data types that require conversion. Conversion is also unnecessary when using any of the &quot;Easy&quot; rich text routines, such as CompoundTextAddText.<br>
<br>
Do not convert data stored in an item that is not one of the aforementioned data types.  For example, do not convert a LIST structure stored in an item of TYPE_NOTELINK.  Do convert a LIST structure stored in an item of TYPE_COMPOSITE.<br>
<br>
<b><font size="5" color="#000080">How to Convert</font></b><br>
<br>
The API provides three functions that allow API programs to convert data between host-specific format and Domino canonical format:<br>

<ul type="disc">
<li>ODSReadMemory - Converts from Domino canonical format to host-specific format 
<li>ODSWriteMemory - Converts from host-specific format to Domino canonical format
<li>ODSLength - Gets the length, in bytes, of a data structure in Domino canonical format</ul>
<br>
ODSReadMemory converts Domino data structures from Domino canonical format to machine-specific format and writes the results into a variable or memory buffer provided by the caller. Portable API programs use ODSReadMemory after reading item data of one of the types listed above and before accessing that data.<br>
<br>
ODSWriteMemory converts Domino data structures from machine-specific format to Domino Canonical format and writes the results into a memory buffer provided by the caller. Portable API programs use ODSWriteMemory to prepare item data of one of the types listed above before appending the data to a note.<br>
<br>
ODSLength returns the length, in bytes, of a data structure in Domino canonical format. Use this function when calculating the buffer size needed to contain data structures converted to Domino canonical format and when initializing the Length members of CD record header structures.<br>
<br>
NOTE: These ODS functions are supported on all platforms.  We recommend that you include these functions in the appropriate places in all API code to ensure that the code is platform-independent.<br>
<br>
The <i>HCL C API for Domino and Notes Reference </i>provides detailed information about these functions.<br>
<br>
These ODS functions perform different actions depending on the platform on which the API program is running. If your API program calls ODS functions in the proper  places, it will be portable to both Intel and non-Intel architecture machines. On Intel architecture machines, these ODS functions are not strictly necessary, but if used properly will do no harm.<br>
<br>
<br>
<b><font size="5" color="#000080">Example Using ODSWriteMemory</font></b><br>
<br>
The sample API program DYNAMIC shows how to use ODSWriteMemory to convert Domino data structures from host format to canonical format.<br>
<br>
The code fragment below adds a rich text field to a note. It creates the rich text data by setting up a buffer that consists of a series of CD records.  <br>
<br>
In order to create each CD record, DYNAMIC needs certain data structures. For example, it needs a variable of type CDPARAGRAPH. It defines these data structures as local variables. Note that when initializing the data structures, DYNAMIC sets the Length member of the record header to the ODS length of the resulting CD record. For example,<br>

<ul>
<ul><tt><font size="2">para.Header.Length = (BYTE) ODSLength( _CDPARAGRAPH );</font></tt></ul>
</ul>
<br>
After initializing each data structure, it converts the data structure from host format to Domino canonical format when appending it to the buffer. The resulting buffer is entirely in Domino canonical format. The code then creates a rich text field by calling NSFItemAppend to append the buffer to a note. 
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example Using ODSWriteMemory</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
</font></tt><tt><font size="2">BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *rt_field; &nbsp; /* allocated rich-text field */<br>
BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *buff_ptr; &nbsp; /* position in allocated memory */<br>
CDPABDEFINITION pabdef; &nbsp; &nbsp; /* rich-text paragraph style */<br>
CDPARAGRAPH &nbsp; &nbsp; para; &nbsp; &nbsp; &nbsp; /* rich-text paragraph header */<br>
CDPABREFERENCE &nbsp;ref; &nbsp; &nbsp; &nbsp; &nbsp;/* rich-text style reference */<br>
CDTEXT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;cdtext; &nbsp; &nbsp; /* rich-text text header */<br>
char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szString1[] = &quot;Hello world... &quot;;<br>
char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szString2[] = &quot;So long world &quot;;<br>
WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wString1Len = strlen( szString1 );<br>
WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wString2Len = strlen( szString2 );<br>
FONTIDFIELDS &nbsp; *pFontID; &nbsp; &nbsp;/* font definitions in text header */<br>
DWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rt_size; &nbsp; &nbsp;/* size of rich-text field */</font></tt><br>
<br>
<tt><font size="2">/* ... steps missing ... */</font></tt><br>
<br>
<tt><font size="2">rt_field = (BYTE *) malloc ( wBuffLen );</font></tt><br>
<br>
<tt><font size="2">/* Keep a pointer to our current position in the buffer. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
buff_ptr = rt_field;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
/* Initialize a CDPABDEFINITION structure.*/</font></tt><br>
<br>
<tt><font size="2">pabdef.Header.Signature = SIG_CD_PABDEFINITION;<br>
pabdef.Header.Length = ODSLength( _CDPABDEFINITION );<br>
pabdef.PABID = PARA_STYLE_ID;<br>
pabdef.JustifyMode = JUSTIFY_CENTER;<br>
pabdef.LineSpacing = DEFAULT_LINE_SPACING;<br>
pabdef.ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;<br>
pabdef.ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;<br>
pabdef.LeftMargin = DEFAULT_LEFT_MARGIN;<br>
pabdef.RightMargin = DEFAULT_RIGHT_MARGIN;<br>
pabdef.FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;<br>
pabdef.Tabs = DEFAULT_TABS;<br>
pabdef.Tab[0] = DEFAULT_TAB_INTERVAL;<br>
pabdef.Flags = 0;</font></tt><br>
<br>
<tt><font size="2">/* Call ODSWriteMemory to convert the CDPABDEFINITION structure to <br>
 &nbsp; Domino canonical format and write the converted structure into<br>
 &nbsp; the buffer at location buff_ptr. This advances buff_ptr to the<br>
 &nbsp; next byte in the buffer after the canonical format strucure.<br>
 */<br>
 &nbsp; &nbsp;<br>
ODSWriteMemory( &amp;buff_ptr, _CDPABDEFINITION, &amp;pabdef, 1 );</font></tt><br>
<br>
<tt><font size="2">/* Put a paragraph header in the field. */<br>
 &nbsp; <br>
para.Header.Signature = SIG_CD_PARAGRAPH;<br>
para.Header.Length = (BYTE) ODSLength( _CDPARAGRAPH );</font></tt><br>
<br>
<tt><font size="2">ODSWriteMemory( &amp;buff_ptr, _CDPARAGRAPH, &amp;para, 1 );<br>
 &nbsp; &nbsp;<br>
/* Put a paragraph reference block in the field.*/</font></tt><br>
<br>
<tt><font size="2">ref.Header.Signature = SIG_CD_PABREFERENCE;<br>
ref.Header.Length = (BYTE) ODSLength( _CDPABREFERENCE );<br>
ref.PABID = PARA_STYLE_ID;<br>
 <br>
ODSWriteMemory( &amp;buff_ptr, _CDPABREFERENCE, &amp;ref, 1 );</font></tt><br>
<br>
<tt><font size="2">/* Add the CDTEXT record to the field. A CDTEXT record consists<br>
 &nbsp; of a CDTEXT structure followed by a run of text. Initialize the<br>
 &nbsp; CDTEXT structure by filling in the signature and the length. <br>
 &nbsp; The CDTEXT structure also contains the font information that<br>
 &nbsp; controls how Domino displays this first run of text. <br>
 */</font></tt><br>
<br>
<tt><font size="2">cdtext.Header.Signature = SIG_CD_TEXT;<br>
cdtext.Header.Length = ODSLength( _CDTEXT ) + wString1Len ;</font></tt><br>
<br>
<tt><font size="2">pFontID = (FONTIDFIELDS *) &amp;(cdtext.FontID);<br>
 &nbsp; &nbsp;<br>
pFontID-&gt;Face = FONT_FACE_SWISS;<br>
pFontID-&gt;Attrib = ISBOLD;<br>
pFontID-&gt;Color = FONT_COLOR_BLUE;<br>
pFontID-&gt;PointSize = 24;</font></tt><br>
<br>
<tt><font size="2">ODSWriteMemory( &amp;buff_ptr, _CDTEXT, &amp;cdtext, 1 );</font></tt><br>
<br>
<tt><font size="2">/* Write the actual characters of this first text run to the buffer. <br>
 &nbsp; Since the run of text may contain embedded null characters, use <br>
 &nbsp; memcpy, not strcpy. No need to terminate the run of text with a <br>
 &nbsp; null because the Header.Length member of the CDTEXT structure <br>
 &nbsp; specifies the length explicitly.<br>
 */</font></tt><br>
<br>
<tt><font size="2">memcpy( (char *)buff_ptr, szString1, wString1Len );<br>
buff_ptr += wString1Len;<br>
 &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">/* We are done filling the buffer with CD records. Now append the <br>
 &nbsp; buffer to the note as a rich text field. First find the size of <br>
 &nbsp; the buffer. Then add the rich-text field to the note by calling <br>
 &nbsp; NSFItemAppend. NSFItemAppend copies the data out of the buffer <br>
 &nbsp; specified by rt_field. Therfore, after calling NSFItemAppend, we <br>
 &nbsp; can free the buffer.</font></tt><br>
<tt><font size="2">&nbsp;*/</font></tt><br>
<br>
<tt><font size="2">rt_size = (DWORD)(buff_ptr - rt_field);</font></tt><br>
<br>
<tt><font size="2">error = NSFItemAppend( note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;RICH_TEXT&quot;, strlen(&quot;RICH_TEXT&quot;),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_COMPOSITE,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;rt_field, rt_size );</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Example Using ODSReadMemory</font></b><br>
<br>
The sample API program DUMPFONT shows how to use ODSReadMemory to convert Domino data structures from canonical format to host format. The code fragment below uses ODSReadMemory to convert a font table from canonical format to host format before printing the contents of the font table to the screen.<br>
<br>
A font table is an item of TYPE_COMPOSITE. It consists of a CDFONTTABLE structure followed by one or more CDFACE structures. When an API program reads a CDFONTTABLE or CDFACE structure from the NSF subsystem, these structures are in canonical format. API programs must convert these canonical format data structures to host-specific format before attempting to access the members of the structures. The code below uses ODSReadMemory to perform this conversion.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Example Using ODSReadMemory</b></td></tr>
</table>
<tt><font size="2">/************************************************************************<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;FUNCTION: &nbsp; ProcessOneNote<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
*************************************************************************/</font></tt><br>
<tt><font size="2">STATUS LNPUBLIC ProcessOneNote( void * phDB, DWORD NoteID )<br>
{<br>
 &nbsp; &nbsp;DBHANDLE &nbsp; &nbsp;hDB;<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error;<br>
 &nbsp; &nbsp;NOTEHANDLE &nbsp;hNote;<br>
 &nbsp; &nbsp;BLOCKID bhThisItem;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp;wType;<br>
 &nbsp; &nbsp;BLOCKID bhValue;<br>
 &nbsp; &nbsp;DWORD &nbsp; dwLength;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; hDB = *( (DBHANDLE *)phDB );</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFNoteOpen( hDB, NoteID, 0, &amp;hNote))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot;Error: unable to open note.\n&quot; );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return( ERR(error) );<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* &nbsp;Look for the &quot;$Fonts&quot; field within this note. */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; error = NSFItemInfo( hNote, ITEM_NAME_FONTS, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strlen (ITEM_NAME_FONTS), <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;bhThisItem, &nbsp;/* Item BLOCKID */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;wType, &nbsp; &nbsp; &nbsp; /* Type &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;bhValue, &nbsp; &nbsp; /* Value BLOCKID */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&amp;dwLength); &nbsp; /* Value length */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* If no font table, just return.*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (ERR(error) == ERR_ITEM_NOT_FOUND)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFNoteClose( hNote );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return NOERROR;<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;else if (error) &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot;Error: unable to access item %d.\n&quot;, ITEM_NAME_FONTS );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;NSFNoteClose( hNote );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return( ERR(error) );<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; EnumCompositeBuffer( bhValue, dwLength, PrintFontTable, NULL);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; NSFNoteClose( hNote );</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return NOERROR;<br>
}<br>
 <br>
/************************************************************************<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;FUNCTION: &nbsp; PrintFontTable<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC PrintFontTable( char &nbsp;*RecordPtr, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD &nbsp; RecordType, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DWORD &nbsp;RecordLength, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;void &nbsp;*Unused )<br>
{<br>
 &nbsp; &nbsp;void &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *pItemValue;<br>
 &nbsp; &nbsp;CDFONTTABLE &nbsp; &nbsp; cdFontTab;<br>
 &nbsp; &nbsp;CDFACE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;cdFace;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wIndex;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (RecordType != SIG_CD_FONTTABLE)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; /* EnumCompositeBuffer found a CD record in the &quot;$Fonts&quot; field<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;that is not of type SIG_CD_FONTTABLE. &nbsp;Unusual, but not fatal.<br>
 &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return NOERROR;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp;/* RecordPtr points to the item value in canonical format after the<br>
 &nbsp; &nbsp; &nbsp;datatype word. The item value starts with a CDFONTTABLE structure. <br>
 &nbsp; &nbsp; &nbsp;Call ODSReadMemory to convert this CDFONTTABLE to host format and<br>
 &nbsp; &nbsp; &nbsp;store it in cdFontTab. ODSReadMemory increments pItemValue to<br>
 &nbsp; &nbsp; &nbsp;point to the next byte in the input buffer after the CDFONTTABLE.<br>
 &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pItemValue = RecordPtr;<br>
 &nbsp; &nbsp;ODSReadMemory( &amp;pItemValue, _CDFONTTABLE, &amp;cdFontTab, 1 );</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; for (wIndex = 0; wIndex &lt; cdFontTab.Fonts; wIndex++)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;ODSReadMemory( &amp;pItemValue, _CDFACE, &amp;cdFace, 1 );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot; &nbsp; &nbsp;Font %d:\n&quot;, wIndex );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot; &nbsp; &nbsp; &nbsp; Face &nbsp; &nbsp;= %d\n&quot;, cdFace.Face );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot; &nbsp; &nbsp; &nbsp; Family &nbsp;= %d\n&quot;, cdFace.Family );<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf( &quot; &nbsp; &nbsp; &nbsp; Name &nbsp; &nbsp;= %s\n&quot;, cdFace.Name );<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return (NOERROR);<br>
}</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Side-by-Side Comparison</font></b><br>
<br>
The code fragments below show how part of the sample program DYNAMIC was modified in porting from Windows to Unix. The fragment on the left works only on Intel architecture platforms such as Windows. The fragment on the right is portable. It works on all platforms supported by Domino or Notes.
<table width="100%" border="0" cellspacing="0" cellpadding="0">
<tr valign="top"><td width="50%"><b>Example: DYNAMIC before porting to UNIX</b></td><td width="50%"><b>Example: DYNAMIC after porting to UNIX</b></td></tr>

<tr valign="top"><td width="50%"><tt><font size="2">BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *rt_field;</font></tt><br>
<tt><font size="2">BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *buff_ptr;</font></tt><br>
<tt><font size="2">CDPABDEFINITION &nbsp;*def;</font></tt><br>
<br>
<tt><font size="2">/* ... steps missing... */</font></tt><br>
<br>
<tt><font size="2">/* Add a CDPABDEFINITION.*/</font></tt><br>
<br>
<tt><font size="2">def = (CDPABDEFINITION *) buff_ptr;</font></tt><br>
<br>
<tt><font size="2">def-&gt;Header.Signature =</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; SIG_CD_PABDEFINITION;<br>
def-&gt;Header.Length = </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; sizeof(CDPABDEFINITION);<br>
</font></tt><br>
<tt><font size="2">def-&gt;PABID = 1;<br>
def-&gt;JustifyMode = JUSTIFY_CENTER;<br>
def-&gt;LineSpacing =	 &nbsp;DEFAULT_LINE_SPACING;<br>
def-&gt;ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;<br>
def-&gt;ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;<br>
def-&gt;LeftMargin = DEFAULT_LEFT_MARGIN;<br>
def-&gt;RightMargin = DEFAULT_RIGHT_MARGIN;<br>
def-&gt;FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;<br>
def-&gt;Tabs = DEFAULT_TABS;<br>
def-&gt;Tab[0] = DEFAULT_TAB_INTERVAL;<br>
def-&gt;Flags = 0;</font></tt><br>
<br>
<tt><font size="2">/* Advance the buffer pointer, so we know where to put the next object in <br>
the buffer. */</font></tt><br>
<br>
<tt><font size="2">buff_ptr += sizeof(CDPABDEFINITION);</font></tt></td><td width="50%"><tt><font size="2">BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *rt_field;<br>
BYTE &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; *buff_ptr;<br>
CDPABDEFINITION pabdef;</font></tt><br>
<br>
<tt><font size="2">/* .....steps missing ....*/</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">/* Init a CDPABDEFINITION*/</font></tt><br>
<br>
<tt><font size="2">pabdef.Header.Signature =</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; SIG_CD_PABDEFINITION;<br>
pabdef.Header.Length =</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; ODSLength( _CDPABDEFINITION );<br>
</font></tt><br>
<tt><font size="2">pabdef.PABID = PARA_STYLE_ID;<br>
pabdef.JustifyMode = JUSTIFY_CENTER;<br>
pabdef.LineSpacing =	 &nbsp;DEFAULT_LINE_SPACING;<br>
pabdef.ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;<br>
pabdef.ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;<br>
pabdef.LeftMargin = DEFAULT_LEFT_MARGIN;<br>
pabdef.RightMargin = DEFAULT_RIGHT_MARGIN;<br>
pabdef.FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;<br>
pabdef.Tabs = DEFAULT_TABS;<br>
pabdef.Tab[0] = DEFAULT_TAB_INTERVAL;<br>
pabdef.Flags = 0;</font></tt><br>
<br>
<tt><font size="2">/* Call ODSWriteMemory to convert the CDPABDEFINITION structure to <br>
 &nbsp; Domino canonical format and write the converted structure into<br>
 &nbsp; the buffer at location buff_ptr. This advances buff_ptr to the<br>
 &nbsp; next byte in the buffer after the canonical format structure.<br>
 */<br>
 &nbsp; &nbsp;<br>
ODSWriteMemory( &amp;buff_ptr, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; _CDPABDEFINITION, &amp;pabdef, 1 );</font></tt></td></tr>
</table>

---
