##### Symbolic Value : Search
##### SE_Fxxx - SEARCH_MATCH - SERetFlags
---
```
#include <nsfsearc.h>
```
**Description :**

If recompiling a V3 API application and you used the MatchesFormula field the 
following code change should be made:
For V3 -
   1) if (SearchMatch.MatchesFormula == SE_FMATCH)
   2) if (SearchMatch.MatchesFormula == SE_FNOMATCH)
   3) if (SearchMatch.MatchesFormula != SE_FMATCH) is equivalent to 2)
   4) if (SearchMatch.MatchesFormula != SE_FNOMATCH) is equivalent to 1)
For V4 -
   1) if (SearchMatch.SERetFlags & SE_FMATCH)
   2) if (!(SearchMatch.SERetFlags & SE_FMATCH))

**See Also :**
[SEARCH_MATCH](/reference/Data/SEARCH_MATCH)
---
