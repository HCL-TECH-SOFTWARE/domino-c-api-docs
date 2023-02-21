##### Function : Billing
##### BillingGetClass - Gets the active Billing Class mask
---
```
#include <billing.h>
STATUS LNPUBLIC BillingGetClass(

	DWORD far *BillingClass);
```
**Description :**

BillingGetClass() supplies a 32-bit mask that specifies which billing classes 
are active on the billing server.  This information is derived from the 
notes.ini  BillingClass variable.  This mask value can be bitwise OR'ed with 
the BILL_CLASS_xxx symbols to interpret the active classes. 

Only a billing server task can execute BillingGetClass().  This call is a 
convenience for programs using the BillingWrite() function.  It is not 
necessary to use this call when extracting data from the MQ$Billing message 
queue.

**Parameters :**
Input :
BillingClass  -  Address of the 32-bit Billing Class mask.

Output :
(routine)  -  If message is obtained successfully; NOERROR;
If the notes.ini BillingClass variable is not present; ERR_BAD_PARAM.


BillingClass  -  The active Billing Class mask, that can be logically OR'ed with BILL_CLASS_xxx.


**See Also :**
[BILL_CLASS_xxx](/domino-c-api-docs/reference/Symb/BILL_CLASS_xxx)
[BillingWrite](/domino-c-api-docs/reference/Func/BillingWrite)
---
