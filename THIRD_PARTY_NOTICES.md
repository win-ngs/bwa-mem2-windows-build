# Third-Party Notices for bwa-mem2 Windows Build

This repository provides a community-built Windows package for `bwa-mem2`.
The release archive includes prebuilt `bwa-mem2` executables and the
MSYS2-MSYS runtime DLLs required to run them on Windows.

## bwa-mem2

Package:

```text
bwa-mem2
```

Description:

```text
The next version of the BWA-MEM sequence alignment algorithm.
```

License:

```text
MIT License
```

Official repository:

```text
https://github.com/bwa-mem2/bwa-mem2
```

Copyright notice from upstream:

```text
BWA-MEM2 (Sequence alignment using Burrows-Wheeler Transform),
Copyright (C) 2019 Intel Corporation, Heng Li.
```

## safestringlib

Package:

```text
safestringlib
```

Description:

```text
Safe C library used by bwa-mem2 and linked into the generated binaries.
```

License:

```text
MIT License
```

Copyright notices from bundled source:

```text
Copyright (c) 2014-2018 Intel Corporation
Copyright (C) 2012, 2013 Cisco Systems
```

Source:

```text
Included under ext/safestringlib in the bwa-mem2 source tree.
```

## Bundled MSYS2-MSYS runtime DLLs

The following DLLs are included in the release archive:

```text
msys-2.0.dll
msys-z.dll
msys-gcc_s-seh-1.dll
msys-stdc++-6.dll
```

These DLLs are redistributed unmodified from MSYS2 packages.

## msys-2.0.dll

Package:

```text
msys2-runtime 3.6.9-1
```

Description:

```text
POSIX emulation engine for Windows.
```

License:

```text
GPL
```

MSYS2 package page:

```text
https://packages.msys2.org/package/msys2-runtime?repo=msys
```

Source:

```text
Please refer to the MSYS2 package page and source package for the
corresponding version of msys2-runtime.
```

## msys-z.dll

Package:

```text
zlib 1.3.2-1
```

Description:

```text
Compression library implementing the deflate compression method.
```

License:

```text
zlib license / custom, as listed by MSYS2
```

MSYS2 package page:

```text
https://packages.msys2.org/packages/zlib?variant=x86_64
```

Upstream project:

```text
https://www.zlib.net/
```

Source:

```text
Please refer to the MSYS2 package page and the upstream zlib project.
```

## msys-gcc_s-seh-1.dll

Package:

```text
gcc-libs 15.2.0-1
```

Description:

```text
GCC runtime library.
```

License:

```text
GPL/LGPL components with the GCC Runtime Library Exception, as listed by the
MSYS2 gcc-libs package.
```

MSYS2 package page:

```text
https://packages.msys2.org/packages/gcc-libs?variant=x86_64
```

Upstream project:

```text
https://gcc.gnu.org/
```

## msys-stdc++-6.dll

Package:

```text
gcc-libs 15.2.0-1
```

Description:

```text
GNU libstdc++ runtime library.
```

License:

```text
GPL/LGPL components with the GCC Runtime Library Exception, as listed by the
MSYS2 gcc-libs package.
```

MSYS2 package page:

```text
https://packages.msys2.org/packages/gcc-libs?variant=x86_64
```

Upstream project:

```text
https://gcc.gnu.org/
```

## Notes

The bundled DLLs are included only to make the MSYS2-MSYS build of `bwa-mem2`
runnable on Windows systems without requiring users to manually locate these
runtime libraries.

No modifications are made to these DLLs in this release.

For exact license terms, users should refer to the corresponding MSYS2 package
pages and upstream source packages.
