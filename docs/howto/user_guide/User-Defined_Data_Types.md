##### Chapter 12-5
##### User-Defined Data Types

<b><font size="5" color="#000080">Introduction</font></b><br>
<br>
This chapter explains how to create fields<b><font color="#FF0000"> </font></b>with custom data types and fill them with data that has a structure of your own definition. Examples of such data include:<br>

<ul type="disc">
<li>Graphics formats that Domino and Notes do not understand
<li>Time stamps with a non-Domino time structure
<li>Encrypted data that uses your own encryption scheme
<li>Arbitrary data structures (created by any application) that you wish to store in a Domino database</ul>
<br>
Domino and Notes allow user-defined fields by assigning them to a new Domino data type called TYPE_USERDATA, explained in the next section. For more information, also see the sample program MISC\USER_DEF.<br>
<br>
<br>
<b><font size="5" color="#000080">Structure of a User-Defined Data Type</font></b><br>
<br>
The structure of a user-defined field is:<br>

<ul>
<ul>BYTE  descrip_len;     /* length of the type description string */<br>
char  type_descrip[descrip_len];    /* type description string */<br>
BYTE  data[data_len];    /* the user-defined data */</ul>
</ul>
<br>
The first byte contains the length of the type description string that follows. Since the number occupies one byte, the length may be from 0 to 255.<br>
<br>
Domino and Notes make no attempt to interpret the type description string, but you should use this string to distinguish various data types that you create. You should make the description long enough that it will not accidentally be confused with someone else's data type. For example, &quot;Acme Corp. Special Password&quot; is a good type description string. &quot;My Data&quot; is not a good description, since someone else might use the same string.<br>
<br>
You can store any data at all in the data portion of a user-defined field. Domino and Notes make no attempt to interpret the data or its structure.<br>
<br>
The overall length of a single field must be less than 64 kilobytes. If you need to set the ITEM_SUMMARY flag, the field must be less than 15 kilobytes. You can have multiple fields with the same name and type description string. You can also have multiple TYPE_USERDATA fields with different field names and description strings.<br>
<br>
<br>
<b><font size="5" color="#000080">Additional Notes</font></b><br>
<br>
You can retrieve documents containing TYPE_USERDATA fields just as you can any other documents. You can use either a sequential search (NSFSearch) or an indexed search (NIFOpenCollection and NIFReadEntries).<br>
<br>
When you are creating a field of any type (including TYPE_USERDATA) you must decide whether to set the field's flag to ITEM_SUMMARY. Only fields with ITEM_SUMMARY set can be used in a view selection formula or an NSFSearch formula. If you need to set the ITEM_SUMMARY flag, you must keep the length of the field small (less than 15<b><font color="#FF0000"> </font></b>kilobytes) because Domino and Notes impose a maximum of 15 kilobytes of summary data per note. If you do not plan to use these operations on the field, you may omit this flag.<br>
<br>
At the Notes user interface, the only way you can see TYPE_USERDATA fields is to select File - Document Properties and then select the Fields tab. You cannot see them from a form or in a view. Since Domino and Notes can not interpret the data in a field of type TYPE_USERDATA, you cannot generally refer to fields of this type in formulas in form fields, view columns, or macros. However, if the ITEM_SUMMARY flag is set, the function @IsAvailable returns TRUE.
---
