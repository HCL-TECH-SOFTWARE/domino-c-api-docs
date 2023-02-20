##### Chapter 15-2
##### Platform-Specific Naming Conventions

Application components that Domino or Notes must load must follow platform-specific naming conventions to allow Domino or Notes to locate and identify them. These components are:<br>

<ul type="disc">
<li>Server add-in tasks
<li>Executable program libraries (DLLs for Windows, shared object libraries for UNIX systems)
<li>Import and export libraries
<li>External database driver libraries
<li>Extension manager libraries</ul>
<br>
<br>
<b><font size="5" color="#000080">Platform Prefix Characters</font></b><br>
<br>
Each PC-based platform that supports Domino or Notes has a unique platform prefix character, which must appear as the first character in the file name of a server add-in task executable or a dynamic link library loaded by Domino or Notes. These characters are:<br>
<br>
Windows 32-bit:	prefix:  &quot;n&quot;<br>
<br>
For example, the extension manager sample program SAMPLES\MISC\EXTPWD has the name &quot;nextpwd.dll&quot; on 32-bit Windows.
---
