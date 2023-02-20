##### Chapter 12-6
##### Network Send and Receive

The C API provides network send and receive routines that give API programs the ability to connect over a COM port to a remote system and exchange data in character mode with that system. They allow an application to connect to a foreign system and use its own protocol to communicate with that system.<br>
<br>
These routines provide two advantages over using the operating system COM driver directly:<br>

<ul type="disc">
<li>They allow the application to share the same COM devices being used by Domino or Notes.
<li>They allow the application to take advantage of the modem support built into Domino and Notes.</ul>
<br>
<br>
An application should use these routines in the following sequence:<br>

<ol type="1">
<li>Call NetLink to dial out to the remote system and establish a session to use to communicate with that system.
<li>Call NetSetSessionMode to set the operating parameters for the session.
<li>Call NetSend and NetReceive to communicate over the session in a manner required by the protocol being implemented by the application.
<li>Call NetCloseSession to hang up the phone, release the COM device,  and close the session. This is an important step and should never be omitted once a call to NetLink returns successfully, even if any subsequent calls to any of the other routines fail.</ol>

---
