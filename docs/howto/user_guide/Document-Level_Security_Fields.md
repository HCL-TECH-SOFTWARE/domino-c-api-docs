##### Chapter 9-4
##### Document-Level Security Fields

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter explains how HCL C API programs for Domino and Notes can append document-level security fields to documents. It examines the sample program AUTH_FLD, which demonstrates how to append document-level security fields. The program appends items with data types Names, Author Names, and Reader Names.<br>
<br>
<b><font size="5" color="#000080">Document-Level Security Fields</font></b><br>
<br>
HCL Domino provides several levels of security in documents. Document-level security does not override the access control list; it only refines it. <br>
<br>
Editor access control over a document is supported via a field of type Author Names. A document may store a list of names (user names, group names, and access roles) to whom Domino will grant editor access.<br>
<br>
Any document that contains an Author Names type field also contains an internal field called $UpdatedBy, of type Names. This field stores a list of all the document's editors.<br>
<br>
Reader access control over a document is supported via a field of type Reader Names. A document may store a list of names (user names, group names, and access roles) to whom Domino will grant reader access.<br>
<br>
<br>
<b><font size="4" color="#000080">Data Type: Names</font></b><b><font size="5" color="#000080">  </font></b><br>
<br>
In the Notes user interface, when you compose a document using a form with a field of type Names, the result is an item of TYPE_TEXT (or TYPE_TEXT_LIST) with the NAMES flag set. The NAMES flag is the distinguished names flag. At the C API level, the NAMES flag corresponds to the ITEM_NAMES bit in the item flags. <br>
<br>
The NAMES flag itself does not make the field a document-level security field.  Instead it tells Domino or Notes that this field normally contains distinguished (hierarchical) names. The Notes editor simplifies these otherwise long names to display them. The simpler version of distinguished names is known as the &quot;abbreviated&quot; distinguished name. However, internally, Domino and Notes still stores these values in unabbreviated format.<br>
<br>
<br>
<b><font size="4" color="#000080">Data Type: Author Names</font></b><br>
<br>
When you compose a document using a form with a field of type Author Names, the internal (C API level) result is an item of TYPE_TEXT (or TYPE_TEXT_LIST) with both the NAMES flag and the READ/WRITE-ACCESS flag set. As with other text fields, the SUMMARY flag is also set. The READ/WRITE-ACCESS flag corresponds to the ITEM_READWRITERS bit in the item flags.<br>
<br>
The READ/WRITE-ACCESS flag tells Domino that this is an Author Names type field. <br>
<br>
Domino takes several actions in response to this field. First, it grants editor access to the entities named in the field. Since this new author field is TYPE_TEXT or TYPE_TEXT_LIST, it may contain multiple names, which may be user names, group names, or access roles. <br>
<br>
Second, Domino and Notes automatically appends the special field  $UpdatedBy to any document that has an Author Name type field. $UpdatedBy is a TEXT_LIST field that tracks all the users who created or modified a document. This preserves the functionality of the Document Author type field of earlier versions of Notes. Note that $UpdatedBy has the NAMES flag set. The @Author function returns the contents of the $UpdatedBy field.<br>
<br>
In Notes 1.x and Notes 2.x, the Document Author field data type corresponded to items of type TYPE_USERID in the C API. Notes 3.x and later does not append items of type TYPE_USERID to documents. However, Notes 3.x and later recognizes items of type TYPE_USERID in documents. It treats such items as Notes 1.x/2.x Document Author type fields.<br>
<br>
<br>
<b><font size="4" color="#000080">Data Type: Reader Names</font></b><br>
<br>
HCL Domino and Notes also provide the field data type Reader Names. Domino grants reader access to entities named in a field of type Reader Names. Internally, fields of this type are TYPE_TEXT or TYPE_TEXT_LIST items with the SUMMARY, NAMES, and READ-ACCESS flags set. At the C API level, the READ-ACCESS flag corresponds to the ITEM_READERS bit in the item flags.<br>
<br>
<br>
<b><font size="4" color="#000080">Writing Names Fields</font></b><br>
<br>
Store distinguished names in fields with external data type Names. The Notes editor will display such fields in abbreviated format.<br>
<br>
The special $UpdatedBy field is an example of a field with external data type Names. Domino and Notes maintains a list of the distinguished names of each user who created or modified the document in the $UpdatedBy field. <br>
<br>
The sample program AUTH_FLD contains a subroutine, AppendUpdatedByItem, that appends an $UpdatedBy item to an open note.<font color="#FF0000"> </font>At the C API level the item has TYPE_TEXT or TYPE_TEXT_LIST with the ITEM_NAMES flag set. Since the C API function NSFItemSetText does not set the ITEM_NAMES flag, AppendUpdatedByItem, shown below, uses NSFItemAppend.<br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>auth_fld.c - Writing Names Fields</b></td></tr>
</table>
<tt><font size="2">/************************************************************************</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; FUNCTION: &nbsp; AppendUpdatedByItem</font></tt><br>
<br>
<tt><font size="2">*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS LNPUBLIC AppendUpdatedByItem (NOTEHANDLE hNote, char * szAuthor)<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp;error;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemAppend ( hNote, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_SUMMARY | ITEM_NAMES,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DISCUSS_ITEM_UPDATEDBY, &nbsp;/* &quot;$UpdatedBy&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD) strlen(DISCUSS_ITEM_UPDATEDBY),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_TEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szAuthor,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(szAuthor)))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to append $UpdatedBy field.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return (error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">Writing Author Names Fields</font></b><br>
<br>
Fields of external data type Author Names are stored as items of TYPE_TEXT or TYPE_TEXT_LIST with both the NAMES flag (ITEM_NAMES) and the READ/WRITE-ACCESS flag (ITEM_READWRITERS) set.<br>
<br>
The sample program AUTH_FLD contains a subroutine, AppendAuthorItem, that appends an Author Names type item to an open note. At the C API level the item has TYPE_TEXT or TYPE_TEXT_LIST with the ITEM_NAMES flag and the ITEM_READWRITERS<font color="#FF0000"> </font>flag set. Since the C API function NSFItemSetText does not set the proper flag, AppendAuthorItem, shown below, uses NSFItemAppend.<br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>auth_fld.c</b><b> - Writing Author Names Fields</b></td></tr>
</table>
<tt><font size="2">/************************************************************************<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;FUNCTION: &nbsp;AppendAuthorItem</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; Append item named &quot;Author&quot; to the open note. <br>
 &nbsp; &nbsp;<br>
 &nbsp; &nbsp;DESCRIPTION:</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; To mimic the behavior of the Notes 3.x and later data type &quot;Author Names&quot;,<br>
 &nbsp; &nbsp;this appends the item using TYPE_TEXT and sets the item flags <br>
 &nbsp; &nbsp;ITEM_SUMMARY, ITEM_READWRITERS, and ITEM_NAMES. This requires use <br>
 &nbsp; &nbsp;of NSFItemAppend rather than NSFItemSetText.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;AppendAuthorItem (NOTEHANDLE &nbsp;hNote, char * szAuthor)<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp;error;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemAppend ( hNote, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_SUMMARY | ITEM_READWRITERS | ITEM_NAMES,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DISCUSS_ITEM_AUTHOR, &nbsp;/* &quot;Author&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD) strlen(DISCUSS_ITEM_AUTHOR),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_TEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;szAuthor,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;strlen(szAuthor)))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to append Author field.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;return (error);<br>
}</font></tt><br>
<br>
<br>
<b><font size="4" color="#000080">Writing Reader Names Fields</font></b><br>
<br>
Fields with external data type Reader Names are stored as items of TYPE_TEXT or TYPE_TEXT_LIST with both the NAMES flag (ITEM_NAMES) and the READ-ACCESS flag (ITEM_READERS) set.<br>
<br>
The sample program AUTH_FLD contains a subroutine, AppendReadersItem, that creates an item named &quot;Readers,&quot; containing two names, and appends it to an open note. The item has external data type Reader Names. At the C API level the item is of TYPE_TEXT_LIST with the ITEM_NAMES flag and the ITEM_READERS flag set. Since the C API function NSFItemSetText does not set the proper flag, AppendReadersItem, shown below, uses NSFItemAppend.<br>
<br>

<table border="1">
<tr valign="top"><td width="648"><b>auth_fld.c</b><b> - Writing Reader Names Fields</b></td></tr>
</table>
<tt><font size="2">/************************************************************************<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;FUNCTION: &nbsp; AppendReadersItem</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; PURPOSE: &nbsp; &nbsp;Create and append the Readers item to the note. <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
*************************************************************************/</font></tt><br>
<br>
<tt><font size="2">STATUS &nbsp;LNPUBLIC &nbsp;AppendReadersItem (NOTEHANDLE &nbsp;hNote)<br>
{<br>
 &nbsp; &nbsp;STATUS &nbsp; &nbsp; &nbsp;error = NOERROR;<br>
 &nbsp; &nbsp;DWORD &nbsp; &nbsp; &nbsp; dwValueLen;<br>
 &nbsp; &nbsp;void far &nbsp; *pvoidItemValue;<br>
 &nbsp; &nbsp;LIST &nbsp; &nbsp; &nbsp; *pList;<br>
 &nbsp; &nbsp;USHORT &nbsp; &nbsp; *pusLength;<br>
 &nbsp; &nbsp;USHORT &nbsp; &nbsp; &nbsp;usLen1, usLen2;<br>
 &nbsp; &nbsp;char &nbsp; &nbsp; &nbsp; *pchStr;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; usLen1 = strlen(READERS1);<br>
 &nbsp; &nbsp;usLen2 = strlen(READERS2);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; dwValueLen = sizeof(LIST) + (READERS_COUNT * sizeof(USHORT)) +<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; usLen1 + usLen2 ;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pvoidItemValue = (void far *) malloc ((size_t)dwValueLen);<br>
 &nbsp; &nbsp;if (pvoidItemValue == NULL)<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to allocate %lu bytes memory.\n&quot;, dwValueLen);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return(ERR_AUTH_FLD_MALLOC);<br>
 &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; pList = (LIST*)pvoidItemValue;<br>
 &nbsp; &nbsp;pList-&gt;ListEntries = READERS_COUNT;<br>
 &nbsp; &nbsp;pList++;<br>
 &nbsp; &nbsp;pusLength = (USHORT*)pList;<br>
 &nbsp; &nbsp;*pusLength = usLen1;<br>
 &nbsp; &nbsp;pusLength++;<br>
 &nbsp; &nbsp;*pusLength = usLen2;<br>
 &nbsp; &nbsp;pusLength++;<br>
 &nbsp; &nbsp;pchStr = (char*)pusLength;<br>
 &nbsp; &nbsp;memcpy (pchStr, READERS1, usLen1);<br>
 &nbsp; &nbsp;pchStr += usLen1;<br>
 &nbsp; &nbsp;memcpy (pchStr, READERS2, usLen2);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; if (error = NSFItemAppend ( hNote, <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_SUMMARY | ITEM_READERS | ITEM_NAMES,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;DISCUSS_ITEM_READERS, &nbsp;/* &quot;Readers&quot; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(WORD) strlen(DISCUSS_ITEM_READERS),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;TYPE_TEXT_LIST,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pvoidItemValue,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;dwValueLen))<br>
 &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;Error: unable to append Readers field.\n&quot;);<br>
 &nbsp; &nbsp;}<br>
 &nbsp; &nbsp;free (pvoidItemValue);<br>
 &nbsp; &nbsp;return (error);<br>
}</font></tt>
---
