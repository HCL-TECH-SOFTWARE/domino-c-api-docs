##### Chapter 9-1
##### Security

<b><font size="5" color="#000080">Security Levels</font></b><br>
<br>
Domino provides levels of security as a means of protecting data. Each level of security refines the previous level. See the <i>Domino 5 Designer Help</i> for detailed information on Domino security.<br>
<br>
HCL C API programs for Domino and Notes operate on behalf of the user ID active in the environment at run time. The user ID determines the level of access you have to a Domino database.<br>
<br>
In most cases, security enforced by the Notes user interface is also supported in C API programs. The C API also allows you to access and modify many Domino security features.  You cannot use the  C API to access Workstation Security options or the user's Execution Control List (ECL).<br>
<br>
<br>
<b><font size="5" color="#000080">Server-Level Security</font></b><br>
<br>
To use a C API program to access a database on a server, the user must have access to the server itself. Otherwise, an error is returned when the C API program attempts to open the database.<br>
<br>
<br>
<b><font size="5" color="#000080">Database-Level Security</font></b><br>
<br>
Every database has an access control list (ACL), which specifies the users who can access the database and what they can do in the database. This level of security is also supported in a C API program. For example, a user with Reader access receives an error when a C API program attempts to update a document.<br>
<br>
The C API provides functions that access and modify the access control list for a database. Users of these functions must have Manager access to update/store an access control list. See the &quot;Access Control Lists&quot; chapter in this guide and the access control list functions in the <i>Reference.</i><br>
<br>
This level of security is enforced on databases that reside on a Domino server and are accessed remotely.  In addition, the access control list of a replica copy of a database may be enforced on a Notes client if the &quot;Enforce a consistent Access Control List across all replicas of this database&quot; option is checked in the database's access control list. However, a C API program can bypass this security by opening the database with NSFDbOpen or with NSFDbOpenExt (using NULLHANDLE for the hNames parameter).  It is also important to note that a C API program may be able to modify an ACL of a database with the same user ID that is restricted when accessed from a Notes Client.  This can happen if there is a Server group entry for the ACL.  The access verification performed on the Client will detect a person is trying to modify the ACL.  In the C API program this verification is not performed and security is bypassed.  Please see the index - ACL - user types in the Domino Administrator's Help database.<br>
<br>
<b><font size="5" color="#000080">View-Level Security</font></b><br>
<br>
You can restrict access to a view by defining a read access list for the view. This level of security is also supported in a C API program. For example, a user who is not in the read access list for a view receives an error when a C API program attempts to access that view. For example,  NIFFindView and NIFFindDesignNote will fail.<br>
<br>
The C API allows you to create a read access list for a view note by defining an item called $Readers in the view note. This item is of TYPE_TEXT_LIST with the ITEM_SUMMARY and ITEM_READERS flags set. For more information about creating view notes, see the &quot;Views&quot; chapter in this guide. For more information about creating a $Readers item, see the &quot;Setting Document Read Access&quot; chapter in this guide.<br>
<br>
<br>
<b><font size="5" color="#000080">Form-level Security</font></b><br>
<br>
You can restrict read access to all documents composed with a form by creating a read access list for the form. All documents composed with that form automatically inherit the read access list. This level of security is also supported in a C API program. For example, suppose a document was composed with a form that contains a read access list. If the user is not in the read access list, NSFSearch will not find this particular document and NIFOpenCollection will not include this document. If the C API program attempts to open this particular document and the user is not in the read access list, NSFNoteOpen returns an error.<br>
<br>
The C API allows you to create a read access list for a form note by defining an item called $Readers in the form note. This item is of TYPE_TEXT or TYPE_TEXT_LIST with the ITEM_SUMMARY flag set. For more information about creating form notes, see the &quot;Forms&quot; chapter in this guide.<br>
<br>
You can restrict the ability to compose a document with a particular form by creating a compose access list for that form. This level of security is not automatically supported in a C API program. When a C API program creates a document, there is no internal mechanism that checks the new document with the form design associated with it.<br>
<br>
The C API allows you to create a compose access list for a form note by defining an item called $FormUsers in the form note. This item is of TYPE_TEXT or TYPE_TEXT_LIST with the ITEM_SUMMARY flag set. For more information about creating form notes, see the &quot;Forms&quot; chapter in this guide.<br>
<br>
<br>
<b><font size="5" color="#000080">Document-Level Security</font></b><br>
<br>
Domino provides various types of document-level security. <br>
<br>
A document can contain a read access list. This list may be created in the form design and inherited automatically when the document is created, or it may be created and modified when creating or editing a document. <br>
<br>
Forms can contain fields of type Reader Names. A Reader Names field contains a list of allowed readers for a particular document. The list  may be created in the form design or it may be created and modified when creating or editing the document.<br>
<br>
Forms can also contain fields of type Author Names. An Author Names field contains a list of allowed editors for a particular document. The list may be created in the form design or it may be created and modified when creating or editing the document.<br>
<br>
This level of security is also supported in a C API program. For example, if a user is not listed in a field of type Author Names in a document, the user cannot update the document (NSFNoteUpdate returns an error) in a C API program. <br>
<br>
For more information about using the C API to append read access lists in a document, see the &quot;Setting Document Read Access&quot; chapter in this guide.<br>
<br>
For more information about using the C API to append fields of types Reader Names and Author Names, see the &quot;Document-Level Security Fields&quot; chapter in this guide.<br>
<br>
<b><font size="5" color="#000080">Section-Level Security</font></b><br>
<br>
Forms can contain one or more sections, each of which can have its own edit access list. The list can be created in the form design or created and modified when creating or editing the document.<br>
<br>
This level of security is not automatically supported in a C API program. A C API program can append any field to a document. There is no internal mechanism that checks section access when a note is updated.<br>
<br>
For more information about fields of type Section, see the &quot;Field-Level Security&quot; chapter in this guide.<br>
<br>
<b><font size="5" color="#000080">Field-Level Security</font></b><br>
<br>
When you design a field in a form, you can use the Options - Security options field in the Design - Field Properties infobox to define the field as: Must have at least Editor access to use.<br>
<br>
This level of security is supported in a C API program. A C API program with author access will not modify the value of fields that require at least editor access. For more information, see the &quot;Field-Level Security&quot; chapter in this guide.
---
