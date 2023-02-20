##### Chapter 12-2
##### Encryption/Decryption

You can use the C API to encrypt documents and to decrypt and read encrypted documents. Encrypted documents are those that contain encrypted fields.<br>
<br>
<b><font size="5" color="#000080">Encryption</font></b><b><font color="#0000FF">-</font></b><b><font size="5" color="#000080">Enabled Fields</font></b><br>
<br>
To encrypt a document, the document must contain at least one encryption-enabled field. Only the encryption-enabled fields in a document are encrypted. An API program uses NSFItemAppend to write an encryption-enabled field.  Set  ITEM_SEAL in the item flags.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>encrypt.c: Writing an Encryption Enabled Text Field</b></td></tr>
</table>
<tt><font size="2">#define ENCRYPTED_ITEM &quot;SECRET&quot;</font></tt><br>
<br>
<tt><font size="2">DBHANDLE &nbsp; &nbsp;hDB; &nbsp; &nbsp; &nbsp; &nbsp;/* database handle */ &nbsp; <br>
NOTEHANDLE &nbsp;hNote; &nbsp; &nbsp; &nbsp;/* note handle */ &nbsp;</font></tt><br>
<tt><font size="2">char	*EncryptKey; &nbsp; &nbsp; &nbsp;/* name of secret encryption key */ &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">char TextField[100]; &nbsp; &nbsp;/* contents of a text field */</font></tt><br>
<tt><font size="2">NOTEHANDLE &nbsp;hEncryptedNote;	/* note handle of encrypted note */ &nbsp;</font></tt><br>
<br>
<tt><font size="2">if (error = NSFItemAppend (hNote,<br>
		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_SUMMARY | ITEM_SEAL,<br>
		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ENCRYPTED_ITEM, strlen(ENCRYPTED_ITEM),<br>
		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT,<br>
		 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TextField, strlen(TextField)))<br>
{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; PrintAPIError(error);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFNoteClose (hNote);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFDbClose (hDB);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; return (1);</font></tt><br>
<tt><font size="2">}</font></tt><br>
<br>
<br>
<br>
<b><font size="5" color="#000080">Encryption Keys</font></b><br>
<br>
Encryption keys are used to encrypt documents.  Secret encryption keys (also known as personal encryption keys) can be created by the user.  These are stored in the user's ID.  Every Notes user has a public encryption key, which is stored in the Domino Directory and used mainly for sending encrypted mail.  Every Notes user also has a private encryption key that is stored in the user's  ID.  The private encryption key is used to decrypt documents that were encrypted with that user's public encryption key.<br>
<br>
You specify whether to use the current user's public key or a different key in the call to NSFNoteCopyAndEncrypt. <br>
<br>
If you want to encrypt a document with the current user's public key, specify the ENCRYPT_WITH_USER_PUBLIC_KEY flag.<br>
<br>
If you want to encrypt a document with a secret encryption key, an ITEM_NAME_NOTE_SEALNAMES field containing the name of the secret key must be appended to the document before you call NSFNoteCopyAndEncrypt. The encryption-enabled fields in the note are encrypted using this key. The ITEM_NAME_NOTE_SEALNAMES item is of TYPE_TEXT (or of TYPE_TEXT_LIST if there are multiple secret encryption keys for the note) with the ITEM_SUMMARY flag set.<br>
<br>
If you want to encrypt a document with a specified user's public key, an ITEM_NAME_NOTE_SEALUSERS field containing the canonical name of the user must be appended to the document before you call NSFNoteCopyAndEncrypt. The encryption-enabled fields in the note are encrypted using this key. The ITEM_NAME_NOTE_SEALUSERS item is of TYPE_TEXT (or of TYPE_TEXT_LIST if there are multiple users) with the ITEM_SUMMARY flag set.<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>encrypt.c: Writing the ITEM_NAME_NOTE_SEALNAMES Field</b></td></tr>
</table>
<tt><font size="2">&nbsp;</font></tt><br>
<tt><font size="2">if (error = NSFItemAppend (hNote,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_SUMMARY,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ITEM_NAME_NOTE_SEALNAMES, (WORD)strlen(ITEM_NAME_NOTE_SEALNAMES),<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE_TEXT,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; EncryptKey, (DWORD)strlen(EncryptKey)))<br>
{<br>
 &nbsp; &nbsp;PrintAPIError(error);<br>
 &nbsp; &nbsp;NSFNoteClose (hNote);<br>
 &nbsp; &nbsp;NSFDbClose (hDB);<br>
 &nbsp; &nbsp;NotesTerm();<br>
 &nbsp; &nbsp;return (1);<br>
}</font></tt><br>
<br>
<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>encrypt.c: Writing the ITEM_NAME_NOTE_SEALUSERS Field Containing Muliple Names</b></td></tr>
</table>
<tt><font size="2">if (error = NSFItemCreateTextList (hNote, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_NAME_NOTE_SEALUSERS, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;USER1, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD))</font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; PrintAPIError(error);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFNoteClose (hNote);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFDbClose (hDB);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; return (1);</font></tt><br>
<tt><font size="2">}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; /* Add another user to the ITEM_NAME_NOTE_SEALUSERS */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; </font></tt><br>
<tt><font size="2">if (error = NSFItemAppendTextList (hNote, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ITEM_NAME_NOTE_SEALUSERS, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;USER2, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FALSE)) </font></tt><br>
<tt><font size="2">{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; PrintAPIError(error);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFNoteClose (hNote);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NSFDbClose (hDB);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; NotesTerm();</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; return (1);</font></tt><br>
<tt><font size="2">}</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<br>
<br>
<b><font size="5" color="#000080">Encrypting the Document</font></b><br>
<br>
Once you have appended all the encrypted-enabled fields to the document and identified the encryption key(s),<b><font color="#FF0000"> </font></b>you can use NSFNoteCopyAndEncrypt to encrypt the encryption-enabled fields. In the following example, the second argument is set to 0, indicating that you want to use one or more secret encryption keys, one or more public keys or both secret and public encryption keys to encrypt the document.  Secret encryption keys are specified in the ITEM_NAME_NOTE_SEALNAMES field.  Canonical user names are specified in the ITEM_NAME_NOTE_SEALUSERS field if you want to use their public encryption key to encrypt the document.<br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>encrypt.c: Encrypting the Document</b></td></tr>
</table>
<tt><font size="2">if (error = NSFNoteCopyAndEncrypt (hNote, 0, &amp;hEncryptedNote)) <br>
{</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; PrintAPIError(error);<br>
 &nbsp; &nbsp;NSFNoteClose (hNote);<br>
 &nbsp; &nbsp;NSFDbClose (hDB);<br>
 &nbsp; &nbsp;NotesTerm();<br>
 &nbsp; &nbsp;return (1); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
if (error = NSFNoteUpdate (hEncryptedNote, 0)) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
{ <br>
 &nbsp; &nbsp;PrintAPIError(error);<br>
 &nbsp; &nbsp;NSFNoteClose (hNote);<br>
 &nbsp; &nbsp;NSFDbClose (hDB);<br>
 &nbsp; &nbsp;NotesTerm();<br>
 &nbsp; &nbsp;return (1);<br>
} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</font></tt><br>
<tt><font size="2">&nbsp;</font></tt><br>
<br>
<b><font size="5" color="#000080">Decrypting an Encrypted Document</font></b><br>
<br>
Use the API function NSFNoteDecrypt to decrypt an encrypted document and read any field from it. The user must have the proper encryption key in the user ID file to decrypt the document and read encrypted fields. <br>
<br>

<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>encrypt.c: Decrypting a Document</b></td></tr>
</table>
<tt><font size="2">NOTEID &nbsp; &nbsp; dwNoteID; &nbsp; &nbsp; &nbsp; &nbsp;/* note id obtained earlier */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
NOTEHANDLE hNote; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* note handle */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
STATUS &nbsp; &nbsp; error; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* return code from API calls */ <br>
BOOL &nbsp; &nbsp; &nbsp; fSealed; &nbsp; &nbsp; &nbsp; &nbsp; /* Is not encrypted? */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
BOOL &nbsp; &nbsp; &nbsp; FieldFound; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
WORD &nbsp; &nbsp; &nbsp; len; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
char &nbsp; &nbsp; &nbsp; ItemText[500]; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
if (error = NSFNoteOpen ( &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hDB, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* database handle */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; dwNoteID, &nbsp; &nbsp; &nbsp;/* note id */ &nbsp;</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;0, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* open flags */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &amp;hNote)) &nbsp; &nbsp; &nbsp; /* note handle (return) */ &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp;return (error); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
/* If the note is encrypted, decrypt it. */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
if (NSFNoteIsSignedOrSealed (hNote, NULL, &amp;fSealed) ) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;if (fSealed) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp;if (error = NSFNoteDecrypt ( &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hNote, &nbsp; &nbsp;/* note handle */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 0, &nbsp; &nbsp; &nbsp; &nbsp;/* reserved */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NULL)) &nbsp; &nbsp;/* Key for attachments - not <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; needed */ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; { &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; NSFNoteClose (hNote); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; return (error); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
printf(&quot;\n\n\nNote ID: &nbsp;%lX\n\n&quot;, dwNoteID); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
FieldFound = NSFItemIsPresent (hNote,</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ItemName, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; strlen (ItemName)); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
if (FieldFound) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
{ &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;len = NSFItemGetText ( &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; hNote, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ItemName, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ItemText, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; sizeof (ItemText)); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;if (fSealed) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp;printf (&quot;The %s field has been decrypted.\n&quot;, ItemName); &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;else &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp; printf (&quot;The %s field is not encrypted.\n&quot;, ItemName); &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;printf (&quot;Contents of %s field:\n\n%s\n&quot;, ItemName, ItemText); &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
} &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
/* If the specified field is not there, print a message. */</font></tt><br>
<br>
<tt><font size="2">else &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp;printf (&quot;%s field not found.\n&quot;, ItemName);</font></tt>
---
