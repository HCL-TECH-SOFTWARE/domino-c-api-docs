




<!--
 /\* Font Definitions \*/
 @font-face
 {font-family:Helv;
 panose-1:2 11 6 4 2 2 2 3 2 4;}
@font-face
 {font-family:"Cambria Math";
 panose-1:2 4 5 3 5 4 6 3 2 4;}
 /\* Style Definitions \*/
 p.MsoNormal, li.MsoNormal, div.MsoNormal
 {margin-top:0cm;
 margin-right:0cm;
 margin-bottom:8.0pt;
 margin-left:0cm;
 line-height:107%;
 font-size:11.0pt;
 font-family:"Calibri",sans-serif;}
.MsoChpDefault
 {font-size:11.0pt;}
.MsoPapDefault
 {margin-bottom:8.0pt;
 line-height:107%;}
 /\* Page Definitions \*/
 @page WordSection1
 {size:612.0pt 792.0pt;
 margin:72.0pt 72.0pt 72.0pt 72.0pt;}
div.WordSection1
 {page:WordSection1;}
-->




**Initial Release 4.5**



**Symbolic Value : Remote LAN adapter**



**REMOTE\_LAN\_SERVICE\_xxx** **-** Type of
action to be performed by a remote LAN adapter.


**----------------------------------------------------------------------------------------------------------**



**#include <net.h>**


 **Symbolic Values :**      REMOTE\_LAN\_SERVICE\_CONNECT           -  Dial the connection,
or skip dialing if already connected.  

  

      REMOTE\_LAN\_SERVICE\_DISCONNECT     -  Hang up the connection, or skip
hanging up if the connection is already terminated.  

  

      REMOTE\_LAN\_SERVICE\_TERMINATE        -  Perform any needed one-time
termination functions. This is called once for each process that called the
remote LAN adapter's initialization function. You do not need to perform any
action if no action is needed by the dialing software.  

  

      REMOTE\_LAN\_SERVICE\_CHECK\_CONNECTED     -  Check whether a connection
already exists. If currently connected, return the value 1 in the location
pointed to by the second call argument , return a value of 0 if the connection
does not exist. Always return NOERROR as the function value. Note that this is
a change from Version 0 of the Remote LAN interface, where the connection value
was returned as the function value.  

  

      REMOTE\_LAN\_SERVICE\_GET\_EXISTING\_LINKS   -  Return (if possible) a list of
existing connections to this remote LAN adapter program. This list is a single
string with entries separated by tab characters. Before creating this string,
the adapter program must convert the names from the native character set to
Lotus multibyte character set (LMBCS).  

  

      REMOTE\_LAN\_SERVICE\_GET\_DIAL\_ENTRY\_INFO            -  Return the phone
number, area code and country code from the native dial entry information. This
is not supported by Version 0 of the Remote LAN interface. It is supported by
Version 1 of the Remote LAN interface.  

  

      REMOTE\_LAN\_SERVICE\_CREATE\_DIAL\_ENTRY   -  Not used  

  

      REMOTE\_LAN\_SERVICE\_CREATE\_DIAL\_ENTRY\_DIALOG             -  Causes the
native dialer to bring up a dialog which allows the user to create a dial
information entry. This is not supported by Version 0 of the Remote LAN
interface. It is supported by Version 1 of the Remote LAN interface.  

  

      REMOTE\_LAN\_SERVICE\_GET\_DIAL\_ENTRY\_LIST             -  Return a tab-separated
list of native dial entries. This is not supported by Version 0 of the Remote
LAN interface. It is supported by Version 1 of the Remote LAN interface.  

  




**Description :**



These values
specify what action is to be performed by a remote LAN adapter.  Domino and
Notes calls the remote LAN adapter's general entry point function with the Type
parameter set to one of these values.  See the chapter in the *Lotus C API
User Guide*, Remote LAN Access Product Adapter, for details.


 **See Also :**


**[PREMOTE\_LAN\_SERVICE\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/CE85C1F5D2E0248085256361003C3CC9)**



----------------------------------------------------------------------------------------------------------


 





