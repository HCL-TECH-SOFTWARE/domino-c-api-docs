##### Data Type : HTML
##### CmdId - Domino Command Ids
---
```
#include <urltypes.h>
```

**Definition :**
```

```

**Description :**

<tt>This enumerates the commands supported in Domino urls</tt><br>
<br>
<tt>typedef enum _CmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; </tt><br>
<tt>{</tt><br>
<tt>&nbsp; &nbsp; kUnknownCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 0,</tt><br>
<tt>&nbsp; &nbsp; kOpenServerCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 1,</tt><br>
<tt>&nbsp; &nbsp; kOpenDatabaseCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 2,</tt><br>
<tt>&nbsp; &nbsp; kOpenViewCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 3,</tt><br>
<tt>&nbsp; &nbsp; kOpenDocumentCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 4,</tt><br>
<tt>&nbsp; &nbsp; kOpenElementCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 5,</tt><br>
<tt>&nbsp; &nbsp; kOpenFormCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 6,</tt><br>
<tt>&nbsp; &nbsp; kOpenAgentCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 7,</tt><br>
<tt>&nbsp; &nbsp; kOpenNavigatorCmdId &nbsp; &nbsp; &nbsp; &nbsp; = 8,</tt><br>
<tt>&nbsp; &nbsp; kOpenIconCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 9,</tt><br>
<tt>&nbsp; &nbsp; kOpenAboutCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 10,</tt><br>
<tt>&nbsp; &nbsp; kOpenHelpCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 11,</tt><br>
<tt>&nbsp; &nbsp; kCreateDocumentCmdId &nbsp; &nbsp; &nbsp; &nbsp;= 12,</tt><br>
<tt>&nbsp; &nbsp; kSaveDocumentCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 13,</tt><br>
<tt>&nbsp; &nbsp; kEditDocumentCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 14,</tt><br>
<tt>&nbsp; &nbsp; kDeleteDocumentCmdId &nbsp; &nbsp; &nbsp; &nbsp;= 15,</tt><br>
<tt>&nbsp; &nbsp; kSearchViewCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 16,</tt><br>
<tt>&nbsp; &nbsp; kSearchSiteCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 17,</tt><br>
<tt>&nbsp; &nbsp; kNavigateCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 18,</tt><br>
<tt>&nbsp; &nbsp; kReadFormCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 19,</tt><br>
<tt>&nbsp; &nbsp; kRequestCertCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 20,</tt><br>
<tt>&nbsp; &nbsp; kReadDesignCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 21,</tt><br>
<tt>&nbsp; &nbsp; kReadViewEntriesCmdId &nbsp; &nbsp; &nbsp; = 22,</tt><br>
<tt>&nbsp; &nbsp; kReadEntriesCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 23,</tt><br>
<tt>&nbsp; &nbsp; kOpenPageCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 24,</tt><br>
<tt>&nbsp; &nbsp; kOpenFrameSetCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 25,</tt><br>
<tt>&nbsp; &nbsp; kOpenFieldCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 26, &nbsp; /* OpenField command for Java applet(s) &amp; HAPI */</tt><br>
<tt>&nbsp; &nbsp; kSearchDomainCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 27,</tt><br>
<tt>&nbsp; &nbsp; kDeleteDocumentsCmdId &nbsp; &nbsp; &nbsp; = 28,</tt><br>
<tt>&nbsp; &nbsp; kLoginUserCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 29,</tt><br>
<tt>&nbsp; &nbsp; kLogoutUserCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 30,</tt><br>
<tt>&nbsp; &nbsp; kOpenImageResourceCmdId &nbsp; &nbsp; = 31,</tt><br>
<tt>&nbsp; &nbsp; kOpenImageCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 32,</tt><br>
<tt>&nbsp; &nbsp; kCopyToFolderCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 33,</tt><br>
<tt>&nbsp; &nbsp; kMoveToFolderCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 34,</tt><br>
<tt>&nbsp; &nbsp; kRemoveFromFolderCmdId &nbsp; &nbsp; &nbsp;= 35,</tt><br>
<tt>&nbsp; &nbsp; kUndeleteDocumentsCmdId &nbsp; &nbsp; = 36,</tt><br>
<tt>&nbsp; &nbsp; kRedirectCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 37,</tt><br>
<tt>&nbsp; &nbsp; kGetOrbCookieCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 38,</tt><br>
<tt>&nbsp; &nbsp; kOpenCssResourceCmdId &nbsp; &nbsp; &nbsp; = 39,</tt><br>
<tt>&nbsp; &nbsp; kOpenFileResourceCmdId &nbsp; &nbsp; &nbsp;= 40,</tt><br>
<tt>&nbsp; &nbsp; kOpenJavascriptLibCmdId &nbsp; &nbsp; = 41,</tt><br>
<tt>&nbsp; &nbsp; kUnImplemented_01 &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; = 42,</tt><br>
<tt>&nbsp; &nbsp; kChangePasswordCmdId &nbsp; &nbsp; &nbsp; &nbsp;= 43,</tt><br>
<tt>&nbsp; &nbsp; kOpenPreferencesCmdId &nbsp; &nbsp; &nbsp; = 44,</tt><br>
<tt>&nbsp; &nbsp; kOpenWebServiceCmdId &nbsp; &nbsp; &nbsp; &nbsp;= 45,</tt><br>
<tt>&nbsp; &nbsp; kWsdlCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 46,</tt><br>
<tt>/* SDK END */</tt><br>
<tt>&nbsp; &nbsp; //hu</tt><br>
<tt>&nbsp; &nbsp; kGetImageCmdId &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;= 47,</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* &lt;= add new types above here </tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; do not reuse numbers, do not rely on &quot;kNumberOfCmds&quot;</tt><br>
<tt>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; being the same on each side of the API */</tt><br>
<br>
<tt>/* SDK BEGIN */</tt><br>
<tt>&nbsp; &nbsp; kNumberOfCmds &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /* This must remain last */</tt><br>
<tt>} CmdId;</tt>


**See Also :**
---
