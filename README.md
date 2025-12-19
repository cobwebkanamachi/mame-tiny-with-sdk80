# mame-tiny-with-sdk80
mame tiny build and sdk80 mitigation

mame(tiny) and sdk-80
<PRE>
1. mame0251s.exe -> extract to mame folder name (should be).
   if you extract to mame0251s folder, then you would get failing
   build.
   https://www.mamedev.org/oldrel.html
  
 https://github.com/mamedev/mame/releases/download/mame0251/mame0251s.exe
   failure symptom:
    Error: invalid option 'with-emulator'
   stack traceback:
        [C]: in function 'error'
        [string "_WORKING_DIR        = os.getcwd()..."]:63: in     
   function '_premake_main'
   gmake: *** [makefile:1246: build/projects/sdl/mametiny/gmake- 
linux/Makefile] Error 1

*** annoyed regenerate this error. please wait to debug this by me. sorry.

2. get 2 files from this repo.
   makefile  -> top of mame dir(mv makefile makefile.org, then copy)
   sdk80.cpp -> src\mame\intel (mv sdk80.cpp sdk80.cpp.org, then copy)
   build/projects/sdl/mametiny/gmake-linux/Makefile -> same as above.
3. make
4. get rom
   name: sdk80.zip
   put it into roms\sdk80.zip
   notice:
    a. sdk80.zip is mear a container of rom binary file.
    b. HILO issue https://github.com/mamedev/mame/issues/6324
       if you got this affected, then you would got D command
       annoying phenomenon.
       if you could appreciate, here has HILO fixed zip file.
       https://www.retrotechnology.com/restore/coward_sdk80.zip
       (you should rename to sdk80.zip and check inside zip
        for rom bin filename is same as src\mame\intel\sdk80.cpp's
        last line arround ROM_LOAD, if not same, you should tweak)
       Mr.Coward 's file has seen on    
       https://www.retrotechnology.com/restore/sdk80.html
       This file is lst file and on the page header, "ISIS-II 8080/8085 MACRO ASSEMBLER, V4.1" was.
       if you produce asm file from this, you would use vim or regexp to edit remove page headers
       and redundant strings.
</PRE>
residue continues here (2025/12/19 initiated)
Enjoy!

 

   
