##### Chapter 9-5
##### Field-Level Security

 This chapter provides additional details about using the HCL C API for Domino and Notes to provide<font color="#FF0000"> </font>section-level and field-level security.<br>
<br>
<b><font size="5" color="#000080">Section-Level Security Fields</font></b><br>
<br>
Domino provides section-level security in documents that use<font color="#FF0000"> </font>a form containing one or more sections. A section controls edit access to all fields within its boundaries. A field of type Section stores a list of names (user names, group names, and access roles). Domino grants members of the list editor access to other fields in the section.<br>
<br>
A field of type Section is defined at the form level. Sections are not a true security feature. In Notes, you can access<font color="#FF0000"> </font>fields that are read-only when viewed through a document containing sections by using<font color="#FF0000"> </font>a different form. A C API program has<font color="#FF0000"> </font>the same access to fields in a section as<font color="#FF0000"> </font>it does to other fields in the document. The section's editor access list has no effect when the C API program updates the document.<br>
<br>
When you create a form note with a C API program, use the CDFIELD data structure to define a field of type Section. Use the data type TYPE_TEXT or TYPE_TEXT_LIST and include the FSECTION flag in the CDFIELD data structure. All fields and static text definitions following the section's CDFIELD structure belong to the section until a new section's CDFIELD structure is defined or the end of the form is reached. For more information on creating form notes, see the &quot;Forms&quot; chapter in this guide.<br>
<br>
When a C API program edits or creates a document, there is no distinction between a section item and an item of TYPE_TEXT or TYPE_TEXT_LIST with the SUMMARY flag set. At the C API level, the SUMMARY flag corresponds to the ITEM_SUMMARY bit in the item flags.<br>
<br>
Since the C API functions NSFItemSetText and NSFItemAppendTextList set the ITEM_SUMMARY flag, you can use them to append an item of this type to a document.<br>
<br>
<b><font size="5" color="#000080">Field-Level Security</font></b><br>
<br>
Domino provides field-level security in documents that use<font color="#FF0000"> </font>a form containing one or more fields with the Security options property &quot;Must have at least Editor access to use.&quot; In a document, such a field has the PROTECTED flag set. At the C API level, the PROTECTED flag corresponds to the ITEM_PROTECTED bit in the item flags.<br>
<br>
As in the Notes UI, a C API program with author access cannot modify the value of fields that require editor access of documents, even if the user authored the document. If the program tries to do this, NSFNoteUpdate does not fail, but fields that have editor-only access are not modified.<br>
<br>
If a C API program with editor or above access modifies an editor-only access field, it is the C API program's responsiblity to set the ITEM_PROTECTED flag when setting the field value. Otherwise, a C API program with author access can later modify this field if the user authored the document. The user cannot modify the field in the Notes UI<font color="#FF0000">, </font>but when a C API program modifies a document, there is no internal mechanism that checks the document with its associated form design.<br>
<br>
<br>
To define a field that has the Security options property &quot;Must have at least Editor access to use,&quot; include the FPROTECTED flag in the CDFIELD data structure. For more information on creating form notes, see the &quot;Forms&quot; chapter in this guide.
---
