##### Chapter 12-16
##### Outline Add-In Programs

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
You can add items to a Notes database outline control and configure Notes to call your API program each time the user interacts with one of these outline entries. The API program must be a Windows DLL that provides a outline add-in function. Install your DLL on the Notes workstation and configure Notes to load your DLL when the user starts running the workstation. Notes sends messages to your outline add-in function so that your function can extend the database outline and respond when the user selects your outline entries.<br>
<br>
You must specify the name of your outline add-in DLL in the AddInOutlines variable in the notes.ini file that configures the Notes workstation. To list multiple add-in DLL names, separate the names with a comma. For example, to add the DLLs outlineaddin1.dll and outlineaddin2.dll to the Notes workstation, add the following line to notes.ini:<br>

<ul>
<ul>AddInOutlines = OUTLINEADDIN1.DLL, OUTLINEADDIN2.DLL</ul>
</ul>
<br>
In this example, the add-in DLLs must reside in a directory in the path. Alternatively, you can specify the full path name of the DLLs in the notes.ini file.<br>
<br>
The name of the add-in DLL may begin with the platform specifier character used in the names of other Notes API add-in programs:   n under Windows 32-bit.  If the DLL name contains a platform specifier character, you may omit the character when specifying the name in the AddInOutlines variable in the notes.ini file.<br>
<br>
<br>
<b><font size="5" color="#000080">Technical Description</font></b><br>
<br>
An add-in DLL must  have the following entry point:
<ul>
<ul></ul>
NAORESULT LNCALLBACK AddinOutlineProc (WORD wMsg, void far *pParam);<br>
</ul>
wMsg is one of the following messages:
<ul><br>
NAOM_INIT<br>
NAOM_QUERY_OUTLINE<br>
NAOM_INIT_OUTLINE<br>
NAOM_QUERY_OPEN<br>
NAOM_OPEN<br>
NAOM_CLOSE<br>
NAOM_SELECT<br>
NAOM_POST_SELECT<br>
NAOM_DRAGDROP_DOC<br>
NAOM_TERM_OUTLINE<br>
NAOM_TERM
<ul></ul>
</ul>
pParam is message-specific data.<br>
<br>
The entry point can have any legal function name. You must declare the function in the EXPORTS section of the add-in's module definition (.def) file and assign it an ordinal value of 1.<br>
<br>
The add-in module must include addinout.h.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_INIT</font></b><br>
<br>
This message is sent after the DLL has been initially loaded.<br>
<br>
When the NAOM_INIT message is passed to AddinOutlineProc, pParam is unused, and AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_QUERY_OUTLINE</font></b><br>
<br>
This message is sent to the DLL when an outline has been created to determine if NAOM_INIT_OUTLINE should be invoked and the outline extended.<br>
<br>
When the NAOM_QUERY_OUTLINE message is passed to AddinOutlineProc, pParam is a pointer to a NAO_OUTLINE_INFO structure.
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_FORM_MAX];		<font color="#008000">/* Outline name */</font><br>
	<font color="#0000FF">char</font>				szAlias[DESIGN_FORM_MAX];		<font color="#008000">/* Outline alias */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Handle to current Db */</font><br>
	BOOL				bExtendOutline;				<font color="#008000">/* Indicates whether or not to extend outline */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_OUTLINE_INFO;<br>
<br>
When the NAOM_QUERY_OUTLINE message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
If bExtendOutline is set to TRUE then a subsequent call into the DLL will be made passing in the NAO_INIT_OUTLINE message.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_INIT_OUTLINE</font></b><br>
<br>
This message is sent to the DLL when an applicable outline has been initially created, as in a database open, in order to load the root entries of the extension.  <br>
When the NAOM_INIT_OUTLINE message is passed to AddinOutlineProc, pParam is a pointer to a NAO_ENTRY_INFO structure.<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">union</font><br>
{<br>
	<font color="#0000FF">char</font>				szFormula[NAO_LENGTH_FORMULA];	<font color="#008000">/* Formula */</font><br>
	<font color="#0000FF">char</font>				szURL[NAO_LENGTH_URL];		<font color="#008000">/* URL */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Database */</font><br>
	NOTEHANDLE			hNote;					<font color="#008000">/* Note */</font><br>
	NOTELINK			nlNoteLink;				<font color="#008000">/* Link */</font><br>
} NAO_ENTRY_RESOURCE;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Image name */</font><br>
	DBID				DbID;					<font color="#008000">/* Replica ID containing szImageName, if not current database */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Handle containing szImageName, if not current database and not on workspace */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_IMAGE_DATA;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	NAO_ENTRY_RESOURCE	EntryResource;				<font color="#008000">/* NAO_ENTRY_RESOURCE */</font><br>
	WORD				wEntryResourceType;			<font color="#008000">/* NAO_RESOURCE_XXX */</font><br>
	NAO_IMAGE_DATA		ImageData;				<font color="#008000">/* NAO_IMAGE_DATA */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_INFO;<br>
<br>
The NAO_ENTRY_DATA structure member dwParentID should be set to 0 for a root entry.<br>
<br>
When the  NAOM_INIT_OUTLINE message is passed, AddinOutlineProc returns one of the following values:<br>

<ul>
<ul>NAO_OPEN_CONTINUE	Requests Notes to send the NAOM_INIT_OUTLINE message again so that the DLL can add another outline entry.<br>
NAO_OPEN_STOP	Tells Notes that this DLL has no more outlines entries to add.<br>
</ul>
</ul>
The default image if left unspecified is the default database icon.<br>
The replica ID of the database containing the image only needs to be passed in if the image is not in the current database.<br>
The database handle of the database containing the image only needs to be passed in if the database is not currently on the user's workspace.  This will add a hidden entry on the workspace.  This is necessary if you<br>
plan to make use of remote images from another database.  This handle only needs to be passed in on the first usage of a given remote database.
<ul>
<ul></ul>
</ul>
More information on the NAO_RESOURCE_XXX flags is given below.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NAOM_QUERY_OPEN</font></b>
<ul>
<ul></ul>
</ul>
This message is sent to the DLL when an applicable outline entry has been expanded to determine if NAOM_OPEN should be invoked.<br>
<br>
When the NAO_QUERY_OPEN message is passed to AddinOutlineProc, pParam is a pointer to a NAO_SELECT_INFO structure<b>.</b>
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	WORD				wLevel;					<font color="#008000">/* Outline level, root = 0 */</font><br>
	BOOL				bNeedsRefresh;				<font color="#008000">/* Indicates outline refresh is needed */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_SELECT_INFO;
<ul>
<ul></ul>
</ul>
When the NAO_QUERY_OPEN message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
If bNeedsRefresh is set then the call to subsequent call into the DLL will be made passing in the NAOM_OPEN message.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NAOM_OPEN</font></b><br>
<br>
This message is sent to the DLL when an applicable outline entry has been expanded and the bNeedsRefresh field of the NAO_SELECT_INFO field has been set through the NAOM_QUERY_OPEN message.  The corresponding sub-entries are dynamically loaded.<br>
<br>
When the NAOM_OPEN message is passed to AddinOutlineProc, pParam is a pointer to a NAO_ENTRY_INFO structure.<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">union</font><br>
{<br>
	<font color="#0000FF">char</font>				szFormula[NAO_LENGTH_FORMULA];	<font color="#008000">/* Formula */</font><br>
	<font color="#0000FF">char</font>				szURL[NAO_LENGTH_URL];		<font color="#008000">/* URL */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Database */</font><br>
	NOTEHANDLE			hNote;					<font color="#008000">/* Note */</font><br>
	NOTELINK			nlNoteLink;				<font color="#008000">/* Link */</font><br>
} NAO_ENTRY_RESOURCE;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Image name */</font><br>
	DBID				DbID;					<font color="#008000">/* Replica ID containing szImageName, if not current database */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Handle containing szImageName, if not current database and not on workspace */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_IMAGE_DATA;<br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	NAO_ENTRY_RESOURCE	EntryResource;				<font color="#008000">/* NAO_ENTRY_RESOURCE */</font><br>
	WORD				wEntryResourceType;			<font color="#008000">/* NAO_RESOURCE_XXX */</font><br>
	NAO_IMAGE_DATA		ImageData;				<font color="#008000">/* NAO_IMAGE_DATA */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_INFO;<br>
<br>
When the  NAOM_OPEN message is passed, AddinOutlineProc returns one of the following values:<br>

<ul>
<ul>NAO_OPEN_CONTINUE	Requests Notes to send the NAOM_OPEN again so that the DLL can add another outline entry.<br>
NAO_OPEN_STOP	Tells Notes that this DLL has no more outlines entries to add.<br>
</ul>
</ul>
The default image if left unspecified is the default database icon.<br>
The replica ID of the database containing the image only needs to be passed in if the image is not in the current database.<br>
The database handle of the database containing the image only needs to be passed in if the database is not currently on the user's workspace.  This will add a hidden entry on the workspace.  This is necessary if you<br>
plan to make use of remote images from another database.  This handle only needs to be passed in on the first usage of a given remote database.
<ul>
<ul></ul>
</ul>
More information on the NAO_RESOURCE_XXX flags is given below.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_CLOSE</font></b>
<ul>
<ul></ul>
</ul>
This message is sent to the DLL when an applicable outline entry has been collapsed.<br>
<br>
When the NAOM_CLOSE message is passed to AddinOutlineProc, pParam is a pointer to a NAO_SELECT_INFO structure<b>.</b><br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	WORD				wLevel;					<font color="#008000">/* Outline level, root = 0 */</font><br>
	BOOL				bNeedsRefresh;				<font color="#008000">/* Indicates outline refresh is needed */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_SELECT_INFO;<br>
<br>
When the NAOM_CLOSE message is passed, AddinOutlineProc always returns NAO_NOERROR.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NAOM_SELECT</font></b><br>
<br>
This message is sent to the DLL when the user has selected one of the add-in outline entries<br>
<br>
When the NAOM_SELECT message is passed to AddinOutlineProc, pParam is a pointer to a NAO_SELECT_INFO structure<b>.</b><br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	WORD				wLevel;					<font color="#008000">/* Outline level, root = 0 */</font><br>
	BOOL				bNeedsRefresh;				<font color="#008000">/* Indicates outline refresh is needed */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_SELECT_INFO;
<ul>
<ul></ul>
</ul>
When the NAOM_SELECT message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
The NAOM_SELECT message is passed whenever the user has selected one of the add-in outline entries.  If a resource action is associated with the outline entry then NAOM_SELECT will be passed just prior to invoking the defined action.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NAOM_POST_SELECT</font></b><br>
<br>
This message is sent to the DLL after the user has selected one of the add-in outline entries<br>
<br>
When the NAOM_POST_SELECT message is passed to AddinOutlineProc, pParam is a pointer to a NAO_SELECT_INFO structure<b>.</b><br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	WORD				wLevel;					<font color="#008000">/* Outline level, root = 0 */</font><br>
	BOOL				bNeedsRefresh;				<font color="#008000">/* Indicates outline refresh is needed */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_SELECT_INFO;
<ul>
<ul></ul>
</ul>
When the NAOM_POST_SELECT message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
The NAOM_POST_SELECT message is passed whenever after user has selected one of the add-in outline entries that contains a resource link.  If the outline entry is a just a simple entry with no resource action associated with it then only the NAOM_SELECT message will be issued.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_DRAGDROP_DOC</font></b><br>
<br>
This message is sent to the DLL when documents are dragged and dropped from an add-in folder to another add-in folder, and add-in folder to a notes folder and a notes folder to an add-in folder.<br>
<br>
When the NAO_DRAGDROP_DOC message is passed to AddinOutlineProc, pParam is a pointer to a NAO_DRAGDROP structure<b>.</b><br>
<br>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_NAME_MAX];		<font color="#008000">/* Outline entry name, full title or named element */</font><br>
	DWORD			dwID;					<font color="#008000">/* Outline entry ID */</font><br>
	DWORD			dwParentID;				<font color="#008000">/* ID of parent outline entry */</font><br>
	DWORD			dwRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwSecRefID;				<font color="#008000">/* Outline reference ID, only used by DLL implementation */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_ENTRY_DATA;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	NAO_ENTRY_DATA		EntryData;				<font color="#008000">/* NAO_ENTRY_DATA */</font><br>
	WORD				wLevel;					<font color="#008000">/* Outline level, root = 0 */</font><br>
	BOOL				bNeedsRefresh;				<font color="#008000">/* Indicates outline refresh is needed */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_SELECT_INFO;
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	BOOL				bMove;					<font color="#008000">/* TRUE if MOVE, FALSE if COPY */</font><br>
	DWORD			dwCount;				<font color="#008000">/* Number of documents being dropped */</font><br>
	DBHANDLE			hSourceDb;				<font color="#008000">/* Source database handle for these notes */</font><br>
	HANDLE			hIDTable;				<font color="#008000">/* ID table of documents to drop into folder */</font><br>
	DBHANDLE			hDestDb;				<font color="#008000">/* Destination database handle for these notes */</font><br>
	NAO_SELECT_INFO		DestFolderInfo;				<font color="#008000">/* NAO_SELECT_INFO of destination folder */</font><br>
	BOOL				bNamedFolder;				<font color="#008000">/* TRUE if destination folder has a named folder element */</font><br>
	BOOL				bActionEntry;				<font color="#008000">/* TRUE if destination folder has a action element */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_DRAGDROP_DOC;<br>
<br>
When the NAOM_DRAGDROP_DOC message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
If the destination folder is an add-in folder then the NAOM_DRAGDROP_DOC message will be sent to the outline extension responsible for that folder regardless of the source folder.  If the destination folder is a notes folder and the source folder is an add-in folder then the NAOM_DRAGDROP_DOC message will be sent to the outline extension responsible for the source folder.  Drag / Drop functionality is not supported between two different outline extensions.<br>
<br>
In this context szName will contain the full title of the outline entry or if applicable the named element (folder) which the outline entry is associated.<br>
The hDestDB is a handle to the database where the destination <b>entry </b>is located.  The hSourceDB is a handle to the database containing the <b>notes </b>to be drag/dropped.<br>
<br>
<b><font size="4" color="#000080">NAOM_TERM_OUTLINE</font></b>
<ul>
<ul></ul>
</ul>
This message is sent to the DLL when an applicable outline has been removed, as in a database close.<br>
<br>
When the NAOM_TERM_OUTLINE message is passed to AddinOutlineProc, pParam is a pointer to a NAO_OUTLINE_INFO structure.
<ul>
<ul></ul>
</ul>
<font color="#0000FF">typedef</font> <font color="#0000FF">struct</font><br>
{<br>
	DWORD			dwSize;					<font color="#008000">/* Size of this structure */</font><br>
	<font color="#0000FF">char</font>				szName[DESIGN_FORM_MAX];		<font color="#008000">/* Outline name */</font><br>
	<font color="#0000FF">char</font>				szAlias[DESIGN_FORM_MAX];		<font color="#008000">/* Outline alias */</font><br>
	DBHANDLE			hDb;					<font color="#008000">/* Handle to current Db */</font><br>
	BOOL				bExtendOutline;				<font color="#008000">/* Indicates whether or not to extend outline */</font><br>
	DWORD			dwReserved1;				<font color="#008000">/* Reserved */</font><br>
	DWORD			dwReserved2;				<font color="#008000">/* Reserved */</font><br>
} NAO_OUTLINE_INFO;<br>
<br>
When the NAOM_TERM_OUTLINE message is passed, AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
bExtendOutline is always set to FALSE in the case of NAOM_TERM_OUTLINE.<br>
<br>
<br>
<b><font size="4" color="#000080">NAOM_TERM</font></b><br>
<br>
This message gives the DLL a chance to free any storage that it allocated before Notes frees it.<br>
<br>
When NAOM_TERM message is passed to AddinOutlineProc, pParam is unused, and AddinOutlineProc always returns NAO_NOERROR.<br>
<br>
<br>
<b><font size="5" color="#000080">Notes Outline Add-in resource values.</font></b><br>

<ul>
<ul><tt>NAO_RESOURCE_NONE		- No default resource action</tt><br>
<tt>NAO_RESOURCE_FORMULA	- Resource action is formula</tt><br>
<tt>NAO_RESOURCE_URL		- Resource action is a URL</tt><br>
<tt>NAO_RESOURCE_DB		- Resource action is a database handle</tt><br>
<tt>NAO_RESOURCE_NOTE		- Resource action is a note handle<br>
NAO_RESOURCE_NOTELINK	- Resource action is a Notes link</tt></ul>
</ul>
<br>
<br>
<b><font size="5" color="#000080">Notes Outline Add-in Template</font></b><br>
<br>
<a style="display: inline-block; text-align: center" href="../images/Outline_Add-In_Programs0.gif" title="outline_template.c"><img src="../images/Outline_Add-In_Programs1.gif" width="94" height="47" alt="outline_template.c" border="0"></a><br>
<br>
<br>
<b><font size="5" color="#000080">Known Limitations and Usage Restrictions</font></b><br>
<br>
Outline add-in programs are only supported on Windows 32-bit Notes clients.<br>
<br>
Right-Click menu options are not supported.<br>
<div align="center">----------------------------------------------------------------------------------------------------------<br>
</div><br>

---
