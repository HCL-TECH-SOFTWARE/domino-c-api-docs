




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



**Symbolic Value : Calendaring and
Scheduling**



**SCHED\_ATTR\_xxx** **-** SCHED\_ENTRY
- Attr


**----------------------------------------------------------------------------------------------------------**



**#include <nsfdata.h>**


 **Symbolic Values :**      SCHED\_ATTR\_FOREIGN\_UNID       -  Used by gateways to return
foreign UNIDs  

  

      SCHED\_ATTR\_REPEAT\_EVENT     -  In Release 5, identifies a repeating
meeting.  

  

      SCHED\_ATTR\_RESERVED4            -  Bit 6 is reserved for future use.  

  

      SCHED\_ATTR\_RESERVED8            -  Bit 7 is reserved for future use.  

  

      SCHED\_ATTR\_TYPE\_BITS   -  Entry type mask.  

  

      SCHED\_ATTR\_FREE\_BASE            -  Entry types that don't block off busy
time.  

  

      SCHED\_ATTR\_BUSY\_BASE            -  Entry types that block off busy time.  

  

      SCHED\_ATTR\_NULL           -  (SCHED\_ATTR\_FREE\_BASE + 0x00)  

  

      SCHED\_ATTR\_PENCILED   -  (SCHED\_ATTR\_FREE\_BASE + 0x01)  

  

      SCHED\_ATTR\_FREE\_RESERVED2             -  (SCHED\_ATTR\_FREE\_BASE + 0x02)  

  

      SCHED\_ATTR\_FREE\_RESERVED3             -  (SCHED\_ATTR\_FREE\_BASE + 0x03)  

  

      SCHED\_ATTR\_FREE\_RESERVED4             -  (SCHED\_ATTR\_FREE\_BASE + 0x04)  

  

      SCHED\_ATTR\_FREE\_RESERVED5             -  (SCHED\_ATTR\_FREE\_BASE + 0x05)  

  

      SCHED\_ATTR\_FREE\_RESERVED6             -  (SCHED\_ATTR\_FREE\_BASE + 0x06)  

  

      SCHED\_ATTR\_FREE\_RESERVED7             -  (SCHED\_ATTR\_FREE\_BASE + 0x07)  

  

      SCHED\_ATTR\_APPT           -  (SCHED\_ATTR\_BUSY\_BASE + 0x00)  

  

      SCHED\_ATTR\_NONWORK   -  (SCHED\_ATTR\_BUSY\_BASE + 0x01)  

  

      SCHED\_ATTR\_BUSY\_RESERVED2             -  (SCHED\_ATTR\_BUSY\_BASE + 0x02)  

  

      SCHED\_ATTR\_BUSY\_RESERVED3             -  (SCHED\_ATTR\_BUSY\_BASE + 0x03)  

  

      SCHED\_ATTR\_BUSY\_RESERVED4             -  (SCHED\_ATTR\_BUSY\_BASE + 0x04)  

  

      SCHED\_ATTR\_BUSY\_RESERVED5             -  (SCHED\_ATTR\_BUSY\_BASE + 0x05)  

  

      SCHED\_ATTR\_BUSY\_RESERVED6             -  (SCHED\_ATTR\_BUSY\_BASE + 0x06)  

  

      SCHED\_ATTR\_BUSY\_RESERVED7             -  (SCHED\_ATTR\_BUSY\_BASE + 0x07)  

  




**Description :**



Possible
values for the Attr member of the SCHED\_ENTRY structure.  Note that if bit 3
(bits are numbered from 0 to 7) is set, the entry will take up busy time.  The
lower nibble of the attributes defines the the entry type.


 


NOTE:  The
upper two bits of the Attr field is reserved for future use (bit 6 - 7).


 **See Also :**


**[SCHED\_ENTRY](notes:///8525872100478C66/61FD4E9848264AD28525620B006BA8BD/5EDBDAD427D0F3328525636100504E3B)**



----------------------------------------------------------------------------------------------------------


 





