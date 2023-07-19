##### Symbolic Value : Search
##### SE_Fxxx - SEARCH_MATCH - SERetFlags
---
```
#include <nsfsearc.h>
```

**Symbolic Values :**

	SE_FNOMATCH	  -  Does not match formula (deleted or updated).

	SE_FMATCH	  -  Matches formula.

	SE_FTRUNCATED	  -  Document truncated.

	SE_FPURGED	  -  Note has been purged. Returned only when SEARCH_INCLUDE_PURGED is used.

	SE_FNOPURGE	  -  Note has no purge status. Returned only when SEARCH_FULL_DATACUTOFF is used.

	SE_FSOFTDELETED	  -  If SEARCH_NOTIFYDELETIONS: note is soft deleted; NoteClass&NOTE_CLASS_NOTIFYDELETION also on (off for hard delete).


**Description :**

If recompiling a V3 API application and you used the MatchesFormula field the following code change should be made:<br>
For V3 -<br>
   1) if (SearchMatch.MatchesFormula == SE_FMATCH)<br>
   2) if (SearchMatch.MatchesFormula == SE_FNOMATCH)<br>
   3) if (SearchMatch.MatchesFormula != SE_FMATCH) is equivalent to 2)<br>
   4) if (SearchMatch.MatchesFormula != SE_FNOMATCH) is equivalent to 1)<br>
For V4 -<br>
   1) if (SearchMatch.SERetFlags &amp; SE_FMATCH)<br>
   2) if (!(SearchMatch.SERetFlags &amp; SE_FMATCH))


**See Also :**
[SEARCH_MATCH](/domino-c-api-docs/reference/Data/SEARCH_MATCH)
---
