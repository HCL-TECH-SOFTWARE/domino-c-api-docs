##### Chapter 8-3
##### Navigators

<b><font size="5" color="#000080">Overview</font></b><br>
Navigators are a specialized type of view. The header file vmods.h defines the on-disk structures for navigators. An early name for navigators was &quot;ViewMap&quot;; you will find that term used frequently in the data structure and symbolic constant names.<br>
<br>
Navigators introduce two item types, TYPE_VIEWMAP_DATASET and TYPE_VIEWMAP_LAYOUT. The data set record is stored in an item named $ViewMapDataset and contains control data and information about the default graphical display characteristics for different graphics features. The C API data structure contained in this item is VIEWMAP_DATASET_RECORD.   <br>
<br>
The actual graphical layout of the navigator is spelled out in the layout item named $ViewMapLayout. This item contains a VIEWMAP_HEADER_RECORD followed by a series of VIEWMAP_xxx CD records. Each graphical element in the navigator is stored in one of these records<font color="#FF0000"> </font>and might be a:<br>

<ul type="disc">
<li>Rectangle
<li>Polygon
<li>Text string
<li>Bitmap
<li>Hotspot region (an area of the display that responds to user actions)</ul>
<br>
Any layout record may be followed by an optional VIEWMAP_ACTION_RECORD, which contains information about the action to be performed if the user selects that graphical element. For example, a rectangle that opens a view when the user selects it is stored as a VIEWMAP_RECT_RECORD describing the rectangle followed by a VIEWMAP_ACTION_RECORD specifying the action to be performed. Actions include:
<ul>
<li type="disc">Opening a view
<li type="disc">Opening another navigator
<li type="disc">Opening a link
<li type="disc">Serving as an alias for a folder
<li type="disc">Running a formula
<li type="disc">Running a LotusScript script</ul>
<br>
Since navigators are graphical in nature, most applications do not need to deal directly with the on-disk storage formats. The Notes user interface support for navigator graphics design is much easier to work with. <br>
<br>
On the other hand, an application with a well-defined set of rules for creating graphics from data can generate the VIEWMAP_xxx CD records directly, and Notes can then display them as a navigator. For example, consider a program (or user) that adds a document note to a database once per day. This program or some other administrative program can then dynamically create a navigator layout item that acts as a document link to the database note, thus eliminating the time it takes to do so manually from the design interface. The sample program MAKENAV demonstrates how to create a navigator view and its graphical layout and action records in this manner.<br>
<br>
<br>
<b><font size="5" color="#000080">Creating a Navigator</font></b><br>
<br>
Navigators are implemented as a specialized type of View. They<font color="#FF0000"> </font>contain the view items $Title and $Flags and the navigator layout item $ViewMapLayout. The navigator design interface of Notes uses the navigator dataset item $ViewMapDataset as a means of defining the default graphics capabilities of a particular workstation. You do not need this item when creating a navigator because the CD records of the navigator layout item explicitly define this information for each navigator graphics instance. The following sections describe the items required to create a navigator view note and graphical objects.<br>
<br>
<b><font size="4" color="#000080">$Title</font></b><br>
The $Title item (VIEW_TITLE_ITEM) is of type TYPE_TEXT and contains a string specifying the name of the navigator view.<br>
<br>
<b><font size="4" color="#000080">$Flags</font></b><br>
For a navigator view note, the $Flags item (DESIGN_FLAGS) is of type TYPE_TEXT and contains the character sequence DESIGN_FLAG_VIEWMAP | DESIGN_FLAG_HIDE_FROM_V3.   <br>
<br>
<b><font size="4" color="#000080">$ViewMapLayout</font></b><br>
A single navigator view note can contain zero or more navigator layout items. The navigator layout item $ViewMapLayout (VIEWMAP_LAYOUT_ITEM) is of type TYPE_VIEWMAP_LAYOUT and consists of zero or more of the following CD record sequences and related packed data for describing the graphic layout and action associated with each navigator object instance in the view note. <br>
<br>
<b><font color="#000080">VIEWMAP_HEADER_RECORD</font></b><br>
The VIEWMAP_HEADER_RECORD is the first CD record in the navigator layout item. It has a CD record signature of SIG_CD_VMHEADER and contains a version field that should be set to the value VIEWMAP_VERSION (for Notes version compatibility). There can be only one navigator header record per navigator layout item. The NameLen field is reserved for future use and should be set to 0.
<ul></ul>
<b><font color="#000080">VIEWMAP_xxx_RECORD</font></b><br>
Following the navigator header record is a sequence of CD records that define the graphics information and action (if any) for each navigator object instance. The navigator graphics record is defined by the VIEWMAP_xxx_RECORD structure, where xxx can be one of the following values that correspond to the specified graphical elements and CD record signatures:<br>

<ul><b><u>Value	Graphic	CD record signature</u></b><br>
BITMAP	Bitmap	SIG_CD_VMBITMAP	<br>
<br>
POLYGON	Polygon	SIG_CD_VMPOLYGON<br>
	Polygon hotspot region	SIG_VM_POLYRGN<br>
<br>
POLYLINE  	Line of multiple segments  	SIG_CD_VMPOLYLINE	<br>
<br>
RECT	Rectangle 	SIG_CD_VMRECT<br>
	Ellipse	SIG_CD_VMELLIPSE<br>
	Rounded rectangle	SIG_CD_CMRNDRECT	<br>
	Button	SIG_CD_VMBUTTON	<br>
<br>
REGION	Rectangle hotspot region 	SIG_CD_VMREGION	<br>
<br>
TEXT	Text box	SIG_CD_VMTEXTBOX 	<br>
</ul>
Each navigator graphics record consists of a structure that defines the common composite data (including the CD record signature) for the graphical elements. This structure is of type VMODSdrobj (for BSIG signature objects) or VMODSbigobj (for WSIG signature objects).   Some of the fields in the common structure include the bounding rectangle coordinates (type VMODSrect) of the graphical object, the instance name and label name lengths, and the font ID and text color. Set<font color="#FF0000"> </font>the flags field to any combination of the VM_DROBJ_FLAGS_xxx constant values and the reserved Alignment field to 0. The remaining fields of the Navigator graphics record are specific to the graphical element being created -- for example, the data length of a bitmap or the number of points in a polygon.  <br>
<br>
The VIEWMAP_xxx_RECORD structure is followed by data in packed format, consisting of the name, the display label (if any), and any relevant data specific to the graphical element.<br>
<br>
<b><font color="#000080">VIEWMAP_ACTION_RECORD</font></b><br>
If the navigator graphics CD record has an associated action, it is next paired with a single navigator action CD record. This record is defined by the VIEWMAP_ACTION_RECORD structure and has a SIG_CD_VMACTION record signature.  <br>
<br>
The navigator action record structure contains fields that specify what --if anything -- happens when the<font color="#FF0000"> </font>current cursor is positioned over (touches) or selects the navigator graphic region.  When either of these two events occur, the graphics object can be temporarily highlighted, as defined by this Navigator action record. This is controlled by the bHighlightTouch, bHighlightCurrent structure fields, and defined by the HLOutlineColor, HLFillColor, HLOutlineWidth, and HLOutlineStyle structure fields.   <br>
<br>
The VM_ACTION_xxx value assigned to the ClickAction field of the navigator action record<font color="#FF0000"> </font>defines the action that occurs when a user selects (clicks)<font color="#FF0000"> </font>the navigator graphic. The values assigned to the remaining fields of the navigator action record, along with the packed data that follows the structure, are dependent on the specified ClickAction value. The following summarizes the different xxx values, the applicable navigator action record fields, and  the packed data elements.
<ul>	</ul>
<b><u>Value	Description	Applicable action fields	Packed data</u></b><br>
NONE	Take no action<br>
<br>
SWITCHVIEW	Open a view	ActionStringLen,	View name<br>
		ActionDataDesignType<br>
<br>
SWITCHNAV	Open another	ActionStringLen,	Navigator view <br>
	Navigator	ActionDataDesignType	name<br>
<br>
ALIAS_FOLDER	Serve as an alias	ActionStringLen,	Folder name<br>
	for a Folder	ActionDataDesignType<br>
<br>
GOTO_LINK	Open a link	LinkInfo<br>
<br>
RUNFORMULA	Run a formula	ExtDataLen	Compiled formula <br>
<br>
RUNSCRIPT	Run a LotusScript	ExtDataLen	Compiled script<br>
	script	<br>
<br>
<br>
<b><font size="5" color="#000080">The MAKENAV</font></b><b><font size="5" color="#000080"> Sample Program</font></b><br>
<br>
The sample program dbdesign\makenav automates the scenario where a navigator graphic, which links to a document created daily by some user or program, is added to a navigator view. The sample program creates a navigator view note in the sample database makenav.nsf. Each time the program runs it attempts to add a new navigator layout item to the navigator view. The layout item contains an instance of an ellipse that acts as a document link to the first document created in the database on the date the program runs. <br>
<br>
<b><font size="4" color="#000080">MAKENAV Program Flow</font></b><br>

<ol type="1">
<li>Open the sample database file and create a sample navigator view note if it does not already exist.  
<li>Set the view NOTE_CLASS to NOTE_CLASS_VIEW, set the title to &quot;Sample Navigator,&quot; and set the design flags to DESIGN_FLAG_VIEWMAP | DESIGN_FLAG_HIDE_FROM_V3.
<li>Search the MainView of the database for the first document created on the current date. Exit if there is no match; otherwise, derive the NOTELINK information for the view and document.
<li>Scan the navigator view note to determine the number of navigator layout items that exist in the navigator view. This lets the program intelligently place the new layout item graphic in a 'free' area and give it a unique instance and label name.<br>
Add the navigator layout item $ViewMapLayout to the navigator view note. The layout item contains the appropriate information for the following three CD records that make up the navigator instance:<br>
<br>
	VIEWMAP_HEADER_RECORD - only one per navigator view<br>
	VIEWMAP_RECT_RECORD - defines the ellipse characteristics and location<br>
	VIEWMAP_ACTION_RECORD - defines the action (document link to today's document)<br>

<li>Update the note (store it in the database) and close the database.</ol>
<br>
For coding details, refer to the MAKENAV sample program.
---
