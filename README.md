# mame-tiny-with-sdk80
mame tiny build and sdk80 mitigation

mame(tiny) and sdk-80
<PRE>
1. git clone https://github.com/mamedev/mame.git
   <!--
   mame0251s.exe -> extract to mame folder name (should be).
   if you extract to mame0251s folder, then you would get failing
   build.
   https://www.mamedev.org/oldrel.html
   then get bellow above link for 0251s(s meant "source archive").
   https://github.com/mamedev/mame/releases/download/mame0251/mame0251s.exe
   failure symptom:
    Error: invalid option 'with-emulator'
   stack traceback:
        [C]: in function 'error'
        [string "_WORKING_DIR        = os.getcwd()..."]:63: in     
   function '_premake_main'
   gmake: *** [makefile:1246: build/projects/sdl/mametiny/gmake- 
linux/Makefile] Err

*** annoyed regenerate this error. please wait to debug this by me. sorry.
*** cp -rp /mnt/c/Users/user/Downloads/mame.org/build /mnt/c/Users/user/Downloads/mame/build
*** testify residue procedures. 2025/12/19 I forgot how to make it or fix it.
*** I get how to fix above, i will note here.
*** sfx file extract to current dir, so makedir mame and specify path mame.
    I did 7z used, i suspect this would affect result of above(now testing it cause).
*** i search "mame string "_WORKING_DIR = os.getcwd()..."]:63: in function '_premake_main'" on google, 
    then one of mitigation revealed, i found "Run make REGENIE=1". Could it fix of above?(testing yet).
-> I swtiched to use this : https://github.com/mamedev/mame/archive/refs/tags/mame0251.tar.gz
    wget https://github.com/mamedev/mame/archive/refs/tags/mame0251.tar.gz
    gzip -dc mame0251.tar.gz|tar xvf -
    then this extracted. mame-mame0251.
    I prefer use this dirname (and testing it with invoking make).
-->fixed previous notice, that were incorrect...Sorry.(get newest source).

2. get 2 files from this repo.
   makefile  -> top of mame dir(mv makefile makefile.org, then copy)
   sdk80.cpp -> src\mame\intel (mv sdk80.cpp sdk80.cpp.org, then copy)
   <!--build/projects/sdl/mametiny/gmake-linux/Makefile -> same as above.-->
   
3. make
4. get rom
   name: sdk80.zip
   put it into roms\sdk80.zip
   notice:
    a. sdk80.zip is mear a container of rom binary file.
       But tiny indeed loads *.a14 in sdk80.zip as monitor of sdk80.
       so you should change rom file name or ROM_LOAD designation on sdk80.cpp.
       sdk80.zip should be put on .\roms folder as sdk80.zip to use.
       It should be same ROM filename in sdk80.zip and filename on ROM_LOAD.
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
       <img src="https://github.com/cobwebkanamachi/mame-tiny-with-sdk80/blob/main/regexp.jpg" alt="lst to asm diff" title="lst to asm diff"><BR>
</PRE><BR>
residue continues here (2025/12/19 initiated)<BR>
<img src="https://github.com/cobwebkanamachi/mame-tiny-with-sdk80/blob/main/helloworld-sdk80-asm.jpg" alt="hello world of sdk-80 in asm(binary)" title="hello world"><BR>
Enjoy!

 

   
