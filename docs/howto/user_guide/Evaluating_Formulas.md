##### Chapter 8-6
##### Evaluating Formulas

This chapter examines the sample program FORMULA, which demonstrates how to run a formula against a note in a database. FORMULA creates a document containing a number field and then runs a formula against the new document. The formula simply returns the value of the number field. FORMULA is in the subdirectory \samples\dbdesign\formula.<br>
<br>
<br>
<b><font size="5" color="#000080">Formula Evaluation Function Calls</font></b><br>
<br>
Several C API functions are specific to formula evaluation.<br>
<br>
<br>
<b><font size="4" color="#000080">NSFComputeStart</font></b><br>
<br>
NSFComputeStart takes a pointer to a compiled formula as input and returns a handle that NSFComputeEvaluate<font color="#FF0000"> </font>uses to uniquely identify that formula. You must call this function for each formula that you want to evaluate.<br>
<br>
<br>
<b><font size="4" color="#000080">NSFComputeEvaluate</font></b><br>
<br>
NSFComputeEvaluate takes as input the handle returned by NSFComputeStart, a note handle, a data handle to be used to return a buffer of results, a length parameter for this buffer, and several BOOLEAN output parameters. Only the first parameter is required. Set the others to 0 if you don't want to use them. For details about this function, see the <i>Reference.</i><br>
<br>
<br>
<b><font size="4" color="#000080">NSFComputeStop</font></b><br>
<br>
NSFComputeStop terminates processing, freeing the handle allocated by NSFComputeStart. <br>
<br>
<br>
<b><font size="5" color="#000080">The FORMULA Sample Program</font></b><br>
<br>
The sample program FORMULA demonstrates how to evaluate a simple formula. It first creates a document containing a number field -- the note on which the formula will be evaluated. The program then calls NSFFormulaCompile to compile the formula (which simply returns the value in the note's numeric field) and NSFComputeStart. The program<font color="#FF0000"> </font>then calls NSFComputeEvaluate, passing it a handle to the new note and requesting that the following information be returned:<br>

<ul type="disc">
<li>A buffer containing the results of the formula evaluation
<li>A WORD containing the length of the buffer
<li>A BOOLEAN specifying whether the formula modified the note
<li>A BOOLEAN specifying whether the formula determined that the note should be deleted </ul>
<br>
While the formula in this sample does not modify or delete the note, the booleans are included for demonstration purposes.<br>
<br>
The buffer returned by the function call starts with a datatype word, followed by the data itself.<br>
<br>
NOTE: The data is usually returned in LIST format (for example, a number will come back as TYPE_NUMBER_RANGE). A C API program should be able to handle data in both simple and LIST forms.<br>
<br>
Also note that many formulas return a BOOLEAN value. Since BOOLEAN is really a number, these values are also returned as either a number or a number range.<br>
<br>
The program FORMULA locks the data handle returned by NSFComputeEvaluate, gets the datatype of the returned data, and prints the data appropriately. The program then calls NSFComputeStop to terminate formula evaluation, closes the database, and exits.
---
