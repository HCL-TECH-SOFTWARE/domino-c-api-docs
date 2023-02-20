##### Chapter 9-12
##### Lightweight Directory Access Protocol (LDAP)

<b><font size="5" color="#000080">Overview </font></b><br>
<br>
The Lightweight Directory Access Protocol (LDAP) is an open industry standard that has evolved to provide an easy way to administer information that is to be shared among many distributed applications.  LDAP is based on a client-server model in which a client makes a TCP connection to an LDAP server, over which it sends requests and receives responses.<br>
<br>
LDAP defines a standard method for accessing and updating information in a directory.  A directory is a specialized database that lists information about objects, arranged in some order, that give details about each object.  A main difference between a directory and a general database is that a directory is accessed (read or searched) much more often than it is updated (written).  <br>
<br>
The information contained in an LDAP directory is based on an entry.  Entries are composed of attributes, which have a type and one or more values.  Each attribute has a syntax that determines what kinds of values are allowed in the attribute and how those values behave during directory operations.  Entries may be organized in a tree structure, usually based on political, geographical, and organizational boundaries.  Each entry is uniquely named relative to its sibling entries by its relative distinguished name (RDN) consisting of one or more distinguished attribute values from the entry.  At most one value from each attribute may be used in the RDN.  A globally unique name for an entry, called a distinguished name (DN), is constructed by concatenating the sequence of RDNs from the entry up to the root of the tree. <br>
<br>
The LDAP C API provides functions to authenticate, search for and retrieve information, modify information, and add and delete entries from the tree.  A thorough knowledge of the LDAP directory and its format, as well as Domino administration of the LDAP server and directory, are necessary prerequisites to using this API.  Please refer to the <i>Domino Administration Help</i> documentation for a complete description of LDAP administration.<br>
<br>
<b><font size="5" color="#000080">*Note:</font></b><br>
Starting with the HCL C API Toolkit 6.0.5/6.5.4, the ldap_xxx and ber_xxx function names have changed.  You may still use the same ldap_xxx and ber_xxx function names in your source code, but they are subject to the macro substitutions in ldap.h. This was done to prevent collisions with other ldap implementations, for example when Domino DB2 is configured to authenticate using ldap.  Only UNIX applications built prior to the HCL C API Toolkit 6.0.5/6.5.4 that use the ldap_xxx functions will be affected.  These applications must be rebuilt in order to run on Domino 7.0 or later so that they use the new macro substitutions.<br>
<br>
<br>
<b><font size="5" color="#000080">Getting Started</font></b><br>
<br>
The Lightweight Directory Access Protocol (LDAP) is a C API that lets you write your own applications that will send requests to, and receive responses from, an LDAP Server.  <br>
<br>
An LDAP application generally uses the LDAP C API in four simple steps:<br>

<ul>
<ol type="1">
<li>Initialize an LDAP session with a primary LDAP server. The ldap_init function returns a handle to the session, allowing multiple connections to be open at once.<br>

<li>Authenticate to the LDAP server. The ldap_simple_bind and related functions support a variety of authentication methods.<br>

<li>Perform some LDAP operations and obtain some results.   ldap_search and related functions return results which can be parsed by ldap_parse_result, ldap_first_entry, ldap_next_entry, etc.<br>

<li>Close the session. The ldap_unbind function closes the connection.<br>
</ol>
</ul>
Please see the <i>HCL C API Reference </i>for a detailed description of any of the functions mentioned or implied in this chapter.<br>
<br>
<br>
<b><font size="5" color="#000080">Synchronous vs. Asynchronous Operations</font></b><br>
<br>
Operations can be performed either synchronously or asynchronously depending on which type of function is called.  The names of the synchronous functions end in _s.   For example, a synchronous search can be completed by calling ldap_search_s while an asynchronous search can be initiated by calling ldap_search.  All synchronous routines return an indication of the outcome of the operation (e.g, the constant LDAP_SUCCESS or some other result code).  The asynchronous routines make available to the caller the message id of the operation initiated. This id can be used in subsequent calls to ldap_result to obtain the result(s) of the operation.  An asynchronous operation can be abandoned by calling ldap_abandon or ldap_abandon_ext.  Note that there is no requirement that an LDAP API implementation not block when handling asynchronous API functions; the term &quot;asynchronous&quot; as used in this document refers to the fact that the sending of LDAP requests can be separated from the receiving of LDAP responses.<br>
<br>
<br>
<b><font size="5" color="#000080">Obtaining results</font></b><br>
<br>
Many of the LDAP API routines return result codes, some of which indicate local API errors and some of which are LDAP resultCodes that are<br>
returned by servers.  All of the result codes are non-negative integers.  Results and errors are returned in an opaque structure called LDAPMessage.  Routines are provided to parse this structure, step through entries and attributes returned, etc.  Routines are also provided to interpret errors.<br>
<br>
The LDAP C API function ldap_result is used to obtain the result of a previous asynchronously initiated operation.  Note that depending on how it is called, ldap_result can actually return a list or &quot;chain&quot; of result messages.  The ldap_result function only returns messages for a single request, so for all LDAP operations, other than search, only one result message is expected; that is, the only time the &quot;result chain&quot; can contain more than one message is if results from a search operation are returned.  Once a chain of messages has been returned to the caller, it is no longer tied in any caller-visible way to the LDAP request that produced it.  However, it MAY be tied to the session handle.  Therefore, a chain of messages returned by calling ldap_result or by calling a synchronous search routine will never be affected by subsequent LDAP API calls except for ldap_msgfree (which is used to dispose of a chain of messages) and the unbind calls (which dispose of a session handle), or functions defined by extensions of this API.<br>
<br>
<br>
<b><font size="5" color="#000080">Lightweight Basic Encoding Rules (LBER)</font></b><br>
<br>
LBER is the Lightweight version of the Basic Encoding Rules (BER) for LDAP.<br>
<br>
The LDAP C API provides functions to encode and decode BER encoded ASN.1 values.  Abstract Syntax Notation One (ASN.1) is a language for defining standards. <br>
<br>
Note that the LBER-related functions defined in this API all provide a method for determining success or failure but generally do not provide access to specific error codes.  Therefore, applications that require precise error information when encoding or decoding ASN.1 values should not use these functions.<br>
<br>
Please see the HCL C API Reference Database for a detailed description of any of the functions or data types mentioned or implied in this chapter.<br>
<br>
<br>
<b><font size="5" color="#000080">Full LDAP Documentation</font></b><br>
<br>
<img src="../images/Lightweight_Directory_Access_Protocol_(LDAP)0.gif" width="32" height="32"><br>
<i>HCL C API Notes/Domino  Reference</i><br>
<br>
The <i>HCL C API Notes/Domino  Reference</i> is a Domino database included as part of the HCL C API Toolkit for Domino and Notes.  It documents the LDAP functions, data types, and symbolic values in detail.<br>
<br>
<br>
<b><font size="5" color="#000080">Sample program</font></b><br>
<br>
The sample program <i>ldap_msc</i>, located in the <i>admin</i> directory, is included as part of the HCL C API Toolkit for Domino and Notes.  This program is intended to illustrate the basic practical usage of a cross section of the Lightweight Directory Assistance Protocol (LDAP) functions, data types and symbolic values, as implemented via a C API program.<br>
				<br>
Using the LDAP functionality of the C API Toolkit for Notes/Domino, this program will:<br>
				
<ul>- Add an entry to an LDAP directory.<br>
- Modify the Relative Distinguished Name (RDN) of the new entry (deleting an identical entry if one exists.)<br>
- Perform a search of the directory based on a filter.<br>
- Perform a comparison of attribute values. </ul>

---
