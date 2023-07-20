##### Symbolic Value : Rich Text
##### ACTIVEOBJECT_FLAG_xxx - Flag settings for ACTIVEOBJECT.
---
```
#include <editods.h>
```

**Symbolic Values :**

	ACTIVEOBJECT_FLAG_MAYSCRIPT	  -  Active object is an applet that accesses JavaScript.

	ACTIVEOBJECT_FLAG_CORBA_APPLET	  -  Active object is a Java applet that uses CORBA.

	ACTIVEOBJECT_FLAG_CORBA_SSL	  -  This is a CORBA applet that uses SSL.

	ACTIVEOBJECT_FLAG_MAIL_PLUGIN	  -  This object comes from a mime mail message.

	ACTIVEOBJECT_FLAG_NOCORBADOWNLOAD	  -  Don't automatically download the jar stuff for applets.

	ACTIVEOBJECT_FLAG_DIGESTAPPLETFILES	  -  Reserved part of ACTIVEOBJECT struct contains applet files digested for signature verification.


**Description :**

Flag settings for the Flags member within an ACTIVEOBJECT record.


**See Also :**
[ACTIVEOBJECT](/domino-c-api-docs/reference/Data/ACTIVEOBJECT)
---
