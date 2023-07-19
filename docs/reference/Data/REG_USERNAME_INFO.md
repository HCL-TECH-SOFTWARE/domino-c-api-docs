##### Data Type : User Registration
##### REG_USERNAME_INFO - Structure that defines User Registration Name Information.
---
```
#include <reg.h>
```

**Definition :**

typedef struct {
   char * LastName;
   char * FirstName;
   char * MidInitial;
   char * OrgUnit;
   char * ShortName;
   char * AlternateName;
   char * AltOrgUnit;
   char * AltLanguage;
   DWORD  Spare[4];
} REG_USERNAME_INFO;

**Description :**

This structure defines User Name information for the REGNewUser function.
<ul><br>
<br>
The fields in this structure are:<br>
<br>
LastName		last name of the new user.<br>
FirstName		first name of the new user.<br>
MidInitial		middle initial of the new user.<br>
OrgUnit		organizational unit of the new user.<br>
ShortName		<br>
AlternateName<br>
AltOrgUnit<br>
AltLanguage<br>
Spare</ul>



**See Also :**
[REGNewUser](/domino-c-api-docs/reference/Func/REGNewUser)
---
