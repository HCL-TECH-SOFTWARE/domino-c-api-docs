##### Chapter 6-2
##### Tips on Using Views

<b><font size="5" color="#000080">Views and HCL C API Programs for Domino and Notes</font></b><br>
<br>
If you are writing a C API program that can benefit from a particular view of a database, you can define the view to support your C API processing. In fact, this is an excellent reason for creating a view.<br>
<br>
You might want your program to read a special subset of the documents in a database. To do this, you can create a view with a selection formula.<font color="#FF0000"> </font>If you want your program to read a database's documents in a certain order, create a view with the sorting order you want. If you want to read only the main topics in a database, but ignore the response notes, define a view with no response hierarchy.<br>
<br>
<br>
<b><font size="4" color="#000080">NSFSearch versus NIFReadEntries</font></b><br>
<br>
Using a view to select documents for processing by a C API program is very similar to what NSFSearch does. When should you use NSFSearch to find documents in a database, and when should you use a view? Here are some general guidelines.<br>
<br>
Use NSFSearch to select documents from a database when:<br>

<ul type="disc">
<li>The selection criteria are unknown until run time. In this case, the program must compose the selection formula at run time, compile the formula with NSFFormulaCompile, and pass the formula to NSFSearch. The program cannot use a view, since you must create all views manually before running the program.
<li>The performance of the program is not important, or you will run the program only a few times.
<ul></ul>
</ul>
Use a view to select documents from a database when:<br>

<ul type="disc">
<li>You want to process the documents in a certain order. You can build this sorting order into the view definition.
<li>Performance is important. Often, document selection using a view is faster than the equivalent selection using a compiled formula and NSFSearch.</ul>

---
