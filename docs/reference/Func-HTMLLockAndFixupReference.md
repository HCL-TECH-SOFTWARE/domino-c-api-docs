##### Function : HTML
##### HTMLLockAndFixupReference - Prepare a reference for use.
---
##### #include <htmlapi.h>
STATUS LNPUBLIC **HTMLLockAndFixupReference(**

	MEMHANDLE  hRef,
	HTMLAPIReference **ppRef);
**Description :**
	1) This needs to be called before the reference information can be 
accessed.
	 - does not use HTMLHANDLE.
       2) caller is responsible for unlocking the MEMHANDLE.
**Parameters :**
Input :
hRef  -  memory handle to reference list (this was returned from HTMLGetReference). If this is NULLMEMHANDLE then nothing happens (no error status)

Output :
(routine)  -   NOERROR - Successful.
  ERR_xxx - Errors returned by lower level functions.  Call to OSLoadString to interpret the error status as a string that you may display/log for the user.


ppRef  -  ppRef - is the address of a pointer.  The pointer will be set to point into the locked and fixedup memory.  If hRef is not null then this must not be null

**Sample Usage :**
```
	STATUS rslt = NOERRPR;
	FILE *m_pLogFile;
	HTMLHANDLE cvtr;
	DWORD retval;
	unsigned int refi;
	MEMHANDLE hRef = 0;
	HTMLAPIReference *pRef = 0;
	char *LogInfoFormat = "%s%d\n"; 
	............
	rslt = HTMLGetProperty(cvtr, HTMLAPI_PROP_NUMREFS, &retval);
	fprintf(m_pLogFile, LogInfoFormat, "<HAPI:RefList count=", retval); 

	for ( refi = 0 ; refi < retval; refi++ )
	{
        rslt = HTMLGetReference(cvtr, refi, &hRef);
	 if(rslt)
	 {
	  PrintLogInfo("Error in Getting Reference");
	  return rslt;
	 }
	 
	 rslt = HTMLLockAndFixupReference(hRef, &pRef);
	 if(rslt)
	 {
	  PrintLogInfo("Error in Lock And Fixup Reference");
	  return rslt;
	 }
	 
	 fprintf(m_pLogFile, "%s%d%s\n", "<Reference N=\"", refi, "\"");
	 fprintf(m_pLogFile, LogInfoFormat, " Type:     ", pRef->RefType);
	 fprintf(m_pLogFile, LogInfoFormat, " CmdId:    ", pRef->CommandId);
	 fprintf(m_pLogFile, LogInfoFormat, " Text:     ", pRef->pRefText);
	 fprintf(m_pLogFile, LogInfoFormat, " NTargets: ", pRef->NumTargets);

        // show the target components of one reference.
        nTargets = pRef->NumTargets;
	}
```
**See Also :**
[HTMLAPIReference](D:/md_files/HTMLAPIReference.md)
[HTMLAPI_REF_TYPE](D:/md_files/HTMLAPI_REF_TYPE.md)
[HTMLCreateConverter](D:/md_files/HTMLCreateConverter.md)
[HTMLGetReference](D:/md_files/HTMLGetReference.md)
---
