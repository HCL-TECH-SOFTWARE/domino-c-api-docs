##### Data Type : Handles
##### DHANDLE - General definition for handles used by Domino and Notes after ND8.0.
---
```
#include <global.h>
```

**Definition :**
```
#if defined(ND64) || defined(NDUNIX64)
	/* this is defined here for all platforms as this is used somewhere in 
the pack */
	#ifdef HANDLE_IS_64BITS
	 #if defined(UNIX)
	  typedef unsigned long DHANDLE; /* 64-bit HANDLEs */
	 #else
	  typedef unsigned long long DHANDLE; /* 64-bit HANDLEs on Windows */
	 #endif
	#else
	 typedef unsigned int DHANDLE; /* 32-bit HANDLEs */
	 #ifndef HANDLE_IS_32BITS
	  #define HANDLE_IS_32BITS
	 #endif
	#endif
	#if !defined(WINDOWS_INCLUDED)
	 typedef unsigned int HANDLE, *PHANDLE;            /* for tdanalyzer */
	#endif
#else  /* 32 BIT platforms */
	#if !defined(WINDOWS_INCLUDED)
	 #if defined(DOSW16)
	  typedef unsigned int DHANDLE; /* really a short, but compiler is 
picky */
	 #elif defined(HANDLE_IS_32BITS)
	  typedef unsigned int DHANDLE; /* 32-bit HANDLEs */
	 #else
	  typedef unsigned short DHANDLE;
	 #endif
	 typedef DHANDLE HANDLE, *PHANDLE;
	#else
	 typedef HANDLE DHANDLE;
	#endif
#endif
```

**Description :**

This datatype is the base type for various kinds of handles used by Domino and Notes. After ND8.0, DHANDLE will be used instead of HANDLE.


**See Also :**
---
