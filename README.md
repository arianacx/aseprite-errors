# Aseprite compilation errors
This is a not a guide to compile [Aseprite](https://github.com/aseprite/aseprite) but on how to solve main issues when trying to compile it.
###### General info
- Make sure that when downloading Visual Studio, ["Desktop Development with C++"](https://imgur.com/a/7zs51IT) in the Workloads section is marked and "Windows 10.0.18362.0 SDK" in the Installation Details.
- If you are using customised directories instead of the conventional ones, modify the corresponding commands accordingly.
- Try redownloading the files.
- Deactivate your antivirus momentarily for this process.

## Git errors
Just install Git in https://git-scm.com/downloads, then close and reopen cmd and start the whole process again.

## Ninja errors
All issues with the next line: `C:\aseprite\build>ninja aseprite`.

#### Error #1
```
'ninja' is not recognized as an internal or external command, operable program or batch file.
```

Whilst creating a `C:\Ninja\ninja.exe` path can work for some, others may encounter errors with the system's localization of ninja.

Create a `C:\Ninja` path instead of `C:\Ninja\ninja.exe` (also, delete the path previously created)

Additionally, if the issue has not been solved, try: `ninja -f C:\Ninja\ninja.exe`.

#### Error #2
```
'ninja.build' was not found (or similar code, I did not take notes on this one).
```

After executing commands, the current directory is not correct. cmd is currently on `C:\aseprite\build\build`. Redirect by using `cd C:\aseprite\build`.

#### Error #3
```
LINK : warning LNK4075: ignoring '/INCREMENTAL' due to '/LTCG' specification
D:\apps\vs\VC\Tools\MSVC\14.28.29333\lib\x64\wsetargv.obj : fatal error LNK1112: module machine type 'x64' conflicts with target machine type 'x86'
```

Compile Aseprite with the x86 version of Skia

call "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\Tools\VsDevCmd.bat" -arch=x64 <- make sure this last argument matches your libraries and machine type.

### Compilation started but failed

```
[1/1533] Building C object third_party\CMakeFiles\tinyexpr.dir\tinyexpr\tinyexpr.c.obj
FAILED: third_party/CMakeFiles/tinyexpr.dir/tinyexpr/tinyexpr.c.obj
...
C:\aseprite\third_party\lua\llex.c(13): fatal error C1083: Cannot open include file: 'locale.h': No such file or directory
ninja: build stopped: subcommand failed.
```

Forgot to initialize the following Visual Studio call in cmd:
```
call "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
always required for the compilation
```

## Other errors (uncommon)
### Issues with Skia or Aseprite files/folders
If you do not use any compression software and just Windows' native one, there might be some issues with copy and pasting files (from downloads to Local Disk), try to decompress *before* copying, else some subfolders or files might not be copied. Try redownloading.

## Farewell
I hope this quick guide was useful, it is mainly meant for users who have never compiled any program before.
