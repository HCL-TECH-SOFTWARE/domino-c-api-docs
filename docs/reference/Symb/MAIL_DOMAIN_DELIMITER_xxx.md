##### Symbolic Value : Mail
##### MAIL_DOMAIN_DELIMITER_xxx - Domain name delimiters.
---
```
#include <mail.h>
```

**Symbolic Values :**

	MAIL_DOMAIN_DELIMITER	  -  Domain name delimiter string for a Domino mail address.

	MAIL_DOMAIN_DELIMITER_CHAR	  -  Domain name delimiter character for a Domino mail address.

	MAIL_DOMAIN_DELIMITER_SPACES	  -  Domain name delimiter string for a Domino mail address. Whether or not this string has spaces depends on the value of MAIL_DOMAIN_DELIMITER_NOSPACES.

	MAIL_DOMAIN_DELIMITER_NOSPACES	  -  A value set to 1 so that there are no spaces in the string defined by MAIL_DOMAIN_DELIMITER_SPACES; for SMTP compatibility.


**Description :**

These are the delimiters used to specify a domain name.


**See Also :**
[MAIL_SERVER_DELIMITER_CHAR](/domino-c-api-docs/reference/Symb/MAIL_SERVER_DELIMITER_CHAR)
---
