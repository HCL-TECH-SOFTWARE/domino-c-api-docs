##### Function : MIME
##### MMGetReadReceipt - get Conversion Controls 'read receipt' setting
---
```
#include <mailmisc.h>
WORD LNPUBLIC MMGetReadReceipt(

	CCHANDLE  hCC);
```
**Description :**

The function  MMGetReadReceipt returns the Conversions Controls 'read receipt' 
setting.

**Parameters :**
Input :
hCC  -  a handle to a Conversion Controls context from a previous call to MMCreateConvControls.

Output :
(routine)  -  0 - Do not pass read receipt requests when importing or exporting 
              1 - Support read receipt requests (as Return-Receipt-To when exporting)
              2 - Support read receipt requests (as Disposition-Notification-To when exporting)



**Sample Usage :**
```
WORD wReadReceipt;

wReadReceipt = MMGetReadReceipt(hCC);

```
**See Also :**
[CCHANDLE](/reference/Data/CCHANDLE)
[MMSetReadReceipt](/reference/Func/MMSetReadReceipt)
---
