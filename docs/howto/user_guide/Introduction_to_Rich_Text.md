##### Chapter 7-1
##### Introduction to Rich Text

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Domino and Notes use rich text fields to store a variety of objects, including text, tables, document links, bitmaps, and OLE links. Rich text fields have several advantages over other types of fields:
<ul type="disc">
<li>Paragraphs in rich text can<font color="#FF0000"> </font>have mixed attributes, such as indenting, justification, and spacing
<li>Text in rich text can<font color="#FF0000"> </font>have mixed attributes such as font face, color, and point size
<li>A single rich text field can<font color="#FF0000"> </font>hold several megabytes of data</ul>
<br>
This chapter introduces the structure of rich text and explains how to access the individual CD records that constitute a rich text field. Later chapters explain the details of document links, OLE links, and other objects.<br>
<br>
<br>
<b><font size="5" color="#000080">Creating Rich Text</font></b><br>
 <br>
The HCL C API for Domino and Notes provides high-level and low-level ways to create rich text. The high-level way is simple but limited. The low-level way is complex but provides access to advanced features such as tables, pop-ups, and OLE links.<br>
<br>
<br>
<b><font size="4" color="#000080">High-Level Access to Rich Text</font></b><br>
<br>
The CompoundTextxxx family of C API functions provide a high-level way to create rich text. These functions implement an abstraction for rich text that allows C API code to treat a rich text field as an object. We refer to this rich text object as a &quot;compound text context.&quot; Use the functions below to create, delete, and manipulate compound text as an object:<br>

<ul>
<ul>CompoundTextCreate<br>
CompoundTextDefineStyle<br>
CompoundTextInitStyle<br>
CompoundTextAddText<br>
CompoundTextAddParagraph<br>
CompoundTextAddDocLink<br>
CompoundTextAddRenderedNote<br>
CompoundTextAssimilateItem<br>
CompoundTextAssimilateFile<br>
CompoundTextDiscard<br>
CompoundTextClose</ul>
</ul>
<br>
Use these high-level functions to create rich-text fields that contain text and document links. The text can<font color="#FF0000"> </font>have any type face or paragraph style. One advantage of these high-level functions is that C API programs that use them do not need to perform host/canonical conversion to be portable to platforms such as UNIX. <br>
<br>
For more information on these functions, see the <i>Reference.</i>For example usage, see the sample program EASYRICH.<br>
<br>
<br>
<b><font size="4" color="#000080">Low-Level Access to Rich Text</font></b><br>
<br>
To take advantage of the advanced features of rich text, such as tables, pop-ups, and OLE links, C API programs must access the individual CD records that constitute a rich text field.<br>
<br>
<br>
<b><font color="#000080">Low-Level Structure of Rich Text</font></b><br>
<br>
A rich text field in a note consists of one or more items<font color="#FF0000"> </font>of data type TYPE_COMPOSITE. A single rich text field may consist of multiple items of type TYPE_COMPOSITE, so long as all the items have the same name.<br>
<br>
The data in an item of<font color="#FF0000"> </font>type TYPE_COMPOSITE consists of a series of records called CD records. (&quot;CD&quot; stands for &quot;Compound Document&quot; or &quot;Composite Data.&quot;)<br>
<br>
To add an item of TYPE_COMPOSITE to a note, prepare a buffer that consists of a series of CD records, and then use NSFItemAppend to append this buffer to the note. The data in the buffer must be in Domino canonical format.<br>
<br>
NOTE: Some C API programs do not perform host/canonical conversion when accessing low-level structures in rich text. Canonical conversion is not strictly necessary for programs that run only on Intel-architecture platforms such as  Windows. However, source code that does not perform host/canonical conversion will not run on platforms such as UNIX. Source code that does perform host/canonical conversion will run on any platform supported by Domino and Notes. For more information on canonical format requirements, read the &quot;Domino Canonical Format&quot; chapter in this guide.
<ul>
<ul></ul>
</ul>
To prepare the buffer of CD records, initialize each CD structure in turn and then use ODSWriteMemory to convert each CD structure to Domino canonical format. Store the canonical format result in the buffer as the next CD record.<br>
<br>
Domino and Notes define many different types of CD records. The C API header file editods.h contains the type definitions for each CD structure.<br>
<br>
Every CD record begins with a header,<font color="#FF0000"> </font>which starts with a signature byte. The signature byte identifies the type of the header and the type of the CD record that follows.<br>
<br>
The three types of headers, defined in file ods.h, are BSIG, WSIG, and LSIG. Each header includes a length member, which specifies the entire length of the CD record, including the header. Code can use this length to offset from the start of one record to the start of the next record.<br>
<br>
NOTE:<b> </b>In a Composite Data buffer, every CD record must begin on an even byte boundary. If the length member of a given CD record is odd, the next CD record begins length+1 bytes after the start of the given record.<br>
<br>
Also note that you initialize the length member of a CD record header with the ODSLength of the CD record, not the &quot;sizeof&quot; the data structure. The length member must specify the length of the record in Domino canonical format.<br>
<br>
Rich text must satisfy a set of size limits.  First, the total size of any CD record is limited by the size of the length field in the header.  For a record with a byte signature (BSIG), the total size is limited to 254 bytes.  For a record with a word signature, the total size is limited to approximately 64k.  The actual limit is specified by the constant MAXONESEGSIZE.<br>
<br>
Second, the size of any rich text item must be less than MAXONESEGSIZE.  If a rich text item exceeds this size, it must be stored as separate items with the same name.  Domino or Notes will assemble these items in order when the records are read from the file.<br>
<br>
Third, the total size of a paragraph of rich text is also limited to MAXONESEGSIZE.  However, large elements such as bitmaps, metafiles, and file attachments are not included in the stored size of a paragraph, and are not counted in this limit.  When creating rich text, CDPARAGRAPH records must be inserted to ensure that the paragraph data such as CDTEXT records does not exceed this limit.<br>
<br>
Finally, the size of a rich text record stored on disk may be different from the storage required when Domino or Notes manipulates the records internally.  Additional storage may be used for information that only applies to the Notes user interface.  To allow for this expansion, a practical limit on the size of a rich text item or a paragraph is approximately 40k.<br>
<br>
The C API provides the function EnumCompositeBuffer to simplify parsing a buffer of CD records.<br>
<br>
<br>
<b><font color="#000080">Example</font></b><br>
<br>
The data in a simple rich-text field containing text consist of a series of four CD records.<br>

<ul>
<ul>CDPABDEFINITION<br>
CDPARAGRAPH<br>
CDPABREFERENCE<br>
CDTEXT</ul>
</ul>
<br>
A CDPABDEFINITION structure defines the &quot;style&quot; of a paragraph. This structure contains fields in which to specify margins, line justification, tab stops, and other style attributes. Each CDPABDEFINITION has a unique ID. Subsequent paragraphs in the rich text field use this ID to identify the CDPABDEFINITION that defines its style. Each CDPABDEFINITION structure may be used by many paragraphs in the rich text field.<br>
<br>
A CDPARAGRAPH structure marks the start of each new paragraph. Rich-text fields are composed of one or more paragraphs.<br>
<br>
CDPABREFERENCE structures specify which paragraph style is to be used in the current paragraph. If a CDPABREFERENCE is not specified for a paragraph, the style of the previous paragraph is used.<br>
<br>
NOTE: CDPABREFERENCE structures only refer to styles that have already been defined. Forward references to style definitions are not allowed. While it is not required, we recommend that you define all styles at the beginning of the buffer so you can reference the styles as needed.<br>
<br>
A CDTEXT structure defines the start of a run of text. The FontID member of CDTEXT specifies the color, size, and font of this run of text. The actual text string is appended to the buffer immediately following the CDTEXT structure.<br>
<br>
 <br>
<b><font size="5" color="#000080">Writing A Rich Text Field in a Document</font></b><br>
<br>
This section examines the sample program DYNAMIC. DYNAMIC creates a document in a database and appends several fields to the document, including a rich text field. <br>
<br>
The code fragments below create a rich text field in a document by setting up a buffer that contains four CD records. It creates each CD record by initializing a data structure and then converting the structure to Domino canonical format. It stores the converted canonical data in the buffer. After preparing the buffer, it calls NSFItemAppend to append the buffer to the document as the data value of the rich text field.<br>
<br>
The diagram below depicts the data in the buffer created by the code fragments. The diagram is not drawn to scale. The sizes of the structures in a rich-text field vary considerably. <br>
<br>

<table border="1">
<tr valign="top"><td width="552">Paragraph Definition - CDPABDEFINITION</td></tr>

<tr valign="top"><td width="552">Paragraph Header - CDPARAGRAPH</td></tr>

<tr valign="top"><td width="552">Paragraph Reference - CDPABREFERENCE </td></tr>

<tr valign="top"><td width="552">Text Header - CDTEXT</td></tr>

<tr valign="top"><td width="552">&quot;Hello World... &quot;</td></tr>
</table>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating a CDPABDEFINITION Structure in Sample Program DYNAMIC</b></td></tr>
</table>
<tt><font size="2">&nbsp; WORD &nbsp; &nbsp; </font></tt><tt><i><font size="2">&nbsp; </font></i></tt><tt><font size="2">wBuffLen; &nbsp;/* required buffer length */<br>
 &nbsp;BYTE &nbsp; &nbsp; &nbsp;*rt_field; &nbsp;/* allocated rich-text field */<br>
 &nbsp;BYTE &nbsp; &nbsp; &nbsp;*buff_ptr; &nbsp;/* position in allocated memory */<br>
 &nbsp;CDPABDEFINITION pabdef; &nbsp; /* rich-text paragraph style */</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* ... steps missing ... */</font></tt><br>
<br>
<tt><font size="2">&nbsp; rt_field = (BYTE *) malloc ( wBuffLen );</font></tt><br>
<br>
<tt><font size="2">&nbsp; if( rt_field == (BYTE *)NULL )<br>
 &nbsp;{<br>
 &nbsp; &nbsp;API_RETURN (NOERROR);<br>
 &nbsp;} &nbsp;<br>
 &nbsp; &nbsp; &nbsp; <br>
 &nbsp;/* Keep a pointer to our current position in the buffer. */<br>
 &nbsp; &nbsp; &nbsp; <br>
 &nbsp;buff_ptr = rt_field;<br>
 &nbsp; &nbsp; &nbsp; <br>
 &nbsp;/* Initialize a CDPABDEFINITION structure.We use all defaults, <br>
 &nbsp; &nbsp;except for centered justification. <br>
 &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; pabdef.Header.Signature = SIG_CD_PABDEFINITION;<br>
 &nbsp;pabdef.Header.Length = ODSLength( _CDPABDEFINITION );<br>
 &nbsp;pabdef.PABID = PARA_STYLE_ID;<br>
 &nbsp;pabdef.JustifyMode = JUSTIFY_CENTER;<br>
 &nbsp;pabdef.LineSpacing = DEFAULT_LINE_SPACING;<br>
 &nbsp;pabdef.ParagraphSpacingBefore = DEFAULT_ABOVE_PAR_SPACING;<br>
 &nbsp;pabdef.ParagraphSpacingAfter = DEFAULT_BELOW_PAR_SPACING;<br>
 &nbsp;pabdef.LeftMargin = DEFAULT_LEFT_MARGIN;<br>
 &nbsp;pabdef.RightMargin = DEFAULT_RIGHT_MARGIN;<br>
 &nbsp;pabdef.FirstLineLeftMargin = DEFAULT_FIRST_LEFT_MARGIN;<br>
 &nbsp;pabdef.Tabs = DEFAULT_TABS;<br>
 &nbsp;pabdef.Tab[0] = DEFAULT_TAB_INTERVAL;<br>
 &nbsp;pabdef.Flags = 0;</font></tt><br>
<br>
<tt><font size="2">&nbsp; /* Call ODSWriteMemory to convert the CDPABDEFINITION structure to <br>
 &nbsp; &nbsp;Domino canonical format and write the converted structure into<br>
 &nbsp; &nbsp;the buffer at location buff_ptr. This advances buff_ptr to the<br>
 &nbsp; &nbsp;next byte in the buffer after the canonical format strucure.<br>
 &nbsp; */<br>
 &nbsp;<br>
 &nbsp;ODSWriteMemory( &amp;buff_ptr, _CDPABDEFINITION, &amp;pabdef, 1 );</font></tt><br>
<br>
<br>
This code dynamically allocates a buffer in which to build the rich-text item. It then fills in all the fields of the CDPABDEFINITION structure. The PABID member is the unique identifier for this style definition. In the above code, this parameter is set to 1. If other CDPABDEFINITION structures are defined in the same rich-text field, each one must have its PABID member set to a unique value.<br>
<br>
After setting all members of the structure, the code calls ODSWriteMemory to convert the CDPABDEFINITION structure to Domino canonical format and store the result in the allocated buffer. ODSWriteMemory advances the buff_ptr to point to the next byte in the allocated buffer after the converted CDPABDEFINITION record.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating a CDPARAGRAPH Structure in Sample Program DYNAMIC </b></td></tr>
</table>
<tt>&nbsp; &nbsp; CDPARAGRAPH &nbsp; &nbsp; para; &nbsp; &nbsp; &nbsp; /* rich-text paragraph header */</tt><br>
<br>
<tt>&nbsp; &nbsp; /* Put a paragraph header in the field. */<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;para.Header.Signature = SIG_CD_PARAGRAPH; <br>
 &nbsp; &nbsp;para.Header.Length = (BYTE) ODSLength( _CDPARAGRAPH );</tt><br>
<br>
<tt>&nbsp; &nbsp; ODSWriteMemory( &amp;buff_ptr, _CDPARAGRAPH, &amp;para, 1 );<br>
</tt>    <br>
<br>
This code initializes the CDPARAGRAPH structure and then converts it to Domino canonical format, storing the result in the buffer. ODSWriteMemory advances the buffer pointer to the next available byte in the buffer.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating a CDPABREFERENCE Structure in Sample Program DYNAMIC </b></td></tr>
</table>
<tt>&nbsp; &nbsp; </tt><tt>CDPABREFERENCE &nbsp; &nbsp; ref;</tt><br>
<br>
<tt>&nbsp; &nbsp; /* Put a paragraph reference block in the field. Specify <br>
 &nbsp; &nbsp; &nbsp; PARA_STYLE_ID so that this paragraph uses the style <br>
 &nbsp; &nbsp; &nbsp; defined above.<br>
 &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; ref.Header.Signature = SIG_CD_PABREFERENCE;<br>
 &nbsp; &nbsp;ref.Header.Length = (BYTE) ODSLength( _CDPABREFERENCE );<br>
 &nbsp; &nbsp;ref.PABID = PARA_STYLE_ID;<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;ODSWriteMemory( &amp;buff_ptr, _CDPABREFERENCE, &amp;ref, 1 );</tt><br>
<br>
<br>
This code initializes the CDPABREFERENCE structure and then converts it to Domino canonical format, storing the result in the buffer. ODSWriteMemory advances the buffer pointer to the next available byte.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating Two CDTEXT Structures in Sample Program DYNAMIC </b></td></tr>
</table>
<tt>&nbsp; &nbsp; CDTEXT &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;cdtext; &nbsp; &nbsp; /* rich-text text header */<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szString1[] = &quot;Hello world... &quot;;<br>
 &nbsp; &nbsp;WORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;wString1Len = strlen( szString1 );<br>
 &nbsp; &nbsp;FONTIDFIELDS &nbsp; *pFontID; &nbsp; &nbsp;/* font definitions in text header */</tt><br>
<br>
<tt>&nbsp; &nbsp; /* Add the CDTEXT record to the field. A CDTEXT record consists<br>
 &nbsp; &nbsp; &nbsp; of a CDTEXT structure followed by a run of text. Initialize the<br>
 &nbsp; &nbsp; &nbsp; CDTEXT structure by filling in the signature and the length. <br>
 &nbsp; &nbsp; &nbsp; The CDTEXT structure also contains the font information that<br>
 &nbsp; &nbsp; &nbsp; controls how Domino or Notes displays this first run of text. <br>
 &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; cdtext.Header.Signature = SIG_CD_TEXT;<br>
 &nbsp; &nbsp;cdtext.Header.Length = ODSLength( _CDTEXT ) + wString1Len ;</tt><br>
<br>
<tt>&nbsp; &nbsp; pFontID = (FONTIDFIELDS *) &amp;(cdtext.FontID);<br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;pFontID-&gt;Face = FONT_FACE_SWISS;<br>
 &nbsp; &nbsp;pFontID-&gt;Attrib = ISBOLD;<br>
 &nbsp; &nbsp;pFontID-&gt;Color = NOTES_COLOR_BLUE;<br>
 &nbsp; &nbsp;pFontID-&gt;PointSize = 24;</tt><br>
<br>
<tt>&nbsp; &nbsp; ODSWriteMemory( &amp;buff_ptr, _CDTEXT, &amp;cdtext, 1 );</tt><br>
<br>
<tt>&nbsp; &nbsp; /* Write the actual characters of this first text run to the buffer. <br>
 &nbsp; &nbsp; &nbsp; Since the run of text may contain embedded null characters, use <br>
 &nbsp; &nbsp; &nbsp; memcpy, not strcpy. No need to terminate the run of text with a <br>
 &nbsp; &nbsp; &nbsp; null because the Header.Length member of the CDTEXT structure <br>
 &nbsp; &nbsp; &nbsp; specifies the length explicitly.<br>
 &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; memcpy( (char *)buff_ptr, szString1, wString1Len );<br>
 &nbsp; &nbsp;buff_ptr += wString1Len;<br>
</tt>    <br>
<br>
This code fragment adds a CDTEXT record to the buffer. A CDTEXT record consists of a CDTEXT structure followed by a run of text characters. The CDTEXT portion of the record defines certain attributes of the text, including the font face, color, and point size and must be converted to Domino canonical format. Immediately following this structure, we append the run of text characters that will be displayed with the specified attributes. The run of characters is not converted to canonical format.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Appending the Rich</b><font color="#FF0000"> </font><b>Text Buffer to the Note in Sample Program DYNAMIC</b></td></tr>
</table>
<tt><font size="2">&nbsp; &nbsp; DWORD &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; rt_size; &nbsp; &nbsp;/* size of rich-text field */<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;error; &nbsp; &nbsp; &nbsp;/* return code from API calls */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; /* We are done filling the buffer with CD records. Now append the <br>
 &nbsp; &nbsp; &nbsp; buffer to the note as a rich text field. First find the size of <br>
 &nbsp; &nbsp; &nbsp; the buffer. Then add the rich-text field to the note by calling <br>
 &nbsp; &nbsp; &nbsp; NSFItemAppend. NSFItemAppend copies the data out of the buffer <br>
 &nbsp; &nbsp; &nbsp; specified by rt_field. Therefore, after calling NSFItemAppend, we <br>
 &nbsp; &nbsp; &nbsp; can free the buffer.<br>
 &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; rt_size = (DWORD)(buff_ptr - rt_field);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; error = NSFItemAppend( note_handle,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&quot;RICH_TEXT&quot;, strlen(&quot;RICH_TEXT&quot;),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_COMPOSITE,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;rt_field, rt_size );</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; free( rt_field );</font></tt><br>
<br>
<br>
This code fragment gets the total length of the data in the buffer and calls NSFItemAppend.<br>
<br>
NSFItemAppend adds an item to the note specified by note_handle. The name of the field in the note is &quot;RICH_TEXT.&quot; The data type parameter, TYPE_COMPOSITE, specifies that this is a rich text field. The pointer  rt_field specifies the buffer of data, which must be in Domino canonical format. The rt_size parameter specifies how much data is in the buffer. <br>
<br>
Not shown above are the subsequent call to NSFNoteUpdate to save the new note to disk and the code that closes the note and the database.
---
