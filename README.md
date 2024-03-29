# aseprite-errors
This is a not a guide to compile Aseprite but a guide on how to solve main issues when trying to compile it.

# git errors
Just install Git https://git-scm.com/downloads, close and reopen cmd and start the whole process again.

# ninja aseprite
line:
C:\aseprite\build>ninja aseprite
error: 'ninja' is not recognized as an internal or external command, operable program or batch file.

issue: some online tutorials say to create a path C:\Ninja\ninja.exe, whilst it can work for some, some may encounter errors with the system's navigation/localization/readability of ninja. Y

solution: create a path create a C:\Ninja path instead of C:\Ninja\ninja.exe (also, delete the C:\Ninja\ninja.exe path previously created)

additional: if the issue has not been solved, you can also try: ninja -f C:\Ninja\ninja.exe 

error: 'ninja.build' was not found (or similar code, I did not take notes on this one)
issue: current directory is not correct, after executing commands, cmd is currently on C:\aseprite\build\build instead of C:\aseprite\build

solution: redirect by using
cd C:\aseprite\build

## compilation started but failed

error:
[1/1533] Building C object third_party\CMakeFiles\tinyexpr.dir\tinyexpr\tinyexpr.c.obj
FAILED: third_party/CMakeFiles/tinyexpr.dir/tinyexpr/tinyexpr.c.obj

...

C:\aseprite\third_party\lua\llex.c(13): fatal error C1083: Cannot open include file: 'locale.h': No such file or directory
ninja: build stopped: subcommand failed.

issue: forgot to initialize the Visual Studio call in cmd:
call "C:\Program Files\Microsoft Visual Studio\2022\Community\Common7\Tools\VsDevCmd.bat" -arch=x64
always required for the compilation
