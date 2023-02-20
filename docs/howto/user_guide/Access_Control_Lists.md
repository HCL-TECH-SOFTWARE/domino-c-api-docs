##### Chapter 9-2
##### Access Control Lists

All Domino databases contain an access control list. Access control lists are used to determine the level of access that users and servers have to a database.  Refer to the  <i>Notes 8.0  Help</i> database for details about access control lists.<br>
<br>
The HCL C API for Domino and Notes contains a set of access control list functions to access and modify the access control list for a database. The sample program ADMIN\ACLS demonstrates many of these routines. For more information, refer to this sample and the Access Control List functions in the <i>Reference.</i><br>
<br>
To specify a hierarchical user name in a call to one of the Access Control List functions, use the fully distinguished name. A fully distinguished name is in canonical format; that is, it contains all possible naming components. For example, Mary Lee/Sales/Acme is an abbreviated name. CN=Mary Lee/OU=Sales/O=Acme is the fully distinguished name. For more information on converting and parsing distinguished names, refer to the Distinguished Name C API functions.
---
