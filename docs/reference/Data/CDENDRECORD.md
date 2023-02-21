##### Data Type : Composite Data
##### CDENDRECORD - Defines the end of a series of CD Records.
---
```
#include <editods.h>
```
**Description :**

This CD record defines the end of a series of CD records.  Not all CD records 
are enclosed within a CDBEGINRECORD/CDENDRECORD combination.  For those CD 
records that are enclosed within a CDBEGINRECORD/CDENDRECORD combination, the 
Version element is defined in the following table.

CD Signature	Version Value	Symbol (if any)
SIG_CD_BAR	0	BAR_VERSION1
SIG_CD_OLEBEGIN	0	
SIG_CD_FIELD	0	
SIG_CD_EMBEDDEDCTL	0	EMBEDDEDCTL_VERSION1
SIG_CD_GRAPHIC	1	CDGRAPHIC_VERSION2
SIG_CD_V4HOTSPOTBEGIN	0	
SIG_CD_HORIZONTALRULE	1	CDHORIZONTALRULE_VERSION1
SIG_CD_KEYWORD	0	
SIG_CD_LINK2	0	LINK_VERSION1
SIG_CD_MAPELEMENT	1	CDMAPELEMENT_VERSION1
SIG_CD_AREAELEMENT	1	CDAREAELEMENT_VERSION1
SIG_CD_TEXT	0	
SIG_CD_PRETABLEBEGIN	1	

Header Defines this record as a CDENDRECORD
Version Defines the version of this element.  (Note see table above)
Signature Defines the CD Signature the CDENDRECORD is for.



**See Also :**
[BAR_VERSIONxxx](/domino-c-api-docs/reference/Symb/BAR_VERSIONxxx)
[CDAREAELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDAREAELEMENT_VERSIONxxx)
[CDBEGINRECORD](/domino-c-api-docs/reference/Data/CDBEGINRECORD)
[CDGRAPHIC_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDGRAPHIC_VERSIONxxx)
[CDHORIZONTALRULE_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDHORIZONTALRULE_VERSIONxxx)
[CDMAPELEMENT_VERSIONxxx](/domino-c-api-docs/reference/Symb/CDMAPELEMENT_VERSIONxxx)
[EMBEDDEDCTL_VERSIONxxx](/domino-c-api-docs/reference/Symb/EMBEDDEDCTL_VERSIONxxx)
[LINK_VERSIONxxx](/domino-c-api-docs/reference/Symb/LINK_VERSIONxxx)
---
