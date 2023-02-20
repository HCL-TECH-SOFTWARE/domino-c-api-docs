##### Data Type : Rich Text
##### ACTIVEOBJECTPARAM - Active object parameter specification.
---
```
#include <editods.h>
```
**Description :**

This record specifies how a parameter to an active object is obtained.  This 
record only appears following an ACTIVEOBJECT record, and is part of a 
CDHOTSPOTBEGIN record.  The ACTIVEOBJECTPARAM may contain either a string 
representing the entire parameter, or a string representing the parameter name 
and a formula representing the parameter value.

In the first case, the variable length data is a string of the form 
"ParameterName=ParameterValue".  In this case, "Length" should be the number of 
bytes in this string, and "FormulaLength" should be zero.

In the second case, the variable length data consists of a string representing 
the parameter name followed by a formula representing the parameter value.  In 
this case, "Length" should be the number of bytes in the parameter name string, 
and "FormulaLength" should be the length of the formula.

The fields in this record are:

Length  Length of string parameter or length of parameter name.
FormulaLength Length of the formula, if any.  If no formula is provided, 0.
Reserved Reserved;  must be 0.

This record is followed first by the string, in LMBCS format with no NULL 
delimiter, then by the formula, if present.

**See Also :**
[ACTIVEOBJECT](/reference/Data/ACTIVEOBJECT)
[CDHOTSPOTBEGIN](/reference/Data/CDHOTSPOTBEGIN)
---
