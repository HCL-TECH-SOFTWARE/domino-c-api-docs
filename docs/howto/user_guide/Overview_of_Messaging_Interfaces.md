##### Chapter 10-1
##### Overview of Messaging Interfaces

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
You can send Domino mail via a C API program in two ways:<br>

<ul type="disc">
<li>Using the Domino Mail Gateway API
<li>Using the HCL C API NSF functions</ul>
<br>
This chapter introduces these two methods, compares them to one another, and identifies the particular advantages of each.<br>
<br>
Although programs can mix functionality from these two methods in a single application, this chapter distinguishes between them to clarify the intended purpose of each. <br>
<br>
The Domino Mail Gateway API is a subset of the HCL C API for Notes/Domino. It consists of the set of functions starting with the prefix &quot;Mail.&quot; Subsequent chapters explain the Domino Mail Gateway API in more detail.<br>
<br>
The C API NSF functions is a subset of the HCL C API, consisting of the set of functions starting with the prefix &quot;NSF&quot;.  <br>
<br>
<br>
<b><font size="5" color="#000080">Domino Mail Gateway API</font></b><br>
<br>
The Domino Mail Gateway API consists of a subset of the functions in the HCL C API for Notes/Domino. This subset helps you implement  mail gateway programs. Each of the  Mail Gateway API functions starts with the prefix &quot;Mail&quot; (for example, MailCreateMessage). These functions simplify the process of manipulating mail messages.<br>
<br>
<br>
<b><font size="4" color="#000080">Capabilities of the Domino Mail Gateway API</font></b><br>
<br>
The Domino Mail Gateway API provides a complete set of functions for manipulating mail messages and are particularly useful in the context of a HCL Domino Server add-in task. Mail Gateway API functions let you:<br>

<ul type="disc">
<li>Access message files
<li>Create and manipulate lists of messages
<li>Create and delete messages
<li>Get and set message items (for example, &quot;Recipients&quot;)
<li>Look up mail addresses and parse mail addresses
<li>Attach and extract data files from messages
<li>Transfer messages to the Domino Mail Router
<li>Send delivery or non-delivery reports</ul>
<br>
<br>
<b><font size="4" color="#000080">Advantages of the Domino Mail Gateway API</font></b><br>
<br>
The Domino Mail Gateway API is optimized to manipulate mail messages. Use Mail Gateway API functions to manipulate fields common to typical electronic mail communication packages such as SendTo, CopyTo, From, and Subject. Procedures that access message files, manipulate message lists, and look up addresses require fewer steps with Mail Gateway functions than equivalent functionality that uses NSF functions.<br>
<br>
<br>
<b><font size="4" color="#000080">Limitations of the Mail Gateway API</font></b><br>
<br>
Programs based on the Mail Gateway API work only with Domino.<br>
<br>
The Domino Mail Gateway API does not provide direct access to all fields of all Domino documents. It only provides access to fields found in typical mail messages such as SendTo, CopyTo, and Subject. Domino lets you &quot;mail&quot; virtually any document (that is, send it to a database using the Domino Mail Router). A mail-enabled Domino application may have fields not found in typical mail messages.<br>
 <br>
For example, a Domino application might send a document containing fields named &quot;LoanMaturityDate&quot; and &quot;PaymentSchedule.&quot; The Domino Mail Router can send this document, but the Mail Gateway API cannot directly access the atypical fields of that message. In this example, a gateway program might use Mail Gateway API functions to access fields such as SendTo and Subject and standard NSF functions to access fields such as &quot;LoanMaturityDate.&quot;<br>
<br>
The Domino Mail Gateway API does not determine the user's mail server or submit a message to a remote mail.box file. Therefore, although the Mail Gateway API functions are good for creating a new message, they are only appropriate for submitting the message to the Domino Mail Router if the calling program runs directly on a mail server.<br>
<br>
<br>
<b><font size="4" color="#000080">For More About the Mail Gateway API</font></b><br>
<br>
Subsequent documents in this guide discuss Domino Mail and the Mail Gateway API. Also see the <i>Reference</i> and the sample programs MGATE, READMAIL, and SENDMAIL. <br>
<br>
<br>
<b><font size="5" color="#000080">HCL C API NSF Functions</font></b><br>
<br>
The HCL C API NSF functions <font color="#FF0000"> </font>provide the lowest-level, most general interface to mail.  They provide complete access to all types of Domino databases and documents. Since programmatic access to Domino mail is based entirely databases and documents, the HCL C API provides all the functionality necessary to send and receive messages in any context.<br>
<br>
<b><font size="4" color="#000080">Capabilities of the </font></b><b><font size="4" color="#000080">HCL C API NSF Functions</font></b><br>
<br>
You can use the standard HCL C API functions for Domino and Notes to create mail-enabled workstation applications, HCL Domino Server add-in tasks, Notes workstation add-in programs, or import/export DLLs. For a more detailed explanation of the capabilities of the C API, see &quot;Overview of the HCL C API for Domino and Notes.&quot;<br>
<br>
<br>
<b><font size="4" color="#000080">Advantages of the </font></b><b><font size="4" color="#000080">HCL C API NSF Functions</font></b><br>
<br>
The main advantage of the HCL C API NSF functions is that they provide complete access to all types of Domino databases and documents.  You need to use the HCL C API NSF functions to manipulate forms, views, or fields of documents that do not fall within the set of items in typical mail messages. Any C API application based on a mail-enabled Domino database with fields other than SendTo, CopyTo, and so on requires use of the NSF family of C<font color="#FF0000"> </font>API functions.<br>
<br>
<br>
<b><font size="4" color="#000080">Limitations of the </font></b><b><font size="4" color="#000080">HCL C API NSF Functions</font></b><br>
<br>
A serious limitation of programs that access mail via NSF functions is that such programs may become incompatible with future releases of Domino. For example, R5 of Domino introduced the ability to have more than one mail.box file on the server.  Previous programs that directly access the &quot;mail.box&quot; locally will no longer work with this configuration.  Other problems may arise when such programs depend explicitly on names and meanings of fields in the mail database.  A program that &quot;hard-codes&quot; item names and data types may require maintenance if the design of the mail database changes in future versions of Domino.<br>
<br>
Like the Domino Mail Gateway API, the HCL C API NSF functions do not provide independence from Domino. Programs based on the HCL C API work only with Domino or Notes.<br>
<br>
Because the HCL C API NSF functions provide the lowest-level interface to mail, many common mail-enabled application tasks that you can  accomplish with a single Mail Gateway API function call require multiple function calls with the C<font color="#FF0000"> </font>API NSF functions.<br>
<br>
<br>
<b><font size="4" color="#000080">For More About the C API</font></b><br>
<br>
Subsequent documents in this guide discuss Domino Mail in more detail. See also the<font color="#FF0000"> </font><i>Reference </i>and the sample program SENDMEMO.
---
