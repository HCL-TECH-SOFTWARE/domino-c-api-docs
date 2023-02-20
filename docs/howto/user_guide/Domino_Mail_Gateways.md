##### Chapter 10-4
##### Domino Mail Gateways

The sample MGATE is a fairly sophisticated program that demonstrates the basic steps involved in exchanging messages between Domino mail and another electronic mail system.  While a full discussion of MGATE is beyond the scope of this <i>User Guide,</i> this chapter briefly describes how MGATE operates.<br>
<br>
<br>
<b><font size="5" color="#000080">Sending Outbound Messages</font></b><br>
<br>
Outbound messages originate from a Domino user and are destined for someone outside the Domino mail system.<br>
<br>
Outbound messages are first routed through a foreign domain (created for messages to this particular foreign mail system) to a gateway mail file. The gateway mail file holds the messages until MGATE is ready to transfer them to the foreign users. Based on the modification time of the gateway mail file, MGATE detects pending outbound messages.<br>
<br>
When MGATE finds an outbound message, it delivers the message to a directory with the same name as the foreign user. In this sample program, all foreign user names must be eight characters or less. All foreign user directories are in the subdirectory \mgate\user.<br>
<br>
After delivery, the outbound message is a plain character text file. Each line of the file begins with one of the following item codes:<br>
<br>
A - Attachment (path name of attachment file, original file name)<br>
B - Body text line<br>
C - CC name<br>
D - Time/date<br>
O - Originator name<br>
S - Subject<br>
T - To name<br>
<br>
Following the item code on each line are the item contents. <br>
<br>
If MGATE does not find a directory for the foreign user, it continues to look for the directory during every outbound attempt until the mail times out. When an outbound message times out, MGATE sends a failure report to the mail sender.<br>
<br>
<br>
<b><font size="5" color="#000080">Receiving an Inbound Message</font></b><br>
<br>
An inbound message is one that originates outside of Domino and is destined for a Domino user.<br>
<br>
MGATE looks for inbound messages in the \mgate\inbound directory. This directory is scanned periodically, based on the number of minutes specified by the environment variable MgateInterval. When an inbound message is found, MGATE transforms it into a Domino mail message and passes it to the local mail router. <br>
<br>
If Domino cannot deliver the message, MGATE returns it to the sender's directory under \mgate\user.<br>
<br>
Message files may have any name, as long as they have the extension .msg. Attachments files may have any name, as long as they have the extension .att.<br>
<br>
In an inbound message file, the first character of each line is one of the following item codes:<br>
<br>
A - Attachment (path name of attachment file, original file name)<br>
B - Body text line<br>
C - CC name<br>
D - Time/date<br>
O - Originator name<br>
R - Recipient (full email address)<br>
S - Subject<br>
T - To name<br>
<br>
Following the item code on each line are the item contents. Items can be repeated as many times as necessary and in any order.
---
