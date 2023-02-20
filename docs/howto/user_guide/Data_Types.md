##### Chapter 14-2
##### Data Types

This chapter describes some of the data types used in the HCL C API for Domino and Notes.<br>
<br>
<br>
<b><font size="5" color="#000080">BLOCKID</font></b><br>
<br>
A BLOCKID is a structure that Domino and Notes uses to manage memory. Some API functions (for example, NSFItemInfo) return data in memory blocks. Other API functions (for example,  NSFItemAppendByBLOCKID) take input data in memory blocks. These functions are designed to manipulate a collection of many different records which, for efficiency reasons, are all stored in the same memory object identified by a single memory handle.<br>
<br>
A memory object consists of a &quot;pool&quot; subdivided into &quot;blocks.&quot; The pool member of a BLOCKID stores the handle to an allocated area of memory.  You must use OSMemAlloc and OSMemFree to manage this pool; this handle is <u>not</u> an operating system memory handle. The block member of a BLOCKID stores an offset to some position in the pool.<br>
<br>
As a typical example in Domino or Notes, the items stored in a note are kept in a single large memory object if the contents of the note are smaller than the Domino or Notes memory allocation limit, MAXONESEGSIZE.  If you use NSFItemInfo to examine the items in the note, the pool member is the same for all the items while the block member differs.<br>
<br>
<br>
<b><font size="5" color="#000080">DARRAY</font></b><br>
<br>
Domino and Notes uses an implementation of dynamic arrays to store lists of information. Elements can be added to or removed from a DARRAY.<br>
<br>
In the Domino and Notes implementations, elements in a dynamic array have a set of fields followed by some number of packed strings. You must use the data structure PSTRING (defined in darray.h) in the dynamic array element to describe the packed strings; the PSTRING elements must be the last members of the dynamic array element.<br>
<br>
A Domino or Notes dynamic array contains three components:<br>

<ul type="disc">
<li>A header structure, DARRAY
<li>The array of element records
<li>Storage for packed strings</ul>
<br>
<br>
<b><font size="5" color="#000080">TIMEDATE</font></b><br>
<br>
 The Domino and Notes TIMEDATE structure consists of two long words that encode the time, the date, the time zone, and the Daylight Savings Time settings that were in effect when the structure was initialized.  The TIMEDATE structure is designed to be accessed exclusively through the time and date subroutines defined in misc.h.  This structure is subject to change;  the description here is provided for debugging purposes.<br>
<br>
The first DWORD, Innards[0], contains the number of hundredths of seconds since midnight, Greenwich mean time.  If only the date is important, not the time, this field may be set to ALLDAY.<br>
<br>
The date and the time zone and Daylight Savings Time settings are encoded in Innards[1].  The 24 low-order bits contain the Julian Day, the number of days since January 1, 4713 BC.  Note that this is NOT the same as the Julian calendar!  The Julian Day was originally devised as an aid to astronomers.  Since only days are counted, weeks, months, and years are ignored in calculations.  The Julian Day is defined to begin at noon;  for simplicity, Domino and Notes assume that the day begins at midnight.  The high-order byte, bits 31-24, encodes the time zone and Daylight Savings Time information.  The high-order bit, bit 31 (0x80000000), is set if Daylight Savings Time is observed.  Bit 30 (0x40000000) is set if the time zone is east of Greenwich mean time.  Bits 27-24 contain the number of hours difference between the time zone and Greenwich mean time, and bits 29-28 contain the number of 15-minute intervals in the difference.<br>
<br>
For example, 2:49:04 P. M., Eastern Standard Time, December 10, 1996 would be stored as:<br>

<ul>Innards[0]:	0x006CDCC0	19 hours, 49 minutes, 4 seconds GMT<br>
Innards[1]:	0x852563FC	DST observed, zone +5, Julian Day  2,450,428</ul>
<br>
If the time zone were set for Bombay, India, where Daylight Savings Time is not observed, 2:49:04 P. M., December 10, 1996 would be stored as:<br>

<ul>Innards[0]:	0x0032B864	9 hours, 19 minutes, 4 seconds GMT<br>
Innards[1]:	0x652563FC	No DST, zone 5 1/2 hours east of GMT, Julian Day  2,450,428</ul>

---
