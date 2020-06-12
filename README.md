# SEUCKMOD
KickAssembler source of a previous SEUCK enhancement source that allows custom colour bars over hires chars. The source is documented on how to put things together. Please note that this source code only makes a new front end and plays title + in game music. It does not give you full in game enhancements such as power ups or anything like that. This is just a little curiosity fun production.

INTRODUCTION

SEUCKMOD is a small piece of frame work that allows you create a new front end, with additional colour raster bars behind the text. It also adds a scroll text and allows to play music on your games created on the Shoot Em Up Construction Kit or the Sideways Scrolling SEUCK. It does NOT enhance your SEUCK game completely with power ups or anything in particular like that. The zip archive consists of the complete game archive and source code.

The files are as follows:

In folder C64:
  seuckp1.prg - SEUCK game split into first segment $0900-$6580)
  seuckp2.prg - SEUCK game split into last segment $b6c0-$fffa)
  titlemusic.prg - Title music (Relocated range: $9000-$9fff)
  ingamemusic.prg - In game music (Reolcated range: $a000-$afff)
  titlescreen.bin - Exported Screen data for title screen
  endscreen.bin    - Exported end screen data for end
  
  Outside folder C64:
  seuckmod.asm - Source code
  scrolltext.txt - Scroll text

INSTRUCTIONS:

Before you start, you will need the following software:

KICK ASSEMBLER V5.0 or higher
CHAR PAD V2.0 or higher
VICE C64 or a COMMODORE 64 WITH ACTION REPLAY/RETRO REPLAY (and the ability to transfer files from your C64 to PC)
GOAT TRACKER / CHEESE CUTTER / Or any native C64 music editor, which can relocate music from $1000-$1fff to desired location (Optional)
EXOMIZER / PUCRUNCH / BONGO / BYTE BOOZER Or any native C64 packer / Cruncher (Warning, may take longer if using native packer + cruncher)
SIDPLAY, SIDRELOC 
D64 Editor / Style Dir Master
1. Load in your RAW SEUCK game in to VICE or your Commodore 64, Ultimate 64, etc. Then press the FREEZE button on your Action Replay / Retro Replay and enter the MACHINE CODE MONITOR.

Insert a formatted disk / D64 in to your drive and then save your SEUCK game in to two segments:

a) Type in S "SEUCKP1",8,0900,6580
b) Type in S "SEUCKP2",8,B6C0,FFFA

We are done with this.

2. Grab some music (JCH / DMC / VOICETRACKER, packed music etc) or make your own. Use a music relocator to place the music into the following addresses:

TITLE MUSIC = $9000
IN GAME MUSIC = $A000

You can use SIDReloc to relocate your music, but you MUST remember to save the SID file you wish to relocate as a PSID file. Then in SIDPlay extract it to the project directory as a C64 prg file (You may need to edit the settings in SIDPLAY to change the DAT prefix into PRG). Place the relocated music files in to your C64 directory.

3. Using a D64 editor, extract the files which you have saved in to the C64 directory

4. Create your title screen and end screen using Charpad

a) Design your front end, using CHARPAD. You may use my existing characters as a template. (Since the charpad project has also been included). All characters must remain as one colour in hi-res. Also tile mode must be DISABLED. IMPORTANT: The SAME charset layout must also be used for the end screen.
b) Export your front end and end screen to the folder C64 (Export charset, then map)

5. Using Notepad, edit scrolltext.txt to make it your own scrolling message

6. Also using Notepad or any other text/code editor. Open seuckmod.asm and edit any necessary parts in the code.

7. Open up the command prompt and call kick assembler to assemble the source code:

java -jar "[drive]/[path]/kickass.jar seuckmod.prg

and check for any errors

5. Use a cruncher like Exomizer to crunch the assembled and built file. Jump address is $0800

e.g.
c:\exomizer/win32/exomizer.exe sfx $0800 seuckmod.prg -o [nameofgame].prg -x2
