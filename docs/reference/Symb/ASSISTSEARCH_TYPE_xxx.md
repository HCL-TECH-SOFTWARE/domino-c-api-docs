##### Symbolic Value : Agents
##### ASSISTSEARCH_TYPE_xxx - ODS_ASSISTSTRUCT - wSearchType values for agent search types.
---
```
#include <queryods.h>
```

**Symbolic Values :**

	ASSISTSEARCH_TYPE_NONE	  -  No search type specified.

	ASSISTSEARCH_TYPE_ALL	  -  Run on all documents in database

	ASSISTSEARCH_TYPE_NEW	  -  Run on new documents added since the last run of the Agent.

	ASSISTSEARCH_TYPE_MODIFIED	  -  Run on documents that were new or modified since the last run of the Agent.

	ASSISTSEARCH_TYPE_SELECTED	  -  Run on selected documents.

	ASSISTSEARCH_TYPE_VIEW	  -  Run on all documents in the view.

	ASSISTSEARCH_TYPE_UNREAD	  -  Run on all unread documents.

	ASSISTSEARCH_TYPE_PROMPT	  -  Prompt the user to select the documents.

	ASSISTSEARCH_TYPE_UI	  -  Run on the document currently being viewed in the Notes user interface.

	ASSISTSEARCH_TYPE_COUNT	  -  Total number of search types.


**Description :**

The search type specifies what documents are selected for an Agent to run against.  These constants are used in the wSearchType field of the ODS_ASSISTSTRUCT record for an Agent.


**See Also :**
[ODS_ASSISTSTRUCT](/domino-c-api-docs/reference/Data/ODS_ASSISTSTRUCT)
---
