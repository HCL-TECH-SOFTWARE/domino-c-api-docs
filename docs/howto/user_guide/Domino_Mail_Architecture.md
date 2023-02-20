##### Chapter 10-2
##### Domino Mail Architecture

<b><font size="5" color="#000080">Audience</font></b><br>
<br>
This chapter explains the Domino mail system from the perspective of the C API programmer. Read this chapter if you need to implement a mail gateway or mail-enabled application using the Domino Mail Gateway API or the NSF family of C API functions. <br>
<br>
<b><font size="5" color="#000080">How Domino Mail Works</font></b><br>
<br>
<b><font size="4" color="#000080">The Mailer, the Router, and the Domino Directory</font></b><br>
<br>
The important components of mail in Domino include the mailer, the router, and the Domino Directory.<br>
<br>
The mailer is part of the Notes workstation. It handles the Mail menu Send and Forward commands. The Notes Editor invokes the mailer when the document should be sent. The router is the Domino server process that routes mail from server<font color="#FF0000"> </font>to<font color="#FF0000"> </font>server and from network to network. The Domino Directory is a database that provides directory services to the mailer, router, and other mail programs. Directory services provided by the Domino Directory include mapping a<font color="#FF0000"> </font>user name to a mail address and network topology information.<br>
<br>
<br>
<b><font size="4" color="#000080">Mail Files</font></b><br>
<br>
Each Domino-enabled mail user has a mail database, created by Domino during new user registration and referred to as a &quot;Mail File&quot; in the Register New User dialog box. The user's mail file resides on the Domino Server designated as that user's mail server. The Person record in the Domino Directory identifies the user's mail file and mail server. The mail file is an ordinary database (.nsf file) normally named with the user's first initial and last name<font color="#FF0000"> </font>(for example, ksmith.nsf).<br>
<br>
<br>
<b><font size="4" color="#000080">mail.box </font></b><br>
<br>
One or more mail.box files may reside on every Domino mail server (i.e.: &quot;mail.box&quot; or &quot;mail1.box&quot;, &quot;mail2.box&quot;, ... &quot;mail10.box&quot;). The mail.box file is an ordinary database in that it has the same structure as an .NSF file, but normally only the mailer and the router access a mail.box file. <br>
<br>
When the user sends mail, the mailer moves the message from the user's mail file to the mail server's mail.box file, causing the router to deliver the message. The router periodically scans its mail.box file for mail messages. When it finds a message, it attempts to deliver it.  To access a mail.box file through a server  using the C API, it is best to use the symbolic value MAILBOX_NAME to insure that the message is deposited in an active mail.box file in the event of multiple mail.box files.  To deposit a message locally, it is the developer's responsibility to determine which mail.box file(s) is active.<br>
<br>
<br>
<b><font size="4" color="#000080">Messages</font></b><br>
<br>
The user's mail file is a database that contains data notes. We refer to these data notes as &quot;messages.&quot; <br>
<br>
A normal message is a data note with the Form item set to &quot;Memo.&quot;  A message composed using Memo contains the text items From, SendTo, CopyTo, BlindCopyTo, and Subject.  A message also contains a rich text item named Body. <br>
<br>
The fields defined by the form Memo (From, SendTo, and so on) are common to most mail messaging systems. However, not all Domino messages are composed using the form Memo. Also, details of the Memo form may differ from system to system. The Memo form you use may define other fields or redefine the normal fields. Use the File - Document Properties command to examine the items in any document.<br>
<br>
<b><font size="4" color="#000080">Recipients</font></b><br>
<br>
The Recipients field is the only field required by the Domino router to deliver a message. This distinction between the Recipients field and other fields in the document allows Domino to use the router to send any document, regardless of the form used to compose it.<br>
<br>
Recipients is a text list field. Each text item in the list is a full mail address that names a user or  group that will receive a copy of the document. A full mail address is a string of the form USERNAME@DOMAIN. The @DOMAIN part is optional if the user resides in the current router's domain.<br>
<br>
Before the mailer copies a message to the mail.box file, it attempts to look up in the Domino Directory each name specified in the SendTo, CopyTo, and BlindCopyTo items of the message. The mailer interacts with the user to resolve misspelled names, non-unique names, and names it cannot find in the Domino Directory. The mailer expands group names to their constituent user names and expands user names to include the domain if the domain differs from the current router's domain. If a forwarding address is specified, the mailer replaces the name with its forwarding address. If a name specified in the SendTo, CopyTo, or BlindCopyTo list contains explicit &quot;@&quot; routing, the mailer does not attempt to look up that name in the Domino Directory unless the message is being encrypted, in which case it needs the recipient's public key. <br>
<br>
Using the information it gets from the Domino Directory, the mailer builds the Recipients item of the message. All messages delivered to a mail.box file must have a Recipients item. The router then uses this Recipients item to route and deliver the message. <br>
<br>
Note that from an API program or from the Notes UI, the domain name is case-sensitive. If you develop a program that specifies a domain name explicitly (not obtaining it from the Domino Directory), that domain name must agree in case with the domain name listed in the Domino Directory. <br>
<br>
The mailer is responsible for eliminating duplicate entries in the Recipients list before storing the message in the mail.box file. The router places one copy of the message in the mail file for each recipient, so duplicate entries in the Recipients list<font color="#FF0000"> </font>means that the referenced recipient receives duplicate messages. <br>
<br>
The Domino mailer expands all group names to eliminate duplicates unless the group name is followed by an @DOMAIN that indicates that the group is not defined in the Domino Directory.<br>
<br>
If a group is defined in a foreign domain's Domino Directory, the Recipients field may contain a recipient of the form GROUPNAME@DOMAIN. The router can expand these distribution lists so that users can send messages to a group defined in a foreign domain.
---
