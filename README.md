# README: cc-base.h Project

Implementation Status: Soon. (Already implemented. Just organizing the code for xfer to Github).

This project defines the common base C preprocessor definitions for both C and C++, for multiple compilers and multiple O/S.

It is designed to unify the C preprocessor definitions in the following environment.

1. different languages: C, C++
2. different versions of C: C99, C11
3. different versions of C++: C++03, C++11, C++14
4. different compilers: gcc, clang, msvc
5. different O/S: linux, ios, windows

The goals are:

1. To minimize the need for inserting 'ifdefs' inside project source code.

2. To minimize the need for creation of virtual layers/drivers for the O/S,
language, or compiler.

3. To provide a uniform syntax for generic "typeless" programming, using the
macro CC_AUTO(varname,value), where the compiler can infer the variable
type from its value, and therefore its type need not be specified. The
challenge is that C99, C11, C++03, C++11, and C++14 all have a different
syntax for specifying this same logical construct. For	example:

```C
			int x = 42;
			CC_AUTO(y,x);
			// ==> gcc/clang: C99 & C++03:	__typeof(x) y = x
			// ==> gcc/clang: C11:			__auto_type y = x
			// ==> gcc/clang/msvc: C++11:	auto y = x
			// ==> gcc/clang/msvc: C++14:	decltype(auto) y = x
```

4. To provide a macro "wrapper" for specifying compiler specific attributes
and pragmas that the preprocessor ignores when the associated compiler
is not present. And similarly to provide the infrastructure for
specifying logically equivalent attributes and pragmas via a generic
macro that the preprocessor resolves to	the compiler specific variant.

LANGUAGE MINIMUM REQUIREMENTS:
- C99: full
- C11: optional
- C++03: full
- C++11: optional
- C++14: optional
- C++ Boost library must compile: yes

COMPILER MINIMUM REQUIREMENTS:
- gcc v4.6.4+ (Apr 2013)
- clang v3.4.2+ (June 2014)
- Ubuntu 14.04.1 LTS, Trusty Tahr (July 2014)
- MSVC 1900+ (2015)

O/S SUPPORT:
- Android
-	IOS
- Linux
- Win32

COMPILERS ACTUALLY TESTED:
- gcc/g++ v5.4.0 (June 2016)
- clang/clang++ v3.8.0 (March 2016)
- Ubuntu 16.04.2 LTS, Xenial (Feb 2017)

TEST ENV: Ubuntu 16.04, gcc/clang

## --
<address>
<br>AUTHOR: Avraham DOT Bernstein AT gmail
<br>DATE: 2017-05-22T21:26:00Z
<br>Copyright (c) Avraham Bernstein, Jerusalem ISRAEL. All rights reserved.
<br>LICENSE: Apache License, Version 2.0: https://opensource.org/licenses/Apache-2.0
</address>

