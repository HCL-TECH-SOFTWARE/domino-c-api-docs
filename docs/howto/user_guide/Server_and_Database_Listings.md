##### Chapter 9-6
##### Server and Database Listings

The samples examined in this chapter demonstrate ways for a C API program to obtain a list of the HCL Domino Servers available in the environment and a list of the Domino databases on a HCL Domino Server.<br>
<br>
The first sample, SERVLIST, shows how to obtain a list of the known<font color="#FF0000"> </font>HCL Domino Servers on all network ports. servlist.c is in the directory samples\admin\servlist. SERVLIST is a Windows program that displays a dialog box showing all available servers, similar to the one displayed by File - Database - Open. SERVLIST is a spare but complete example of C API programming for Windows.<br>
<br>
The second sample, FIND_DBS, demonstrates how to use the C API function NSFSearch to find all the Domino databases in a subdirectory on a HCL Domino Server.  find_dbs.c is in the directory \samples\admin\find_dbs.<br>
<br>
<br>
<b><font size="5" color="#000080">Listing All Known Servers</font></b><br>
<br>
MainWndProc, the main Windows procedure, processes the FILE_GET_SERVER_LIST message by calling the function ServListDlg, which does the real work of the program.<br>
<br>
ServListDlg calls the C API function NSGetServerList to obtain a list of all servers available that are listed in the user's home/mail server's Domino Directory.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>servlist.c: Obtaining a List of Server Names</b></td></tr>
</table>
<br>
<tt><font size="2">BOOL LNPUBLIC ServListDlg(HWND hDlg, WORD message,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;WPARAM wParam, LPARAM lParam)<br>
{<br>
 &nbsp;STATUS &nbsp; &nbsp;sError = NOERROR; &nbsp; &nbsp; &nbsp; /* Error return from API routines. */<br>
 &nbsp;char &nbsp; &nbsp; &nbsp;ServerString[MAXPATH]; &nbsp;/* String to hold server names. &nbsp;*/<br>
 &nbsp;LPSTR &nbsp; &nbsp; szServerString = ServerString;<br>
 &nbsp;USHORT &nbsp; &nbsp;i; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Loop counter. */<br>
 &nbsp;HANDLE &nbsp; &nbsp;hServerList=NULLHANDLE; /* Handle returned by NSGetServerList */<br>
 &nbsp;BYTE far *pServerList; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Pointer to start of Server List */<br>
 &nbsp;WORD &nbsp; &nbsp; &nbsp;wServerCount; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Number of servers in list. */<br>
 &nbsp;WORD far *pwServerLength; &nbsp; &nbsp; &nbsp; &nbsp; /* Index to array of servername lens */<br>
 &nbsp;BYTE far *pServerName;</font></tt><br>
<br>
<tt><font size="2">&nbsp; switch (message)<br>
 &nbsp;{<br>
 &nbsp; &nbsp;case WM_COMMAND: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* message: received a command &nbsp; &nbsp; &nbsp;*/</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; switch (wParam)<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;case IDOK: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* &quot;OK&quot; box selected? &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp; &nbsp;EndDialog(hDlg, TRUE); &nbsp;/* Exits the dialog box. &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (TRUE);</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; }<br>
 &nbsp; &nbsp; &nbsp;break;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; case WM_INITDIALOG: &nbsp; &nbsp; &nbsp; &nbsp; /* message: initialize dialog box &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Get the list of available servers. Setting the first parameter<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;to NULL gets a list of known servers on all ports.<br>
 &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; sError = NSGetServerList( (char far *) NULL, &amp;hServerList);</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; if (sError != NOERROR)<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;char String[256];<br>
 &nbsp; &nbsp; &nbsp; &nbsp;OSLoadString(NULLHANDLE, ERR(sError), String, sizeof(String)-1);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;MessageBox (GetFocus(), String, &quot;Notes Error&quot;, MB_OK);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;return (TRUE);<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Lock the handle returned to get the list of servers. The buffer</font></tt><br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; &nbsp;* &nbsp;returned is in the following format:<br>
 &nbsp; &nbsp; &nbsp; *<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;The first WORD specifies the number of servernames in the buffer.<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;This is followed by a series of N WORDS (N being the number<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;of servernames in the buffer), specifying the length of each<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;servername (without any NULL terminator). This is then<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;followed by the packed list of servernames.<br>
 &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;First, get a pointer to the start of the buffer, and then<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;get the number of servernames in the list.<br>
 &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; pServerList &nbsp;= (BYTE far *)OSLockObject(hServerList);<br>
 &nbsp; &nbsp; &nbsp;wServerCount = *(WORD *)pServerList;</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Now, get a pointer to the first member in the array of<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;servername lengths.<br>
 &nbsp; &nbsp; &nbsp; */</font></tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; pwServerLength = (WORD *)(pServerList + sizeof(WORD));</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Now get a pointer to the first servername in the packed list.<br>
 &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; pServerName = (BYTE far *) pServerList + sizeof(wServerCount) +<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;((wServerCount) * sizeof(WORD));</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Copy each servername to a local character buffer, add a null<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;terminator, then add the server name to the listbox.<br>
 &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; for (i=0; i&lt;wServerCount; pServerName+=pwServerLength[i], i++)<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp;memmove (szServerString, pServerName, pwServerLength[i]);<br>
 &nbsp; &nbsp; &nbsp; &nbsp;szServerString[pwServerLength[i]] = '\0';<br>
 &nbsp; &nbsp; &nbsp; &nbsp;SendDlgItemMessage(hDlg, SERVLIST_LISTBOX, LB_ADDSTRING,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; (WORD) NULL, (LONG)(LPSTR) szServerString);<br>
 &nbsp; &nbsp; &nbsp;}</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /*<br>
 &nbsp; &nbsp; &nbsp; * &nbsp;Unlock and free the memory associated with the server list.<br>
 &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; OSUnlockObject (hServerList);<br>
 &nbsp; &nbsp; &nbsp;OSMemFree (hServerList);</tt><br>
<br>
<tt>&nbsp; &nbsp; }</tt><br>
<br>
<tt>&nbsp; &nbsp; return (FALSE); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* Didn't process a message. */<br>
}</tt><br>
<br>
ServListDlg calls the function NSGetServerList, specifying NULL as the first parameter. NSGetServerList returns a list of all servers known on the port named in its first parameter. If the first parameter is set to NULL, NSGetServerList returns a  list of all servers known on any network port. NSGetServerList gets the list of servers from the Server/Server view of the user's home server Domino Directory. Servers not listed there are not returned from NSGetServerList.<br>
<br>
NSGetServerList returns a handle to a buffer containing the list of server names. The buffer has the following format:<br>

<ul type="disc">
<li> One WORD containing a number N, the number of server names in the list, followed by 
<li>An array of N WORDs, each containing the length of the corresponding server name (without null terminator)
<li>A packed character list of server names</ul>
<br>
ServListDlg parses the buffer returned by NSGetServerList, adding each server name to a listbox. When it has processed all server names, ServListDlg returns and the listbox containing the server names is displayed.<br>
<br>
<br>
<b><font size="5" color="#000080">Listing All the Databases in a Directory</font></b><br>
<br>
find_dbs.c finds all the Domino databases in a directory. It works for local or remote databases and also lists any subdirectories it finds. Note the program's use of NSFSearch to find all the databases.
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>find_dbs.c: Using NSFSearch to Find Databases</b></td></tr>
</table>
<tt><font size="2">/* Call NSFSearch to find files in the directory. For each file found, <br>
call an action routine. */</font></tt><br>
<tt><font size="2">&nbsp; &nbsp;if (error = NSFSearch (<br>
 &nbsp; &nbsp; &nbsp;dir_handle, &nbsp; &nbsp; &nbsp; /* directory handle &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp;NULLHANDLE, &nbsp; &nbsp; &nbsp; /* selection formula &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* title of view in formula &nbsp; */<br>
 &nbsp; &nbsp; &nbsp;SEARCH_FILETYPE + /* search for files &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp;SEARCH_SUMMARY, &nbsp; /* return a summary buffer &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;FILE_DBANY + &nbsp; &nbsp; &nbsp;/* find any .NS? file &nbsp; &nbsp; &nbsp; &nbsp; */<br>
 &nbsp; &nbsp; &nbsp;FILE_DIRS + &nbsp; &nbsp; &nbsp; /* find subdirectories &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;FILE_NOUPDIRS, &nbsp; &nbsp;/* don't find the &quot;..&quot; dir &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* starting date &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;file_action, &nbsp; &nbsp; &nbsp;/* call for each file found &nbsp; */<br>
 &nbsp; &nbsp; &nbsp;NULL, &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* argument to action routine */<br>
 &nbsp; &nbsp; &nbsp;NULL)) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* returned ending date (unused) */</font></tt><br>
<br>
<tt><font size="2">&nbsp; &nbsp; &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;NSFDbClose (dir_handle);<br>
 &nbsp; &nbsp; &nbsp;return (ERR(error));<br>
 &nbsp; &nbsp; &nbsp;}</font></tt><br>
This call to NSFSearch directs it to search for all .ns? files and subdirectories (but not parent directories), return a summary buffer, and call file_action for each target found that matches the selection criteria.<br>
<br>
file_action does most of its work by calling print_file_summary. It is a useful routine to step through because it navigates a summary buffer. Here is an example of output from print_file_summary to check while you trace:
<table width="100%" border="1">
<tr valign="top"><td width="100%"><b>find_dbs.c: Output to Use for Stepping Through print_file_summary</b></td></tr>
</table>
         $TITLE:  API_DOC.NSF<br>
         $Path:  API_DOC.NSF<br>
         $Type:  $NOTEFILE<br>
         $Modified:  12/16/91 06:13:32 PM<br>
         $Length:  49152<br>
         $Info:  Notes API Docs
---
