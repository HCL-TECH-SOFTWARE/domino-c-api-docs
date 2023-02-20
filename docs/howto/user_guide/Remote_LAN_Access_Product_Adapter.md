##### Chapter 12-14
##### Remote LAN Access Product Adapter

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
<b><font size="4" color="#000080">Overview</font></b><br>
<br>
This chapter describes how to write an adapter to go between Notes and a remote access product. This allows Notes users to use a remote access product other than Microsoft Remote Access Service (RAS) or AppleTalk Remote Access (ARA). Examples of other remote access products include Lan Distance, NetWare Connect, and Shiva.<br>
<br>
The adapter, which is referred to here as an RLAN adapter, must be a DLL or shared object.  It must reside in the Notes executable directory. <br>
<br>
The use of this adapter requires a modification to the Server Connection document of type Remote LAN Service in the user's Address Book.  You must add an option corresponding to the new remote access service type and provide fields to store any required parameters.  To do this, you must create a new subform and add it to the user's Address Book, as described in the next section.  After you add the subform, you can create a Server Connection document, select Remote LAN Service as the Connection Type, and select your remote access method as the service type.<br>
<br>
Release 4 of Notes supported Version 0 of the Remote LAN interface.  Release 5 of Notes supports Version 1 of the Remote LAN interface.  This chapter documents Version 1.  Additional entry points have been added since version 0 and the form of the connection document subform has been redefined.  Connection documents created to version 0 of the interface should still function in this new definition.<br>
<br>
<b><font size="4" color="#000080">Creating a Remote LAN Service Subform</font></b><br>
<br>
To make a new, different, or modified remote LAN technique available to end users, you must create a new subform and add it to the users' Address Book. This subform must include the full name of the adapter and an abbreviated name that matches the adapter's filename. Follow these steps to create the subform:<br>
<br>
1.  Open the Address book and select Create - Design - Subform to open the subform design window.<br>
<br>
2.	Select  Design - Subform Properties to open the Subform infobox.<br>
<br>
3.	Enter the name of the new subform. The subform name must be made up of three parts, separated by vertical bars:
<ul>
<ul>
<ul type="disc">
<li>$RLAN, followed by the driver name (without a platform prefix)
<li>The descriptive string displayed to users when they open the Connection document and choose a Remote LAN Service type
<li>The driver name (without platform prefix)</ul>
</ul>
</ul>

<ul><br>
For example:<br>

<ul>$RLANRAS | Microsoft Remote Access Service | RAS<br>
</ul>
</ul>
4.	The subform must consist of ten fields, consisting of five pairs of fields. Each pair consists of a static text field and its associated user input field, as described below:  <br>

<ul>
<ul>
<ul type="disc">
<li>The first five fields must be called StaticTag, Static1, Static2, Static3, and Static4. Even if you don't use all the fields, each must be present and must contain the following type of formula:<br>
- the driver name (without platform prefix), followed by <br>
- the three characters &quot;$%^&quot;, followed by <br>
- the string representing the static text you want to display for each of the input values<br>
<br>
If you do not have any text to display, the formula still must contain the name of the driver and the three characters. For example:<br>
<br>
&quot;ARA$%^Connection document location:&quot;<br>
&quot;RAS$%^&quot;<br>
<br>
The static fields should be hidden on the subform and appear above the layout region.<br>

<li>The second five fields must be called RLANTag, RLAN1, RLAN2, RLAN3, and RLAN4. These fields should be placed in a layout region that contains at least these five fields plus the same static text used in the the static fields describing the input fields (see above). There are no restrictions on the default, input translation, or validation formulas for the input fields. As with the static fields, even if you don't need five input fields, each must be on the subform. If you do not need the user to input any data into one of the input fields, it can be hidden. <br>
</ul>
</ul>
</ul>
5.	The subform and the driver must be installed on the machine that will use the Remote LAN Access Product. Note that for the user to fill out a connection record, only the subform is required. <br>
<br>
6.	Check &quot;Do not allow design refresh/replace to modify&quot; to ensure that the subform is not deleted when  Design Replace or Refresh is run on the Address Book.  As an alternative, you can specify a different template to inherit from instead of the standard  Address book design template.<div align="center"><br>
<img src="../images/Remote_LAN_Access_Product_Adapter0.gif" width="426" height="229"></div><br>
			<br>
The following sections list the API calls designed for the RLAN adapter and show a pseudocode program of an example adapter. <br>
<br>
<br>
<b><font size="5" color="#000080">Header Files</font></b><br>
<br>
The RLAN adapter may require the following HCL C API header files for Domino and Notes:<br>
<br>
#include &quot;global.h&quot; <br>
#include &quot;misc.h&quot;<br>
#include &quot;net.h&quot;<br>
#include &quot;neterr.h&quot;<br>
#include &quot;oserr.h&quot;<br>
#include &quot;osmisc.h&quot;<br>
<br>
<b><font size="5" color="#000080">Required Adapter Functions</font></b><br>
<br>
The RLAN adapter must define two functions that Notes will call. The first function is an initialization routine that registers the adapter with Notes by providing the address of the second function. The second function provides a single entry point to perform all other functions of this adapter.<br>
<br>
Under Windows, any legal function name is valid for the initialization function. Under Windows, you must declare the function in the EXPORTS section of the add-in's module definition (.DEF) file and assign it an ordinal value of 1. Notes calls this function by using the ordinal value of 1.<br>
<br>
The second function may have any legal function name and need not be assigned an ordinal value, since Notes will use its address to call this function.<br>
<br>
<b>MainEntryPoint</b><br>
STATUS LNCALLBACK<font color="#FF0000"> </font>MainEntryPoint(<br>
<b><font color="#FF0000">	</font></b>WORD<b><font color="#FF0000"> </font></b> *pVersion,<br>
<b><font color="#FF0000">	</font></b>PREMOTE_LAN_SERVICE_ENTRY <b><font color="#FF0000"> </font></b>*rtnGeneralEntryPoint,<br>
	PREMOTE_LAN_STATUS_CALLBACK <b><font color="#FF0000"> </font></b>Callback)<br>
<br>
This initializes the Notes interface. It receives and records the status callback function address and returns the address of the general entry point (the entry point that performs all other functions) to this DLL or shared object. It is called once for each process in which Remote LAN is used.<br>
<br>
<br>
<b>Inputs:</b><br>
pVersion	Pointer to a location containing the Remote LAN  version supported by the calling version of Notes. Notes release 4.5 and 4.6 support Remote LAN Version 0.  Notes Release 5 support Version 1.<br>
<br>
Callback	Address of a routine in Notes to call from the adapter to report ongoing status (see StatusDisplayCallback below).<br>
<br>
<b>Outputs:</b><br>
pVersion	Address in which to return the Remote LAN version supported by this adapter. Notes will adapt its expectations to this version. It must be equal to or less than the value supplied by Notes.<br>
<br>
*rtnGeneralEntryPoint	Address in which to return the general entry point  for all other calls to this DLL or shared object.<br>
<br>
<br>
(routine)	A Notes error code.  Return NOERROR if no error has occurred.<br>
<br>
<br>
<b>GeneralEntryPoint</b><br>
STATUS LNCALLBACK<font color="#FF0000"> </font>GeneralEntryPoint(<br>
<b><font color="#FF0000">	</font></b>VARARG_PTR ap)<br>
<br>
This is the single entry point to perform all functions of this interface. The first five parameters are standard. They are the same for all types of calls (as determined by the Type parameter; see below). After the standard parameters, there may be additional parameters specific to the particular action being performed. The interpretation of the additional parameters is a function of the remote LAN service. <br>
<br>
<b>Inputs:</b><br>
These standard parameters must appear in the order shown below.<br>
<br>
WORD Type	Type of action to perform:
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>REMOTE_LAN_SERVICE_CONNECT dials the connection (or skips dialing if already connected). <br>
<br>
REMOTE_LAN_SERVICE_DISCONNECT hangs up the connection (or skips hanging up if the connection is already terminated).<br>
<br>
REMOTE_LAN_SERVICE_CHECK_CONNECTED checks whether a connection already exists. If currently connected, returns (STATUS) 1. If not connected, returns (STATUS) 0. (The native error code and message text are ignored.)<br>
<br>
REMOTE_LAN_SERVICE_GET_EXISTING_LINKS returns (if possible) a list of existing connections to this RLAN program. The list is a single string with entries separated by tab characters. Before creating this string, the adapter program must convert the names from the native character set to Domino multibyte character set.  The list is copied into the error buffer supplied by Notes RLAN when this call is made.  Many dialers can't provide this information.  In this case (if connected to anything), return one string entry with the value, &quot;(Unknown)&quot;.</ul>
</ul>
</ul>
</ul>
</ul>
</ul>

<ul>
<ul>
<ul>
<ul>
<ul>
<ul>REMOTE_LAN_SERVICE_TERMINATE performs any needed one-time termination functions. This is called once for each process that called the INIT entry point.<br>
<br>
REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO  returns the phone number, area code and country code from the native dial entry information. This is not supported by Version 0 of the Remote LAN interface.  It is supported by Version 1 of the Remote LAN interface.<br>
<br>
REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG causes the native dialer to bring up a dialog which allows the user to create a dial information entry. This is not supported by Version 0 of the Remote LAN interface. It is supported by Version 1 of the Remote LAN interface.<br>
<br>
REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST  returns a tab-separated list of native dial entries. This is not supported by Version 0 of the Remote LAN interface. It is supported by Version 1 of the Remote LAN interface.<br>
</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<br>
DWORD *pNativeError	Place to store native error code.<br>
<br>
DWORD *pConnectionHandle	<br>
	Address of native handle of the connection (to put to or get from, depending on the type).<br>
<br>
char *pErrorBuffer	Place to store error messages for display and logging by Notes. Note that if type is REMOTE_LAN_SERVICE_TERMINATE, this address will be NULL.<br>
<br>
WORD ErrorBufferSize	Size of error buffer supplied.<br>
<br>
<b>Additional arguments</b><br>
for REMOTE_LAN_SERVICE_CONNECT:
<ul>char *pEntryName	Name of native dial information entry. <br>
char *pLoginName	Name to use to login to the remote network. 	<br>
char *pPassword	Password to use to login to the remote network.	<br>
char *pPhoneNo	Phone number to dial.	<br>
char *pDialbackNo	Phone number for the remote access server to call back to to complete the connection. 	</ul>
<br>
for REMOTE_LAN_SERVICE_DISCONNECT:
<ul>char *pEntryName	Name of native dial information entry. </ul>
<br>
for REMOTE_LAN_SERVICE_CHECK_CONNECTED<b>:</b>
<ul>char *pEntryName	Name of native dial information entry. </ul>
<br>
for REMOTE_LAN_SERVICE_GET_EXISTING_LINKS
<ul>None.</ul>
<br>
for REMOTE_LAN_SERVICE_TERMINATE 
<ul>None.</ul>
<br>
for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO 
<ul>char *pPhoneNo	For return of the  phone number in the dial entry.<br>
char *pAreaCode	For return of the  area code in the dial entry.<br>
char *pCountryCode	For return of the country code in the dial entry.<br>
WORD	Size of each of the previous three buffers.</ul>
<br>
for REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG 
<ul>None.<br>
</ul>
for REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST
<ul>char *pReturnBuffer	For return of tab-separated list of dial entry names, terminated by zero.<br>
WORD BufSize	Size of storage allocated in the return buffer<br>
WORD *BufCount	Number of characters returned, including the Null terminator.</ul>
<br>
Note that all strings passed to the adapter and returned from the adapter are stored in multibyte character (LMBCS) format. To convert these to and from a format acceptable to the operating system, the program must use the OSTranslate function.<br>
<br>
<b>Outputs:</b><br>
pConnectionHandle	Address for returning the native handle of the connection after a successful connect (used for call of type REMOTE_LAN_SERVICE_CONNECT).<br>
<br>
pErrorBuffer	Return error string in buffer at this address.<br>
<br>
(routine)	Notes error code. The following error codes have special meaning for dial-up connections:
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>NOERROR<br>
ERR_DEVICE_IN_USE<br>
ERR_CANCEL   (that is, the user has aborted)<br>
ERR_REMOTE_BUSY<br>
ERR_NO_ANSWER<br>
ERR_NO_CARRIER<br>
ERR_NO_DIALTONE<br>
<br>
For all other error conditions, use:<br>
ERR_REMOTE_LAN_ERROR</ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<br>
<br>
<b><font size="5" color="#000080">Using the Notes Callback to Display Connection Process Status</font></b><br>
<br>
For connections that can proceed asynchronously, Notes provides a callback function for use in reporting ongoing status and to detect a user abort from within Notes. This callback capability is not required, but may be useful for asynchronous connections. This function's address is provided in the call to the RLAN adapter's initialization function. Below is an outline of the function:<br>
<br>
BOOL LNCALLBACK StatusDisplayCallback(<br>
<font color="#FF0000">	</font>WORD <font color="#FF0000"> </font>Action,<br>
<font color="#FF0000">	</font>STATUS <font color="#FF0000"> </font>StatusCode,<br>
<font color="#FF0000">	</font>char <font color="#FF0000"> </font>*pErrText)<br>
<br>
The RLAN adapter calls this function when it wants Notes to display status or error information. It also checks for a user abort condition. The adapter can call this function on a thread that is different from the one on which Notes called the adapter. In this case, Notes must be told about the new thread. Therefore, before any status messages can be displayed, the adapter must call this function with the Action REMOTE_LAN_INIT_THREAD. Once the connection has been made (or has failed), it must be called with the Action REMOTE_LAN_TERM_THREAD. The initialize and terminate calls may be made any number of times for a thread, but the number of termination calls must match the number of initialization calls before the thread is terminated.<br>
<br>
<b>Inputs:</b><br>
Action	The type of operation needed. Possible values are:
<ul>
<ul>
<ul>
<ul>
<ul>
<ul>REMOTE_LAN_INIT_THREAD	<br>
Make sure this thread is known to Notes.<br>
<br>
REMOTE_LAN_TERM_THREAD	<br>
Decrement the Notes use count on this thread.<br>
<br>
REMOTE_LAN_DISPLAY_STATUS   	<br>
Map a remote LAN status code to a Notes status message and display it.<br>
<br>
REMOTE_LAN_CHECK_ABORT	<br>
Check user abort condition.<br>
<br>
REMOTE_LAN_DISPLAY_ERR0R_TEXT	<br>
Display an error message in the language provided by the remote LAN service. </ul>
</ul>
</ul>
</ul>
</ul>
</ul>
<br>
StatusCode	A Remote LAN status code, if  type is  REMOTE_LAN_DISPLAY_STATUS (see below)<br>
<br>
pErrText        	The error string, if  type is  REMOTE_LAN_DISPLAY_ERROR_TEXT.<br>
<br>
<b>Outputs:</b><br>
(routine)	The return argument is of type BOOL. This is used to return an abort condition if one has occurred. It should be TRUE (1) if operation should continue, and FALSE (0) if the user has asked for an abort (e.g. ctl+break for a PC).<br>
<br>
<b>Status codes:</b><br>
Status codes that are handled are defined in net.h. They are:<br>
<br>
REMOTE_LAN_STATUS_STARTING_CONNECTION<br>
REMOTE_LAN_STATUS_PHYSICALLY_CONNECTED<br>
REMOTE_LAN_STATUS_AUTHENTICATING<br>
REMOTE_LAN_STATUS_AUTHENTICATED<br>
REMOTE_LAN_STATUS_WAITING_FOR_CALLBACK<br>
REMOTE_LAN_STATUS_LINK_ESTABLISHED<br>
REMOTE_LAN_STATUS_LINK_FAILED<br>
REMOTE_LAN_STATUS_HANGING_UP<br>
REMOTE_LAN_STATUS_HANGUP_COMPLETE<br>
<br>
<br>
<b><font size="5" color="#000080">Sketch of a Remote LAN Adapter</font></b><br>
<br>
<tt>/* Notes interface to an external remote access capability &nbsp;*/</tt><br>
<br>
<tt>/* This module interfaces the Notes Remote LAN capability to an external remote<br>
 &nbsp; access capability. The DLL is explicitly loaded by Notes and once loaded by<br>
 &nbsp; a Notes process, the initialization function (MainEntryPoint) is called.<br>
 &nbsp; Thereafter, calls to this module are made to the standard entry point<br>
 &nbsp; (GeneralEntryPoint). &nbsp;Upon termination, the last process calls<br>
 &nbsp; the standard entry point to allow any needed termination activity, and the<br>
 &nbsp; library is unloaded by Notes. </tt><br>
<br>
<tt>&nbsp; &nbsp;This file is pseudo-code and is intended to explain how the Remote LAN<br>
 &nbsp; interface works. &nbsp;It is laid out with this purpose in mind. Some<br>
 &nbsp; declarations have been abbreviated or left out. It will not compile or<br>
 &nbsp; execute.<br>
*/</tt><br>
<br>
<br>
<tt>/* Needed C API header files */</tt><br>
<br>
<tt>#include &quot;global.h&quot; <br>
#include &quot;misc.h&quot;<br>
#include &quot;net.h&quot;<br>
#include &quot;neterr.h&quot;<br>
#include &quot;oserr.h&quot;<br>
#include &quot;osmisc.h&quot;</tt><br>
<br>
<tt>#define ThisInterfaceVersion 1 &nbsp; &nbsp;/* (This has been increased by 1 from Notes R4)</tt><br>
<br>
<tt>/*<br>
MainEntryPoint</tt><br>
<br>
<tt>&nbsp; &nbsp;This initializes the Notes interface. &nbsp;It records the status<br>
 &nbsp; callback function address, and returns the address of the standard entry<br>
 &nbsp; point to this DLL. It is called once for each process that Remote LAN is<br>
 &nbsp; used in.</tt><br>
<br>
<tt>&nbsp;Inputs:<br>
 &nbsp; *pVersion &nbsp; &nbsp; &nbsp; &nbsp; Version number currently provided by Notes.<br>
 &nbsp; Callback &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Address of a routine to call to report ongoing <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; status.</tt><br>
<br>
<tt>&nbsp;Outputs:</tt><br>
<br>
<tt>&nbsp; &nbsp;*rtnGeneralEntryPoint &nbsp; The entry point for normal calls to this DLL.<br>
 &nbsp; (routine) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Notes error code<br>
*/</tt><br>
<br>
<br>
<tt>STATUS LNCALLBACK MainEntryPoint(<br>
 &nbsp; WORD *pVersion,<br>
 &nbsp; PREMOTE_LAN_SERVICE_ENTRY *rtnGeneralEntryPoint,<br>
 &nbsp; PREMOTE_LAN_STATUS_CALLBACK Callback)<br>
{<br>
 &nbsp; STATUS error = NOERROR;</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Negotiate the version number (example) */<br>
 &nbsp; VersioninUse = MIN(*pVersion, ThisInterfaceVersion);<br>
 &nbsp; *pVersion = VersioninUse;</tt><br>
<br>
<tt>&nbsp; &nbsp;/* &nbsp; &nbsp;If you return zero for the version, Notes will make calls and expect<br>
 &nbsp; &nbsp; &nbsp; &nbsp; return values appropriate to Notes R4. */</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp;*rtnGeneralEntryPoint = (PREMOTE_LAN_SERVICE_ENTRY) GeneralEntryPoint;<br>
 &nbsp; StatusCallback = Callback;</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Load required modules as necessary. */</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Perform one-time initializations. */</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Set error = ERR_REMOTE_LAN_NOT_INSTALLED if unable to initialize. */</tt><br>
<br>
<tt>&nbsp; &nbsp;return error;<br>
}</tt><br>
<br>
<tt>/*<br>
GeneralEntryPoint</tt><br>
<br>
<tt>&nbsp; &nbsp;This is the single entry point to perform all the functions of this<br>
 &nbsp; interface. &nbsp;It is called with a standard first 5 parameters, which<br>
 &nbsp; are the same for &nbsp;all types of call (as determined by the Type parameter)<br>
 &nbsp; After the standard parameters there may be additional ones specific to the<br>
 &nbsp; particular action being performed. </tt><br>
<br>
<tt>&nbsp;Inputs (standard parameters):</tt><br>
<br>
<tt>&nbsp; &nbsp;1st arg: Type &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;The type of action to perform<br>
 &nbsp; 2nd arg: pNativeError &nbsp; &nbsp; &nbsp;Place to store Native error code<br>
 &nbsp; 3rd arg: pConnectionHandle Address of handle (to put to or get from)<br>
 &nbsp; 4th arg: pErrorBuffer &nbsp; &nbsp; &nbsp;Place to store error messages for logging.<br>
 &nbsp; 5th arg: ErrorBufferSize &nbsp; Size of argument buffer<br>
 &nbsp; Additional arguments depending on the function</tt><br>
<br>
<tt>&nbsp;Outputs:<br>
 <br>
 &nbsp; *pConnectionHandle &nbsp; The handle after a successful connect.<br>
 &nbsp; *pErrorBuffer &nbsp; &nbsp; &nbsp; &nbsp;Error string for logging</tt><br>
<br>
<tt>&nbsp; &nbsp;(routine) &nbsp; &nbsp; &nbsp; &nbsp; STATUS &nbsp;error code<br>
*/</tt><br>
<br>
<tt>STATUS LNCALLBACK GeneralEntryPoint(VARARG_PTR ap)<br>
{<br>
 &nbsp; STATUS &nbsp; error = NOERROR;<br>
 &nbsp; WORD &nbsp;Type;<br>
 &nbsp; DWORD &nbsp; &nbsp;*pNativeError;<br>
 &nbsp; DWORD &nbsp; &nbsp;*pConnectionHandle;<br>
 &nbsp; char &nbsp;*pErrorBuffer;<br>
 &nbsp; WORD &nbsp;ErrorBufferSize;<br>
 &nbsp; TCHAR &nbsp; &nbsp;CallDescription[MAX_REMOTE_LAN_PARAM_STRING];<br>
 &nbsp; char &nbsp;*pLMBCSCallDescription; /* Name of place where call information is kept */<br>
 &nbsp; <br>
 &nbsp; /* Get the common arguments */<br>
 &nbsp; <br>
 &nbsp; Type = VARARG_GET(ap, &nbsp;WORD);<br>
 &nbsp; pNativeError = VARARG_GET(ap, DWORD *);<br>
 &nbsp; pConnectionHandle = VARARG_GET(ap, DWORD *);<br>
 &nbsp; pErrorBuffer = VARARG_GET(ap, char *);<br>
 &nbsp; ErrorBufferSize = VARARG_GET(ap, WORD);<br>
 &nbsp; *pNativeError = 0;</tt><br>
<br>
<tt>&nbsp; &nbsp;switch (Type)<br>
 &nbsp; {</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_CONNECT:<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;6th Arg: The Call descriptor name, where the call info is kept.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;7th Arg: Remote Network login ID (optional)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;8th Arg: Remote Network password (optional)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;9th Arg: Phone number (optional)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 10th Arg: Dial-back number (optional) &nbsp; - new for Version 1 (R5)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Two more optional arguments are possible which can be carried<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; from the connection record designed for the specific remote<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; access method.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pLMBCSCallDescription = VARARG_GET(ap, char *); &nbsp;/* Get the call desciptor name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* &nbsp;Convert the call descriptor name from Domino multibyte<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;characters to multibyte characters expected by the OS.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSTranslate(OS_TRANSLATE_LMBCS_TO_NATIVE, pLMBCSCallDescription,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, CallDescription, sizeof (CallDescription));<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* Convert any other optional arguments as well. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Dial the connection here. &nbsp;Skip this if it already is connected.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;If there is an error, store the native error code in *pNativeError,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;the text of the error message if available in pErrorBuffer,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;and return a Notes status code.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</tt><br>
<br>
<br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_DISCONNECT:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* 6th Arg: The Call descriptor name, where the call info is kept. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pLMBCSCallDescription = VARARG_GET(ap, char *); &nbsp;/* Name of call desciptor */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Convert the call descriptor name from Domino multibyte<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;characters to multibyte characters expected by the OS.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSTranslate(OS_TRANSLATE_LMBCS_TO_NATIVE, pLMBCSCallDescription,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, CallDescription, sizeof (CallDescription));</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Hang up the connection here. &nbsp;Skip this if it no longer<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;connected. &nbsp;If there is an error, store the native error code in<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*pNativeError, the text of the error message if available in<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pErrorBuffer, and return a Notes status code.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_CHECK_CONNECTED:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* Return argument logic changed for Version 1 (R5) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* 6th Arg: The Call descriptor name, where the call info is kept. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;pLMBCSCallDescription = VARARG_GET(ap, char *); &nbsp;/* Name of call desciptor */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Convert the call descriptor name from Domino multibyte<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;characters to multibyte characters expected by the OS.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;OSTranslate(OS_TRANSLATE_LMBCS_TO_NATIVE, pLMBCSCallDescription,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, CallDescription, sizeof (CallDescription));</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Check if connection exists. &nbsp;If you can get a list of existing<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;connections, see if this connection is in the list. You will<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;have to use a comparison function that works with the multibyte<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;character set. &nbsp;Return the result as the (coerced) status code.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;If you can't obtain a list of existing connections, keep the<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;list of connections you know about locally and use it. <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;If currently connected, set *pNativeError = 1<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;If not connected, &nbsp; &nbsp;set *pNativeError = 0<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;The function should return NOERROR.</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;case REMOTE_LAN_SERVICE_GET_EXISTING_LINKS:</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* No additional args */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* If you can get a list of existing connections, return this list<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;in a single string with entries separated by tab characters.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Before creating this string, convert the names from the native<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;character set to Domino multibyte character set.<br>
 &nbsp; &nbsp; &nbsp; &nbsp; */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;BOOL &nbsp;bOnline = FALSE;</tt>
<ul><tt>	 &nbsp; char &nbsp;*p;</tt><br>
<br>
<tt>	 &nbsp; *pErrorBuffer = '\0';</tt><br>
<tt>	</tt><br>
<tt>&nbsp; &nbsp; &nbsp; /* Here find out from the dialer if any connection exists and set</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt><tt>bOnline = TRUE if so */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; if (bOnline)</tt><br>
<tt>&nbsp; &nbsp; &nbsp; {</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;p = &quot;(Unknown)&quot;;</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</tt><tt>/* substitute favorite string copy routine here. */</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;Cstrncpy(pErrorBuffer, p, ErrorBufferSize	- 1); &nbsp;</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp;}</tt><br>
<tt><br>
 &nbsp; &nbsp; &nbsp; break;</tt></ul>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;case REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_LIST:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* New in Version 1 (R5) */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; pReturnBuffer = VARARG_GET(ap, char *);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; MaxBufferSize = VARARG_GET(ap, WORD);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; pReturnCount = VARARG_GET(ap, WORD *);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* If available, return a list of phonebook entry names, tab<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;delimited, null terminated. Else return an empty buffer. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_CREATE_DIAL_ENTRY_DIALOG:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* New in Version 1 (R5) */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Bring up the native remote access interface for creating <br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;dialup connection information. There is no return information<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;needed, except an error code if it fails. */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_GET_DIAL_ENTRY_INFO:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* New in Version 1 (R5) */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;char *retLMBCSPhone, *retLMBCSAreaCode, *retLMBCSCountry;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Get Address book entry name */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; pLMBCSPhonebookEntry = VARARG_GET(ap, char *);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; OSTranslate(OS_TRANSLATE_LMBCS_TO_NATIVE, pLMBCSPhonebookEntry,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, PhonebookEntry, sizeof (PhonebookEntry));</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;retLMBCSPhone = VARARG_GET(ap, char *);</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;retLMBCSAreaCode = VARARG_GET(ap, char *);</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;retLMBCSCountry = VARARG_GET(ap, char *);</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MaxBufferSize = VARARG_GET(ap, WORD);</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Call the native remote access capability to get the phone number<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;information stored in it. Return these values. &nbsp;*/</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp; &nbsp; case REMOTE_LAN_SERVICE_TERMINATE:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* Perform any need one-time termination functions. */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; default:</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;break;<br>
 &nbsp; }</tt><br>
<br>
<tt>&nbsp; &nbsp;return error;<br>
}</tt><br>
<br>
<br>
<tt>/*<br>
GetExistingConnections</tt><br>
<br>
<tt>&nbsp; &nbsp;This returns a list of Remote LAN connections that are currently<br>
 &nbsp; connected. &nbsp;</tt><br>
<br>
<tt>&nbsp;Inputs:</tt><br>
<br>
<tt>&nbsp; &nbsp;pBuf &nbsp; &nbsp; Buffer to put conection list in. The list is tab separated and<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;zero terminated.<br>
 &nbsp; Bufsize &nbsp;Size of return buffer allocated.</tt><br>
<br>
<tt>&nbsp;Outputs:</tt><br>
<br>
<tt>&nbsp; &nbsp;None<br>
*/</tt><br>
<br>
<tt>void GetExistingConnections(char *pBuf, WORD BufSize)<br>
{<br>
 &nbsp; unsigned i;<br>
 &nbsp; char &nbsp;*NativeConnections[MAXCONNECTIONS];<br>
 &nbsp; DWORD &nbsp; &nbsp;nConn;<br>
 &nbsp; char &nbsp;*p;<br>
 &nbsp; <br>
 &nbsp; BufSize--; &nbsp; &nbsp; /* leave room for a final terminator */<br>
 &nbsp; <br>
 &nbsp; GetArrayOfNativeConnections(NativeConnections, ...);<br>
 &nbsp; &nbsp;<br>
 &nbsp; for (i = 0, p = pBuf; i &lt; nConn &amp;&amp; (pBuf + BufSize - p) &gt; 1; i++)<br>
 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;/* Delimit entries with a tab char &nbsp;*/<br>
 &nbsp; &nbsp; &nbsp;if (i != 0)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; *p++ = '\t'; &nbsp;/* add a tab, overwriting the previous '\0' */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;/* Translate to LMBCS - it returns the number of bytes not incl. '\0'*/<br>
 &nbsp; &nbsp; &nbsp;p += OSTranslate(OS_TRANSLATE_NATIVE_TO_LMBCS, NativeConnections[i],<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;MAXWORD, p, (WORD)(pBuf + BufSize - p));<br>
 &nbsp; }<br>
 &nbsp; *p = '\0'; &nbsp; /* terminate the string */<br>
}</tt><br>
<br>
<br>
<tt>/*<br>
AsyncConnect</tt><br>
<br>
<tt>&nbsp; &nbsp;This calls the remote LAN to set up a connection, and waits for the<br>
 &nbsp; connection to be completed. &nbsp;</tt><br>
<br>
<tt>*/</tt><br>
<br>
<tt>static DWORD AsyncConnect(arguments...)<br>
{</tt><br>
<br>
<tt>&nbsp; &nbsp;Err = DialAsync (DialCallback, &amp;hCallHandle, ...);<br>
 &nbsp; if (Err)<br>
 &nbsp; &nbsp; &nbsp;return Err;</tt><br>
<br>
<tt>&nbsp; &nbsp;/* Wait until the connection is completed */<br>
 &nbsp; <br>
 &nbsp; for ( ; ; )<br>
 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;Sleep (500); &nbsp; /* 500 msec */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; Err = GetConnectStatus(hCallHandle, &amp;Status);<br>
 &nbsp; &nbsp; &nbsp;if (Err)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /* Break if connection succeded */<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;if (Status == Connected)<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /* Check for user abort */<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;if ((*StatusCallback)(REMOTE_LAN_CHECK_ABORT, NULL, NULL) != NOERROR)<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* Hang up connection */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; }</tt><br>
<br>
<tt>}</tt><br>
<br>
<br>
<tt>/*<br>
DialCallback</tt><br>
<br>
<tt>&nbsp; &nbsp;This is a callback function, called by the remote access service to show<br>
 &nbsp; ongoing status of a connection. &nbsp;</tt><br>
<br>
<tt>*/</tt><br>
<br>
<br>
<tt>DialCallback (ConnState, Error, ...)<br>
{<br>
 &nbsp; STATUS &nbsp; status = NOERROR;<br>
 &nbsp; char &nbsp;ErrorString [MAXSPRINTF];</tt><br>
<br>
<br>
<tt>&nbsp; &nbsp;/* Map remote access status codes to Notes Remote LAN status codes. */<br>
 &nbsp; <br>
 &nbsp; switch(ConnState)<br>
 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;case Starting:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_STARTING_CONNECTION;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case Connected:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_PHYSICALLY_CONNECTED;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case Authenticating:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_AUTHENTICATING;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case Authenticated:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_AUTHENTICATED;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case WaitingForCallback:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_WAITING_FOR_CALLGBACK;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case Connected:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_LINK_ESTABLISHED;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;case Disconnected:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; status = REMOTE_LAN_STATUS_LINK_FAILED;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; }</tt><br>
<br>
<br>
<br>
<tt>&nbsp; &nbsp;if (!Error)<br>
 &nbsp; {</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; /* Display status message in Notes */</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; if (status)<br>
 &nbsp; &nbsp; &nbsp;{<br>
 &nbsp; &nbsp; &nbsp; &nbsp; /* If a new thread has just been created by the remote access program<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;for this status message, We must make the thread known to Notes */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;(*StatusCallback) (REMOTE_LAN_INIT_THREAD, NULL, NULL);</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* Send status to callback in notes */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; (*StatusCallback) (REMOTE_LAN_DISPLAY_STATUS, status, NULL);</tt><br>
<br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;/* In case this is the last time the status callback will be called,<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;we must tell Notes the thread is going away */<br>
 &nbsp; &nbsp; &nbsp; &nbsp; (*StatusCallback) (REMOTE_LAN_TERM_THREAD, NULL, NULL);<br>
 &nbsp; &nbsp; &nbsp;}<br>
 &nbsp; }<br>
 &nbsp; &nbsp; &nbsp;</tt><br>
<br>
<tt>&nbsp; &nbsp;else<br>
 &nbsp; {<br>
 &nbsp; <br>
 &nbsp; &nbsp; &nbsp;/* Display error message in Notes */<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;/* Tell Notes about the thread. */<br>
 &nbsp; &nbsp; &nbsp;(*StatusCallback) (REMOTE_LAN_INIT_THREAD, NULL, NULL);<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;/* &nbsp;Convert Error code to string and have Notes display it. */<br>
 &nbsp; &nbsp; &nbsp;GetErrorString(Error, ErrorString);<br>
 &nbsp; &nbsp; &nbsp;(*StatusCallback) (REMOTE_LAN_DISPLAY_ERR0R_TEXT, NULL, ErrorString);<br>
 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;/* Now tell Notes to forget it. */<br>
 &nbsp; &nbsp; &nbsp;(*StatusCallback) (REMOTE_LAN_TERM_THREAD, NULL, NULL);<br>
 &nbsp; } &nbsp;</tt><br>
<br>
<tt>}</tt><br>
<br>
<tt>/*<br>
MapError</tt><br>
<br>
<tt>&nbsp; &nbsp;This maps a native remote access error code to a Notes error code. </tt><br>
<br>
<tt>&nbsp;Inputs:</tt><br>
<br>
<tt>&nbsp; &nbsp;Error &nbsp; &nbsp; &nbsp; The remote access error code</tt><br>
<br>
<br>
<tt>&nbsp;Outputs:</tt><br>
<br>
<tt>&nbsp; &nbsp;(routine) &nbsp; &nbsp; &nbsp;The Notes error code<br>
*/</tt><br>
<br>
<br>
<tt>STATUS MapError (DWORD Error)<br>
{<br>
 &nbsp; STATUS error; &nbsp;/* Notes error code */</tt><br>
<br>
<tt>&nbsp; &nbsp;switch(Error)<br>
 &nbsp; {<br>
 &nbsp; &nbsp; &nbsp;case 0:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = NOERROR;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;case ERROR_PORT_ALREADY_OPEN:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_DEVICE_IN_USE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp;<br>
 &nbsp; &nbsp; &nbsp;case ERROR_USER_DISCONNECTION:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_CANCEL;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;case ERROR_LINE_BUSY:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_REMOTE_BUSY;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;case ERROR_NO_ANSWER:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_NO_ANSWER;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;case ERROR_NO_CARRIER:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_NO_CARRIER;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;case ERROR_NO_DIALTONE:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_NO_DIALTONE;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; <br>
 &nbsp; &nbsp; &nbsp;default:<br>
 &nbsp; &nbsp; &nbsp; &nbsp; error = ERR_REMOTE_LAN_ERROR;<br>
 &nbsp; &nbsp; &nbsp; &nbsp; break;<br>
 &nbsp; }<br>
 &nbsp; return error;<br>
}</tt>
---
