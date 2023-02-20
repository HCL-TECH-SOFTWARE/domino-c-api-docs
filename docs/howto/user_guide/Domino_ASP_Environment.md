##### Chapter 15-3
##### Domino ASP Environment

The Domino 6 server includes new hosting features that allow multiple organizations to be transparently hosted by a single Domino server.  The Domino domain is configured to support an Application Service Provider (ASP) environment.<br>
<br>
The HCL C API for Domino and Notes is supported in the Domino ASP environment.  This chapter lists some special considerations when using the C API in the Domino ASP environment.<br>

<ul type="disc">
<li>C API entries in the notes.ini file will impact all orgainizations in the Domino ASP envirnonment.  For example, extension managers are fully supported in an ASP environment, but each extension manager services the entire server. If the services of the extension manager must be different for different hosted organizations, then the extension manager itself must be coded to do the filtering. 
<li>The function, NSFGetOrgDir, determines the current organization for a specified user and to returns the organization's data directory.
<li>In an ASP configuration, names in the $Users view are composed by combining the organization name with the user or group name.  Therefore, lookups of names in the $Users view requires both the organization name as well as the user or group name.  To pass the organization name to the NAMELookup function, you must call the C API routine, VDirContextInit.  This function,  initializes a thread-static string with the organization name.  Within the current thread, all future calls to NAMELookup will be scoped by the organization name until VDirContextDestroy is called.  VDirContextDestroy will release the thread-static memory.  You may call VDirContextInit more than once to change the organization name, without calling VDirContextDestroy between VDirContextInit calls.  VDirContextDestroy frees memory that was allocated by VDirContextInit.  If you do not call VDirContextInit before looking up a name in $Users, the lookup will be scoped by the server's organization name.</ul>

---
