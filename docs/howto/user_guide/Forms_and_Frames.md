##### Chapter 8-1
##### Forms and Frames

<b><font size="6" color="#000080">Forms</font></b><br>
<br>
A form serves as a template for data notes in a database. Forms are notes of class NOTE_CLASS_FORM.<br>
Subforms are also forms of class NOTES_CLASS_FORM and may be inserted into a form.<br>
<br>
 <br>
<b><font size="5" color="#000080">Components of a Form Note and A Subform Note</font></b><br>
<br>
A form note consists of three items: a $TITLE item, a $INFO item, and one or more $Body items.<br>
<br>
A subform note consists of four items:  a $TITLE item, a $INFO item, a $Flags item, and one or more $Body items.<br>
<br>
<br>
<b><font size="4" color="#000080">$TITLE</font></b><br>
<br>
The $TITLE item must be the first item in a form note. It is a text item that contains a string specifying the name of the form.<br>
<br>
<br>
<b><font size="4" color="#000080">$INFO</font></b><br>
<br>
The second item in a form note is a rich text item called $INFO. It consists of a CDDOCUMENT data structure, which contains information that pertains to all documents created using the form.  For a description of the CDDOCUMENT structure, see the <i>Reference.</i><br>
<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
<br>
The $Flags item is an additional item and is used to identify a subform from a form note.  The following flag values must be set to create a subform and are defined in stdnames.h:<br>
<br>
DESIGN_FLAG_ADD<br>
DESIGN_FLAG_NO_COMPOSE<br>
DESIGN_FLAG_SUBFORM<br>
DESIGN_FLAG_HIDE_FROM_V3<br>
<br>
<br>
 <b><font size="4" color="#000080">$BODY</font></b><br>
<br>
Following the $TITLE and $INFO items is a sequence of one or more $BODY items, which are rich text items that define the layout and data types of all the fields in the form.  <br>
<br>
A form contains variable data (the fields in which you can enter or edit data) and static, unchanging data, such as field labels and whitespace on the document page. The fields are defined by the CDFIELD data structure, while the rest of the form is defined by a sequence of other Composite Data records, usually CDTEXT items.<br>
<br>
<br>
<b><font color="#000080">Defining Fields with the CDFIELD Data Structure </font></b><br>
<br>
The CDFIELD data structure contains all the information needed to define a field, including:<br>

<ul type="disc">
<li>The name assigned to the field
<li>The data type of the field (TYPE_TEXT, TYPE_NUMBER, TYPE_COMPOSITE, and so on)
<li>Font in which data will be displayed  in the field
<li>Field formulas (if any)</ul>
<br>
For a full description of the CDFIELD structure, see the <i>Reference.</i><br>
<br>
<br>
<b><font size="4" color="#000080">Defining Non-Field Form Data</font></b><br>
<br>
The non-field data in a form (field labels, whitespace, and so on) is often used to label fields and to position them on the work page. For example, to define a form containing two text fields separated by a blank line, the $BODY item would contain:<br>

<ul type="disc">
<li>A CDFIELD item defining the text field as desired
<li>A CDTEXT item containing the null string (&quot;&quot;) to display a blank line
<li>A second CDFIELD item defining the second text field</ul>
<br>
Of course, in this example the $BODY item would also contain the appropriate paragraph-related CD structures (CDPARAGRAPH, CDPABDEF, CDPABREF, and so on).<br>
<br>
<br>
<b><font size="5" color="#000080">The READFORM Sample Program</font></b><br>
<br>
The sample program READFORM opens a database called readform.nsf, opens the form note for the form titled &quot;test form 1,&quot; reads the $TITLE item that contains the title of the form, and stores the title in a buffer to be displayed later.<br>
<br>
Next, READFORM reads the $BODY item and calls EnumCompositeBuffer to search for each CDFIELD record in $BODY.  <br>
<br>
NOTE:  Version 3.0 of the C API added a fourth parameter to the EnumCompositeBuffer function, a void pointer to user-defined data. This allows the action routine and the calling routine to share data without requiring the data to be global. READFORM passes a pointer to an output character buffer in this fourth parameter.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>READFORM: Action Routine FormFields - Reading Field Names and Datatypes</b></td></tr>
</table>
<tt><font size="2">/*<br>
 * FORMFIELDS() -- Action routine invoked by EnumCompositeBuffer.<br>
 *<br>
 * For each field in a form, the $Body field of the Form note will<br>
 * contain a record of type CDFIELD, which defines that field. If the<br>
 * current record is a CDFIELD record, this routine extracts the <br>
 * field name and data type and writes these to the buffer pointed to </font></tt><br>
<tt><font size="2">&nbsp;* by the pCtx parameter. If the current record is not a CDFIELD record, </font></tt><br>
<tt><font size="2">&nbsp;* this routine simply returns.<br>
 */</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC FormFields (char *RecordPtr,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WORD RecordType,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DWORD RecordLength,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;void *pCtx)<br>
{<br>
char FieldString[256];<br>
char szFieldName[128];<br>
char szDataType[128];</font></tt><br>
<tt><font size="2">char far *pFieldName;<br>
WORD binDataType;<br>
char *pBuf = (char *)pCtx;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; switch (RecordType)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp;	case SIG_CD_FIELD:<br>
 &nbsp; &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;CDFIELD *pCDField; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pCDField = (CDFIELD *)RecordPtr;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;/*<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * Get the data type of this field<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; binDataType = pCDField-&gt;DataType;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;switch (binDataType)</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; case TYPE_TEXT:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Text&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_TEXT_LIST:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Multi-Value Text&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_NUMBER:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Number&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_NUMBER_RANGE:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Multi-Value Number&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_TIME:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Time/Date&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_TIME_RANGE:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Multi-Value Time/Date&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;case TYPE_COMPOSITE:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Rich Text&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;default:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strcpy (szDataType, &quot;Unknown Data Type&quot;);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * Now get the name of this field.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; 	 &nbsp; &nbsp;pFieldName = (RecordPtr + ODSLength(_CDFIELD) + pCDField-&gt;DVLength<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; + pCDField-&gt;ITLength + pCDField-&gt;IVLength);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; memcpy(szFieldName, pFieldName, pCDField-&gt;NameLength);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szFieldName[pCDField-&gt;NameLength] = '\0';</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;Construct a string containing the field name and datatype<br>
 &nbsp; &nbsp; &nbsp; &nbsp; * &nbsp;and append it to a global buffer.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; wsprintf(FieldString, &quot;Field Name = %s, &nbsp;Data Type = %s\n&quot;,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; szFieldName, szDataType);<br>
 	 &nbsp; &nbsp; &nbsp;lstrcat(pBuf, FieldString);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; &nbsp; &nbsp; &nbsp;default:<br>
 &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; return (NOERROR);<br>
}</font></tt><br>
<br>
The action routine FormFields, invoked by EnumCompositeBuffer for each CD record in $BODY, checks to see if the CD record being examined is a CDFIELD record. If not, FormFields exits. If the record is a CDFIELD, FormFields reads the field name and data type from the data structure, then writes a string describing the fieldname and data type to the buffer pointed to by pCtx.<br>
<br>
When FormFields has processed every CDFIELD record in the $BODY item, control returns to the main routine, which then displays the database title and the field information in a message box.<br>
<br>
<b><font size="6" color="#000080">Frames</font></b><br>
<br>
A frame serves as one section or pane, and can contain a form, folder, page, document, view, navigator, or frameset.  A frameset consists of a collection of frames that may contain links and other relationships.<br>
<br>
 <br>
<b><font size="5" color="#000080">Components of a Frameset and Frame</font></b><br>
<br>
A frameset note consists of a $TITLE item, a $Flags item, and a $Frameset item.<br>
<br>
<br>
<b><font size="4" color="#000080">$TITLE</font></b><br>
<br>
The $TITLE item must be the first item in a frameset note. It is a text item that contains a string specifying the name of the frameset.<br>
<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
<br>
The $Flags item is an additional item and is used to identify a frameset note.  The following flag values must be set to create a frameset and are defined in stdnames.h:<br>
<br>
DESIGN_FLAG_ADD<br>
DESIGN_FLAG_NO_COMPOSE<br>
DESIGN_FLAG_FRAMESET<br>
DESIGN_FLAG_HIDE_FROM_V3<br>
<br>
<br>
 <b><font size="4" color="#000080">$Frameset</font></b><br>
<br>
Following the $TITLE and $Flags items is a $Frameset item.  <br>
<br>
A frameset contains a number of general properties and individual frame properties that define the layout and arrangement of data.  This information is contained within the following CD records:<br>

<ul type="disc">
<li>CDFRAMESETHEADER
<li>CDFRAMESET
<li>CDFRAME
<li>CDRESOURCE</ul>
<br>
<b><font color="#000080">CDFRAMESET</font></b><br>
<br>
The CDFRAMESET data structure contains all the general properties of the frameset, including:<br>

<ul type="disc">
<li>Frame Border width (if enabled)
<li>Frame Spacing width
<li>Number of Frame Rows
<li>Number of Frame Columns
<li>Frame Types and Values</ul>
<br>
<b><font color="#000080">CDFRAME</font></b><br>
<br>
The CDFRAME data structure contains all the properties of a single frame, including:<br>

<ul type="disc">
<li>Scroll bar style
<li>Frame margin width
<li>Frame margin height
<li>Frame name and length
<li>Frame target name and length</ul>
<br>
<b><font color="#000080">CDRESOURCE</font></b><br>
<br>
The CDRESOURCE data structure contains the information needed to define the content of the frame: <br>

<ul type="disc">
<li>Type of resource (a named element, a link, a URL, etc.)
<li>Resource class (view, document, etc..)
<li>Resource name and length</ul>
<br>
<br>
For a full description of the these structures, see the <i>Reference.</i><br>
<br>
<br>
<b><font size="4" color="#000080">$DefaultFrameset</font></b><br>
<br>
To launch the frameset when the database is opened you must append a $DefaultFrameset Item to the icon note.  Please see the sample MAKEFORM for further information.<br>
 
---
