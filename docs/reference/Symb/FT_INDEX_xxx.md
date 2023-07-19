##### Symbolic Value : Full Text Search
##### FT_INDEX_xxx - Full text search indexing options.
---
```
#include <ft.h>
```

**Symbolic Values :**

	FT_INDEX_REINDEX	  -  Forces re-indexing the database from scratch. This option is useful if the indexing options for the database are being changed.

	FT_INDEX_CASE_SENS	  -  Build case sensitive index.

	FT_INDEX_STEM_INDEX	  -  Build an index that includes word variants (stems). This allows searching to include word variants. A full text search index built with the Notes user interface, is automatically stemmed.

	FT_INDEX_PSW	  -  Build index with word, sentence, and paragraph index break option which allows a search for words within a sentence or paragraph.

	FT_INDEX_OPTIMIZE	  -  Optimize index (e.g. for CDROM).

	FT_INDEX_ATT	  -  Index Attachments.

	FT_INDEX_ENCRYPTED_FIELDS	  -  Index Encrypted Fields.

	FT_INDEX_AUTOOPTIONS	  -  Use the index options that are in database. If the database has never been indexed, use the default indexing options. Database indexing options include the Stop Word File name, case sensitivity, the PSW option, reindexing, and the stem index. Note that the stem index will be set if FT_INDEX_AUTOOPTIONS is used.

	FT_INDEX_SUMMARY_ONLY	  -  Index summary data only.

	FT_INDEX_ATT_BINARY	  -  Index all attachments including BINARY formats.


**Description :**

These values define the options used when creating a full text index for a database.  These options may be combined by bitwise OR-ing them together.  However, FT_INDEX_AUTOOPTIONS will ignore all other indexing options and therefore should not be OR-ed with any of the other indexing options.


**See Also :**
[FTIndex](/domino-c-api-docs/reference/Func/FTIndex)
---
