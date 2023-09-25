##### Chapter 1-2
##### New Features in HCL C API Toolkit for Notes/Domino 14.0.0

This section lists the new and changed features in the HCL C API Toolkit for Notes/Domino 14.0.0<font color="#242424" face="Segoe UI">.</font> See the <i>What's New view</i> in the <i>HCL C API Reference </i>for details.<br>
<b><font size="5" color="#000080"> </font></b><br>
<b><font size="5" color="#000080">Security Functions</font></b><br>
<br>
Some new  functions of security have been added to kfm.h.<br>

<ul type="disc">
<li><b>SECKFMGetIDFlags</b><font size="4"> </font>	<b>Get ID flags information associated to keyfile context.</b><font size="4" face="Times New Roman">.</font> 
<li><b>SECKFMGetUserInfo</b>   <b><font size="4" color="#242424" face="Segoe UI"> </font></b><font size="4">    </font><b>Get user access information for given key file.</b><br>
</ul>
<br>
<b><font size="5" color="#000080">Security Flags</font></b><br>
<br>
Two flags has been added to kfm.h<br>

<ul type="disc">
<li><b><font size="5" color="#000080"> </font></b><b>flDFH_xxx      </b>file define the ID File Header flags.  These flags are stored in the header of an ID file.<br>
</ul>
<br>
             fIDFH_Password	  -  File is password protected<br>
<br>
      	     fIDFH_PWShareable	  -  Password may be shared by all processes.<br>
<br>
<b><font size="5" color="#000080">NIF Functions</font></b><br>
<br>
A  new function of nif have been added to nif.h.<br>

<ul type="disc">
<li><b>NIFReadEntriesExt2</b><b> - Read collection index information .</b></ul>
<br>
<b><font size="5" color="#000080">NIF Flags</font></b><br>
<br>
READ_MASK_TO_JSON	  -  returns output from NIFReadEntriesExt2 in the form of JSON.
<br>
---
