##### Chapter 7-7
##### Font Tables

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
Domino and Notes store the definitions of additional font faces (font faces other than FONT_FACE_xxx) in a special item called a font table. This chapter explains how to use the C API to access font tables in documents.<br>
<br>
<br>
<b><font size="5" color="#000080">The Font Table Item</font></b><br>
<br>
A font table resides in a special item with field name $Fonts (ITEM_NAME_FONTS) and data type TYPE_COMPOSITE. Each entry in a font table associates a font ID with information that describes the font in a platform-independent manner. <br>
<br>
A font table is necessary when a rich text field in a document contains text that uses font faces other than the standard ones (FONT_FACE_ROMAN, FONT_FACE_SWISS, and FONT_FACE_TYPEWRITER).<br>
<br>
When a Notes user assigns a non-standard font face to document text, Notes creates a font table item, assigns a unique ID to that font face, and associates the ID with a description of that font<font color="#FF0000"> </font>face in an entry in the font table. The CDTEXT records in the rich text field refer to the ID in the font table.<br>
<br>
A C API program must add a font table to a document in order to give text in a rich text field any font<font color="#FF0000"> </font>face other than FONTID_ROMAN, FONTID_SWISS, or FONTID_TYPEWRITER. <br>
<br>
<b><font size="5" color="#000080">Creating the Font Table</font></b><br>
                                                                         <br>
The data value of a font table item consists of a CDFONTTABLE record followed by one or more CDFACE records. <br>
                                                                         <br>
CDFONTTABLE<br>
CDFACE<br>
CDFACE<br>
CDFACE<br>
...<br>
                                                                       <br>
The C API header file editods.h defines the CDFONTTABLE structure.  It consists of a Header member and a Fonts member. The Fonts member must be set to the number of CDFACE structures in the FONTTABLE.<br>
<br>
The CDFACE structure contains the members Face, Family, and Name. The Face member is an application-assigned font ID for this font. The Family and Name members are the family code and name of the font associated with the font ID. Do not use font IDs 0 through 4, since these are hard-coded in Domino and Notes. The application should assign font IDs starting with the number STATIC_FONT_FACES (5), which is defined in fontid.h.<br>
<br>
The Family member of the CDFACE structure is a BYTE in which the four low-order bits specify the pitch of the font and the four high-order bits specify the font family.<br>
<br>
For Windows programs, use the values as defined in windows.h:<br>
<br>
<tt>/* PitchAndFamily pitch values (low 4 bits) */<br>
#define DEFAULT_PITCH &nbsp; 0x00<br>
#define FIXED_PITCH &nbsp; &nbsp; 0x01<br>
#define VARIABLE_PITCH &nbsp;0x02</tt><br>
<br>
<tt>/* PitchAndFamily family values (high 4 bits) */<br>
#define FF_DONTCARE &nbsp; &nbsp; 0x00<br>
#define FF_ROMAN &nbsp; &nbsp; &nbsp; &nbsp;0x10<br>
#define FF_SWISS &nbsp; &nbsp; &nbsp; &nbsp;0x20<br>
#define FF_MODERN &nbsp; &nbsp; &nbsp; 0x30<br>
#define FF_SCRIPT &nbsp; &nbsp; &nbsp; 0x40<br>
#define FF_DECORATIVE &nbsp; 0x50</tt><br>
<br>
Use NSFItemAppend to write a field named $FONTS (#defined as ITEM_NAME_FONTS in stdnames.h) to the note. This adds the font table to the note.<br>
<br>
<br>
<b><font size="5" color="#000080">Using a Font in the Font Table</font></b><br>
<br>
To use one of the fonts listed in the font table in a rich text field, set the CDTEXT FontID field to the application-assigned ID  (the Face member in the CDFACE structure).  <br>
<br>
<br>
<b><font size="5" color="#000080">The FONTBL Sample Program</font></b><br>
<br>
This section examines FONTBL, a sample program that creates a document, adds a font table to the document, and uses fonts from the font table to writes some rich text to a rich text field.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Creating a Font Table Structure in Sample Program FONTBL</b></td></tr>
</table>
<tt>/* #defines for fonts included in the font table */<br>
#define FTFAMILY_UNKNOWN &nbsp;0xF0 &nbsp; /* Font family */<br>
#define DEFAULT_PITCH &nbsp; &nbsp; 0x00<br>
#define FIXED_PITCH &nbsp; &nbsp; &nbsp; 0x01<br>
#define VARIABLE_PITCH &nbsp; &nbsp;0x02</tt><br>
<br>
<tt>#define FTFACE_ID &nbsp; STATIC_FONT_FACES &nbsp;/* starting </tt>ID<tt>&nbsp;number for the font<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;face in the font table */</tt><br>
<br>
<tt>#define NUM_FONTS &nbsp; &nbsp; 2 &nbsp; &nbsp;/* number of fonts in the font table */</tt><br>
<br>
<tt>/* Fill in the font table with the following fonts:<br>
 &nbsp; System Monospaced and System Proportional */</tt><br>
<br>
<tt>&nbsp; &nbsp;fntTable.Header.Signature = SIG_CD_FONTTABLE;<br>
 &nbsp; fntTable.Header.Length = ODSLength(_CDFONTTABLE) + (ODSLength(_CDFACE) * NUM_FONTS);<br>
 &nbsp; fntTable.Fonts = NUM_FONTS; &nbsp; /* number CDFACE records follow */</tt><br>
<br>
<tt>&nbsp; &nbsp; ODSWriteMemory( (void far * far *)&amp;pCDBuffer, _CDFONTTABLE, &amp;fntTable, 1 );</tt><br>
<br>
<tt>/* The ID number of the font face in the font table start at FTFACE_ID<br>
 &nbsp; (number 5). &nbsp;ID numbers 0 - 4 are hard-coded */</tt><br>
<br>
<tt>&nbsp; &nbsp;fntFace[0].Face = FTFACE_ID; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* ID number of face */</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Font family */<br>
 &nbsp; fntFace[0].Family = FTFAMILY_UNKNOWN | FIXED_PITCH;<br>
 &nbsp; strcpy (fntFace[0].Name, &quot;System Monospaced&quot;); &nbsp; /* Font name */</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp;fntFace[1].Face = FTFACE_ID + 1; &nbsp; &nbsp; &nbsp; /* ID number of face */</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Font family */<br>
 &nbsp; fntFace[1].Family = FTFAMILY_UNKNOWN | VARIABLE_PITCH; <br>
 &nbsp; strcpy (fntFace[1].Name, &quot;System Proportional&quot;); /* Font name */</tt><br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>Store the Font Table Structure in a Field Named $FONTS in the Note.</b></td></tr>
</table>
<br>
<tt>/* Write a field named $FONTS to the note. This field specifies the <br>
 &nbsp; font table used with the note. */</tt><br>
<br>
<tt>&nbsp; &nbsp;if (error = NSFItemAppend ( note_handle, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_NAME_FONTS,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD) strlen(ITEM_NAME_FONTS),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_COMPOSITE,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pCDBufferStart,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; pCDBuffer-pCDBufferStart))<br>
 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;NSFNoteClose (note_handle);<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (db_handle);<br>
 &nbsp; &nbsp; &nbsp;API_RETURN (ERR(error));<br>
 &nbsp; }</tt><br>
<br>
Once you have written the font table to the note, you can set the CDTEXT FontID field of a rich text structure to the Face ID of one of the fonts in the font table. 
---
