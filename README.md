# Aseprite compilation errors
This is a not a guide to compile [Aseprite](https://github.com/aseprite/aseprite) but on how to solve main issues when trying to compile it.

## Git errors
Just install Git in https://git-scm.com/downloads, then close and reopen cmd and start the whole process again.

## Ninja aseprite
Line:
```
C:\aseprite\build>ninja aseprite
```
Error:
```
'ninja' is not recognized as an internal or external command, operable program or batch file.
```

issue: some tutorials say to create a `C:\Ninja\ninja.exe` path, whilst it can work for some, others may encounter errors with the system's navigation/localization/readability of ninja.

solution: create a `C:\Ninja` path instead of `C:\Ninja\ninja.exe` (also, delete the path previously created)

Additionally, if the issue has not been solved, try: `ninja -f C:\Ninja\ninja.exe` 

error: 
```
'ninja.build' was not found (or similar code, I did not take notes on this one)
```

issue: current directory is not correct, after executing commands, cmd is currently on C:\aseprite\build\build instead of C:\aseprite\build

solution: redirect by using `cd C:\aseprite\build`

### compilation started but failed

error:
```
[1/1533] Building C object third_party\CMakeFiles\tinyexpr.dir\tinyexpr\tinyexpr.c.obj
FAILED: third_party/CMakeFiles/tinyexpr.dir/tinyexpr/tinyexpr.c.obj
...
C:\aseprite\third_party\lua\llex.c(13): fatal error C1083: Cannot open include file: 'locale.h': No such file or directory
ninja: build stopped: subcommand failed.
```

issue: forgot to initialize the Visual Studio call in cmd:
```
call "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
always required for the compilation
```
## other errors (uncommon)
Issues with Skia or Aseprite files/folders. If you do not use any compression software and just Windows' native one, there might be some issues with copy and pasting files (from downloads to Local Disk), try to decompress *before* copying, else some subfolders or files might not be copied.

## farewell
I hope this quick guide was useful, it is mainly meant for users who have never compiled any program before.
