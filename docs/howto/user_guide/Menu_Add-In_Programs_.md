##### Chapter 12-4
##### Menu Add-In Programs 

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
You can add items to the Notes workstation Actions menu and configure Notes to call your API program each time the user selects one of these menu items. The API program must be a Windows DLL that provides a menu add-in function. Install your DLL on the Notes workstation and configure Notes to load your DLL when the user starts running the workstation. Notes sends messages to your menu add-in function so that your function can initialize the Actions menu, enable or disable menu items, and respond when the user selects your menu item.<br>
<br>
You must specify the name of your menu add-in DLL in the AddInMenus variable in the notes.ini file that configures the Notes workstation. To list multiple add-in DLL names, separate the names with a comma. For example, to add the DLLs uiaddin1.dll and uiaddin2.dll to the Notes workstation, add the following line to notes.ini:<br>

<ul>
<ul>AddInMenus = UIADDIN1.DLL, UIADDIN2.DLL</ul>
</ul>
<br>
In this example, the add-in DLLs must reside in a directory in the path. Alternatively, you can specify the full pathname of the DLLs in the notes.ini file.<br>
<br>
The name of the add-in DLL may begin with the platform specifier character used in the names of other Notes API add-in programs:   n under Windows 32-bit.  If the DLL name contains a platform specifier character, you may omit the character when specifying the name in the AddInMenus variable in the notes.ini file.<br>
<br>
<br>
<b><font size="5" color="#000080">Technical Description</font></b><br>
<br>
An add-in DLL must  have the following entry point:
<ul>
<ul></ul>
NAMRESULT LNCALLBACK AddinMenuProc (WORD wMsg, void far *pParam);<br>
</ul>
wMsg is one of the following User Menu messages:
<ul>
<ul></ul>
NAMM_INIT<br>
NAMM_INITMENU<br>
NAMM_COMMAND<br>
NAMM_TERM
<ul></ul>
</ul>
pParam is message-specific data.<br>
<br>
The entry point can have any legal function name. You must declare the function in the EXPORTS section of the add-in's module definition (.def) file and assign it an ordinal value of 1.<br>
<br>
The add-in module must include addinmen.h.<br>
<br>
<br>
<b><font size="4" color="#000080">NAMM_INIT</font></b><br>
<br>
This message gives the DLL the opportunity to add one or more menu items to the Notes Actions menu. For each menu item, the DLL assigns the wMenuID and MenuItemName fields of the structure below. The DLL may assign a mnemonic to each added menu item by placing an ampersand (&amp;) next to the desired character in the MenuItemName field of this structure. This causes the character following the ampersand to be underlined in the Actions menu and allows the user to select the menu item with this key.<br>
<br>
When the NAMM_INIT message is passed to AddinMenuProc, pParam is a pointer to a NAM_INIT_INFO structure<b><font color="#FF0000">.</font></b>
<ul>
<ul><br>
<tt>typedef struct<br>
{<br>
	WORD wStartingID; &nbsp; &nbsp; /* Input: DLL must add this to its </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;menu item ID when specifying the</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;menu id to another module. */<br>
	WORD wMenuItemNumber; /* Input: Ascending ordinal number</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;for each call. */</tt><br>
<tt>	WORD wMenuID; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Output: DLL's Menu ID. */<br>
	char MenuItemName[MAX_ADDIN_MENU_NAME]; /* Output: Text of </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; menu item in LMBCS. */<br>
} NAM_INIT_INFO;</tt><br>
</ul>
</ul>
When the NAMM_INIT message is passed, AddinMenuProc returns one of the following values:<br>

<ul>
<ul>NAM_INIT_CONTINUE	Requests Notes to send NAM_INIT again so that the DLL can add another menu item.<br>
NAM_INIT_STOP	Tells Notes that this DLL has no more menu items to add.<br>
<br>
</ul>
</ul>
<b><font size="4" color="#000080">NAMM_INITMENU</font></b><br>
<br>
This message gives the DLL a chance to modify the attributes of its menu items (for example, enable, disable, gray, or check them).<br>
<br>
When the NAMM_INITMENU message is passed to AddinMenuProc, pParam is a pointer to a NAM_INITMENU structure.
<ul>
<ul><br>
<tt>typedef struct<br>
{<br>
	HMENU hMenu;		/* Handle of the Actions popup menu. */</tt><br>
<tt>	NAM_CONTEXT_DATA Data;	/* Context specific data */</tt><br>
<tt>} NAM_INITMENU_INFO;</tt><br>
</ul>
</ul>
When the NAMM_INITMENU message is passed, AddinMenuProc always returns NAM_NOERROR.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="4" color="#000080">NAMM_COMMAND</font></b><br>
<br>
This message is sent to the DLL when the user has selected one of its menu items.<br>
<br>
When the NAMM_COMMAND message is passed to AddinMenuProc, pParam is a pointer to a NAM_COMMAND_INFO structure<b><font color="#FF0000">.</font></b>
<ul>
<ul><br>
<tt>typedef struct<br>
{<br>
	HWND hNotesWnd; &nbsp; &nbsp; &nbsp; &nbsp; /* Handle of Notes main window </tt><br>
<tt>					 &nbsp; to use as parent. */<br>
					/* Also for use when sending </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;messages to Notes. */<br>
	WORD wMenuID; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* DLL's ID number of selected </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;menu item. */<br>
	NAM_CONTEXT_DATA Data; &nbsp;/* Context specific data */<br>
} NAM_COMMAND_INFO;</tt><br>
</ul>
</ul>
When the NAMM_COMMAND message is passed, AddinMenuProc always returns NAM_NOERROR.
<ul>
<ul></ul>
</ul>
While processing the NAMM_COMMAND message, the DLL can send back to Notes messages requesting Notes to take a particular action. The available messages are:
<ul>
<ul><br>
WM_ADDIN_REFRESH<br>
WM_ADDIN_IMPORT</ul>
</ul>
<br>
For example, to send WM_ADDIN_IMPORT back to Notes:<br>
	
<ul><tt>NAM_COMMAND_INFO *pCmdInfo = (NAM_COMMAND_INFO *)pParam;</tt><br>
<br>
<tt><br>
 &nbsp; SendMessage(pCmdInfo-&gt;hNotesWnd, WM_ADDIN_IMPORT, 0, (LONG)pInfo);<br>
</tt><tt>	 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt></ul>
<br>
These messages are described later under &quot;WM_ADDIN Messages.&quot;<br>
<br>
<br>
<b><font size="4" color="#000080">NAMM_TERM</font></b><br>
<br>
This message gives the DLL a chance to free any storage that it allocated before Notes frees it.<br>
<br>
When NAMM_TERM is passed to AddinMenuProc, pParam is unused, and AddinMenuProc always returns NAM_NOERROR.
<ul>
<ul><br>
</ul>
</ul>
<b><font size="5" color="#000080">Structures</font></b>
<ul>
<ul><br>
<tt>typedef struct<br>
{<br>
	EDITIMPORTDATA Import; &nbsp; /* defined in ixedit.h */<br>
	EDITEXPORTDATA Export; &nbsp; /* defined in ixedit.h */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; char CaretFieldName[34]; /* field name of</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; current cursor position */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; WORD CaretFieldType; &nbsp; &nbsp; /* field type of current cursor </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; position */<br>
} EDITIXDATA;</tt><br>
<br>
<tt>typedef struct<br>
{<br>
	FLAG Context:3; &nbsp; &nbsp; /* Notes context: &nbsp;Desk, View, </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Editor R/W, Editor R/O */<br>
	FLAG fCanExport:1; &nbsp;/* TRUE if the add-in can perform </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;an export. */<br>
	FLAG fCanImport:1; &nbsp;/* TRUE if the add-in can request an </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;import. */<br>
	union<br>
	{<br>
		EDITIXDATA Edit;<br>
		VIEWIXDATA View; &nbsp; /* defined in ixview.h */<br>
	} IXData;<br>
} NAM_CONTEXT_DATA;</tt><br>
</ul>
</ul>
These structures provide import/export data to the add-in DLLs. The Context member of NAM_CONTEXT_DATA indicates the Notes context when the menu item was selected. It has<b><font color="#FF0000"> </font></b>one of the following values:<br>
<br>
NAM_IN_DESK	<b><font color="#FF0000">	</font></b>In the desktop<br>
NAM_IN_VIEW	<b><font color="#FF0000">	</font></b>In a view<br>
NAM_IN_VIEW_DESIGN	Designing a view<br>
NAM_IN_EDIT_RO	In a read-only document<br>
NAM_IN_EDIT_RW	In a document - edit mode<br>
NAM_IN_EDIT_DESIGN	Designing a document<br>
<br>
The CaretFieldName member of the EDITIXDATA structure gives the name of the field containing the cursor when the menu item was chosen. The CaretFieldType member of the EDITIXDATA structure gives the type of the field containing the cursor when the menu item was chosen. It has<b><font color="#FF0000"> </font></b>one of the following values:<br>
<br>
FIELD_TYPE_ERROR	Field type could not be determined<br>
FIELD_TYPE_NUMBER	Number field<br>
FIELD_TYPE_TIME	Time field<br>
FIELD_TYPE_RICH_TEXT	Rich text field.<br>
FIELD_TYPE_AUTHORS	Authors field<br>
FIELD_TYPE_READERS	Readers field.<br>
FIELD_TYPE_NAMES	Names field<br>
FIELD_TYPE_KEYWORDS	Keyword field<br>
FIELD_TYPE_TEXT	Plain text field.<br>
FIELD_TYPE_SECTION	Section field<br>
<br>
<br>
<b><font size="5" color="#000080">WM_ADDIN Messages</font></b><br>
<br>
Add-in menu DLLs can request the Notes workstation to perform certain actions while processing one of their menu commands. In all cases, the wParam of the message is unused and the lParam is set to point to the NAM_COMMAND_INFO structure that was passed to the DLL when the user selected the menu item. Also, in all cases, the return value from the message is a STATUS code.<br>

<ul>
<ul>WM_ADDIN_REFRESH	Tells Notes to refresh the current view.<br>
WM_ADDIN_IMPORT	Tells Notes to import to the editor the CD scratch file specified in the context block.</ul>
</ul>
<br>
<br>
<b><font size="5" color="#000080">Known Limitations and Usage Restrictions</font></b><br>
<br>
Menu add-in programs are only supported on Windows 32-bit Notes clients.<br>
<br>
The add-in DLL cannot add popup menus to the Notes Actions menu. It can only add menu items.
---
