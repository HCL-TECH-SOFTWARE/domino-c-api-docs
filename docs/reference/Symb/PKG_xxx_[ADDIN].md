##### Symbolic Value : Resource Definition
##### PKG_xxx [ADDIN] - Base value for an AddIn's error definitions.
---
```
#include <globerr.h>
```

**Symbolic Values :**



**Description :**

When developing C API programs to run under Windows, define a string table by creating a resource (.RC) file and use PKG_ADDIN as the base value for the resource IDs in the string table.<br>
<br>
By convention, the first resource ID in a C API program's string table should be PKG_ADDIN, and the corresponding string should be the name of the API program.  The second ID should be PKG_ADDIN+1, and the corresponding string should describe the API program's version number.  Subsequent IDs should be numbered sequentially after that (PKG_ADDIN+2, PKG_ADDIN+3, etc...).<br>
<br>
Lotus Domino Server AddIn programs under Windows should follow this convention.  By default, Domino  uses the string at offset PKG_ADDIN in the string table associated with a server AddIn program as the task name in the status line in the &quot;show tasks&quot; display.  Server AddIn programs under other operating systems should use AddInCreateStatusLine.


**Sample Usage :**
```
(in HISTERR.H)
#define HISTORY_NAME                       (PKG_ADDIN+0)
#define HISTORY_VERSION                    (PKG_ADDIN+1)
#define DEFAULT_HISTORY_DBFILENAME         (PKG_ADDIN+2)
#define DEFAULT_HISTORY_DBSERVER           (PKG_ADDIN+3)

(in HISTORY.RC)
#include <windows.h>
#include <globerr.h>
#include "history.h"
#include "histerr.h"

STRINGTABLE
BEGIN
HISTORY_NAME, "History Sample Program"
HISTORY_VERSION, "Version 1.0"
DEFAULT_HISTORY_DBFILENAME, "history"
```

**See Also :**
[AddInFormatError](/domino-c-api-docs/reference/Func/AddInFormatError)
[AddInLogError](/domino-c-api-docs/reference/Func/AddInLogError)
[AddInSetStatus](/domino-c-api-docs/reference/Func/AddInSetStatus)
[AddInCreateStatusLine](/domino-c-api-docs/reference/Func/AddInCreateStatusLine)
[STATUS](/domino-c-api-docs/reference/Data/STATUS)
---
