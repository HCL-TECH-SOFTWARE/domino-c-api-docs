##### Chapter 7-3
##### Document Links

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter describes document links<font color="#FF0000"> </font>which reside in rich text fields. Notes displays document links as an icon. Clicking on a document link icon opens a new window and where the linked-to document is displayed.<br>
<br>
<br>
<b><font size="5" color="#000080">Types of Document Links</font></b><br>
<br>
There are two types of document links. The first type consists of a CDLINK2 record and a DocLink Reference List<font color="#FF0000"> </font>item. The second type consists of a CDLINKEXPORT2 record.<br>
<br>
When a user creates a document link from the Notes user interface, the first type of document link (CDLINK2) is created. This type of document link has two parts: a CDLINK2 record that resides in a rich text field and a DocLink Reference List ($Links) item, which is an internal field that is not displayed at the user interface. The CDLINK2 record requires the DocLink Reference List ($Links) item to resolve the link.<br>
<br>
The second type of document link consists of a CDLINKEXPORT2 record that resides in a rich text field. This type of link is more robust because the CDLINKEXPORT2 record contains all the information necessary to resolve the link. If you copy just the CD records from the rich text field of a source note to a destination note, CDLINKEXPORT2 document links still work. CDLINK2 document links cannot function without their associated DocLink Reference List ($Links) items.<br>
<br>
When a chunk of rich text containing a CDLINK2 document link is exported to the clipboard, Notes converts the CDLINK2 record to a CDLINKEXPORT2. Notes performs this conversion because a CDLINKEXPORT2 record contains the NOTELINK information that a CDLINK2 structure lacks. A CDLINKEXPORT2 functions properly in the context of other documents or databases where the original DocLink Reference List ($Links) item is not available.<br>
<br>
<b><font size="5" color="#000080">View and Database Links</font></b><br>
<br>
A View link may be added to a note using another CDLINKEXPORT2 structure that has the same information as the Document Link CDLINKEXPORT2 structure but with the UNID Note structure set to all zeros.  A Database Link may also be added, again with another CDLINKEXPORT2 structure with both UNID View and UNID Note structures set to all zeros.  You could also group a total of 3 CDLINKEXPORT2 structures together to create first a document link (structure 1), a view link (structure 2) and then a database link (structure 3) to a note.<br>
<br>
<b><font size="5" color="#000080">Anchor Links</font></b><br>
<br>
An Anchor link may be added to a note using another CDLINKEXPORT2 structure that has the same information as the Document Link CDLINKEXPORT2 structure but it also fills out the Display Comment field with the following Anchor related information: A LinkTitle string followed by a NULL, a server &quot;hint&quot; string followed by a NULL, and the actual Anchor Text string, followed by another NULL.  For example the Title string might look like &quot;Database 'DocLink 1 Test database', View 'Main View', Document 'This is a document', Anchor '2'&quot;.  The server &quot;hint&quot; string can be just a NULL.  The Anchor Text might be &quot;2&quot; to identify  2 as the Anchor in the document, etc. (when a user creates an Anchor Link from the UI and points the mouse at the Link the Title information is displayed at the bottom of the screen).<br>
<br>
<b><font size="5" color="#000080">Creating Document Links, View Links, Database Links and Anchor Links</font></b><br>
<br>
There are two ways to create document links in rich text fields. The first way is to use the API function CompoundTextAddDocLink. For more information on this technique, see the sample program EASYRICH and the CompoundText functions in the <i>Reference.</i>The second way is to directly create CDLINKEXPORT2 records in a rich text field that create a document link, a view link, a database link and an anchor link. The remainder of this chapter explains this method.<br>
<br>
<br>
<b><font size="5" color="#000080">Creating </font></b><b><font size="5" color="#000080">CDLINKEXPORT2 Lin</font></b><b><font size="5" color="#000080">ks</font></b><br>
<br>
To create a document link, a view link,  a database link and an anchor link the low-level way, place 4 CDLINKEXPORT2 Composite Data records in the rich text field of a note. These records each contain three pieces of information about the linked-to document, view , database, and anchor link.  In addition the anchor link contains data in the Display Comment section.<br>

<ul type="disc">
<li>The replica ID of the database containing the linked-to document, view and database (same info for all 4).
<li>The UNIVERSALNOTEID of the view containing the linked-to document (set to zeros for a database link).
<li>The UNIVERSALNOTEID of the linked-to document itself (set to zeros for a view and database link).
<li>The Display Comment section is filled in with a Link Title, a NULL, the Anchor Text, and another NULL for the Anchor link. </ul>
<br>
<br>
<b><font size="5" color="#000080">The DOCLINK</font></b><b><font size="5" color="#000080"> Sample Program</font></b><br>
<br>
The DOCLINK sample program creates two notes, one in the database doclink1.nsf and one in the database doclink2.nsf. The document in doclink1.nsf contains text, while the document in doclink2.nsf contains a document link, a view link, a database link , and an anchor link to the first document. Clicking on the document link icon in the second document causes Notes to open and display the first document.  Clicking on the view link icon in the second document causes Notes to open and display the first document's view, clicking on the database link icon in the second document causes Notes to open and display the first document's database, and clicking on the anchor link icon in the second document causes Notes to open and display the document page with anchor text.
<ul></ul>
<br>
<b><font size="4" color="#000080">doclink.c</font></b><br>
<br>
The algorithm DOCLINK uses is:<br>

<ol type="1">
<li>Open the database doclink1.nsf.
<li>Get the note ID of the &quot;Main View&quot; view note.
<li>Open the view note.
<li>Call NSFNoteGetInfo to get the ORIGINATORID of the view note and save it.
<li>Close the view note.
<li>Create a new note, put some text in it and create an anchor to some text in the body.
<li>Update the note (save it to disk).
<li>Get the OID of the note and save it. 
<li>Close the note.
<li>Get the replica ID of the database doclink1.nsf. 
<li>Open the database doclink2.nsf.
<li>Create a new document and put some text in a text field.
<li>Create a rich-text item in memory. This will contain a CDPARAGRAPH record and a CDLINKEXPORT2 record.
<li>Create a document link, a view link, a database link, and then an anchor link.  Fill in the fields of 4 CDLINKEXPORT2 structures as follows:                                                                                                                                                                                                                                                                                                                                                                                                                                                                        <br>
Document Link CDLINKEXPORT2 structure - The replica ID of the database doclink1.nsf<br>
                                                            - The ORIGINATORID of the view note &quot;Main View&quot; in doclink1.nsf<br>
                                                            - The ORIGINATORID of the data note that you just created in  doclink1.nsf<br>
View Link CDLINKEXPORT2 structure - The replica ID of the database doclink1.nsf<br>
                                                            - The ORIGINATORID of the view note &quot;Main View&quot; in doclink1.nsf<br>
                                                            - The ORIGINATORID of the data note set to all zeros                                                   Database Link CDLINKEXPORT2 structure - The replica ID of the database doclink1.nsf<br>
                                                            - The ORIGINATORID of the view note set to all zeros <br>
                                                            - The ORIGINATORID of the data note set to all zeros                                                           Anchor Link CDLINKEXPORT2 structure - The replica ID of the database doclink1.nsf<br>
                                                            - The ORIGINATORID of the view note &quot;Main View&quot; in doclink1.nsf<br>
                                                            - The ORIGINATORID of the data note that you just created in  doclink1.nsf                     <br>
                                                            - The Display Comment section filled in with the Title, a Null, Anchor Text and a Null.
<li>Append  the rich-text item to the note in doclink2.nsf, update the note, and close the database.</ol>

---
