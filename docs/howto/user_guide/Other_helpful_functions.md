##### Chapter 11-6
##### Other helpful functions

<b><font size="5" color="#000080">Other helpful functions</font></b><br>
<br>
Many applications built using the Notes/Domino C API Toolkit already contain advanced operations using Notes objects like NOTEID, UNID, TIMEDATE, etc.  The Calendar and Scheduling methods might be difficult to work with within the constraints of these existing applications.  As such, a few convenience methods have been implemented to ease this process.
<p>CalGetRecurrenceID will return char* data representing a valid RECURRENCE-ID based on an existing TIMEDATE object.  This returned value can then be used as an argument to specify an instance for one of the other methods.
<p>CalOpenNoteHandle can be used to get a handle to a note that represents a calendar entry with a given UID.  CalOpenNoteHandle can also take RECURRENCE-ID input to return a note that represents only a single instance of a recurring meeting, hiding the complexities of the complex parent/child relationship that exists between notes representing that recurring meeting in the database. 
---
