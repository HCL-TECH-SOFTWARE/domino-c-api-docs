##### Data Type : Rich Text
##### ACTIVEOBJECTPARAM - Active object parameter specification.
---
```
#include <editods.h>
```

**Definition :**
```
typedef struct {
   WORD Length;        /* Length of the text string that follows */
   WORD FormulaLength; /* Length of the formula data (if any) that
                          follows */
   WORD Reserved;
/* Variable length data follows (strings not null terminated) */
} ACTIVEOBJECTPARAM;
```

**Description :**

This record specifies how a parameter to an active object is obtained.  This record only appears following an ACTIVEOBJECT record, and is part of a CDHOTSPOTBEGIN record.  The ACTIVEOBJECTPARAM may contain either a string representing the entire parameter, or a string representing the parameter name and a formula representing the parameter value.
<ul><br>
<br>
In the first case, the variable length data is a string of the form &quot;ParameterName=ParameterValue&quot;.  In this case, &quot;Length&quot; should be the number of bytes in this string, and &quot;FormulaLength&quot; should be zero.<br>
<br>
In the second case, the variable length data consists of a string representing the parameter name followed by a formula representing the parameter value.  In this case, &quot;Length&quot; should be the number of bytes in the parameter name string, and &quot;FormulaLength&quot; should be the length of the formula.<br>
<br>
The fields in this record are:<br>

<ul>Length		Length of string parameter or length of parameter name.<br>
FormulaLength	Length of the formula, if any.  If no formula is provided, 0.<br>
Reserved	Reserved;  must be 0.</ul>
<br>
This record is followed first by the string, in LMBCS format with no NULL delimiter, then by the formula, if present.</ul>



**See Also :**
[ACTIVEOBJECT](/domino-c-api-docs/reference/Data/ACTIVEOBJECT)
[CDHOTSPOTBEGIN](/domino-c-api-docs/reference/Data/CDHOTSPOTBEGIN)
---
