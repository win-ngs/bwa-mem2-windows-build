# bwa-mem2 for Windows: Community-built Windows binaries

This repository provides a Windows build of `bwa-mem2`.
The release archive includes pre-compiled binaries and the [MSYS2-MSYS](https://www.msys2.org/docs/environments/) runtime
DLLs needed to run them from PowerShell without installing MSYS2.

This is **not an official bwa-mem2 release**.
Official bwa-mem2 repository: https://github.com/bwa-mem2/bwa-mem2

This build is based on upstream `bwa-mem2` tag `v2.3`.
Note that upstream `v2.3` still reports `2.2.1` from
`bwa-mem2.exe version` because its internal `PACKAGE_VERSION` value was not
updated for the `v2.3` tag.

## Downloading bwa-mem2 for Windows

Prebuilt Windows binaries are available from the
[Releases](https://github.com/win-ngs/bwa-mem2-windows-build/releases) page
of this repository.

Download the latest release archive, for example:

```text
bwa-mem2-2.3-windows-x86_64-msys.zip
```

After extracting the archive, you should see:

```text
bwa-mem2/
  bwa-mem2.exe
  bwa-mem2.sse41
  bwa-mem2.sse42
  bwa-mem2.avx
  bwa-mem2.avx2
  bwa-mem2.avx512bw
  msys-2.0.dll
  msys-z.dll
  msys-gcc_s-seh-1.dll
  msys-stdc++-6.dll
```

Keep the DLL files in the same folder as `bwa-mem2.exe` and the SIMD-specific
`bwa-mem2.*` executables.

The release archive intentionally contains only binaries and runtime DLLs.
License and third-party notice files are provided in this repository:

- [LICENSE.md](LICENSE.md)
- [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)

## Running bwa-mem2 from PowerShell

Open PowerShell, then move into the extracted `bwa-mem2` folder before running
`bwa-mem2.exe`:

```powershell
# Replace this path with the folder where you extracted the ZIP file.
# For example:
cd C:\Users\your_name\Downloads\bwa-mem2
```

Check the executable:

```powershell
.\bwa-mem2.exe version
```

Index a reference:

```powershell
.\bwa-mem2.exe index .\reference.fa
```

Map paired-end reads:

```powershell
.\bwa-mem2.exe mem -t 8 .\reference.fa .\reads_R1.fastq .\reads_R2.fastq > out.sam
```

The `bwa-mem2.exe` dispatcher automatically chooses the best available SIMD
binary for the current CPU. In normal use, run `bwa-mem2.exe` rather than
launching `bwa-mem2.avx2` or another SIMD-specific binary directly.

## Runtime DLLs included in the release archive

The release archive includes the following MSYS2-MSYS runtime DLLs:

```text
msys-2.0.dll
msys-z.dll
msys-gcc_s-seh-1.dll
msys-stdc++-6.dll
```

These DLLs are required to run the MSYS2-MSYS build of `bwa-mem2.exe` outside
the MSYS2 environment.

The DLLs are redistributed unmodified from MSYS2 packages.

License information for these bundled DLLs is provided in
[THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Build from source

This section is for users who want to build the Windows binaries themselves.

Install [MSYS2](https://www.msys2.org/), then open the **MSYS2-MSYS** terminal
by selecting **MSYS2-MSYS** from the Windows Start menu.

Use the **MSYS2-MSYS** environment, **not MSYS2-UCRT64** or another MinGW
environment.

Update MSYS2:

```bash
pacman -Syu
```

If MSYS2 asks you to close the terminal, close it, reopen **MSYS2-MSYS**, and
run again:

```bash
pacman -Syu
```

Install the required build tools:

```bash
pacman -S --needed base-devel git gcc zlib-devel
```

Build all dispatcher targets:

```bash
make CXX=g++
```

The expected outputs are:

```text
bwa-mem2.exe
bwa-mem2.sse41
bwa-mem2.sse42
bwa-mem2.avx
bwa-mem2.avx2
bwa-mem2.avx512bw
```

## MSYS2-MSYS build notes

The upstream `bwa-mem2` source almost builds in MSYS2-MSYS as-is, but newer GCC
reports missing standard-library declarations in `safestringlib`.

This build adds the required standard headers to:

```text
ext/safestringlib/safeclib/safeclib_private.h
```

The added headers are:

```c
#include <stdlib.h>
#include <ctype.h>
```

They provide declarations for functions such as `abort()` and `toupper()`.

## License

`bwa-mem2` is distributed under the MIT License.

This repository preserves the upstream source and license information.
See the official bwa-mem2 repository for the original source code and license:

https://github.com/bwa-mem2/bwa-mem2

The release archive also includes MSYS2-MSYS runtime DLLs.
See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for third-party package
and license information.

## Disclaimer

This is a community build.

It is not provided, reviewed, or endorsed by the official bwa-mem2 developers.
Please verify the binaries and results in your own analysis environment.
