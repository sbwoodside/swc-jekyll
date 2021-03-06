---
layout: post
title: more dll 
---


One of the programmers on <a href="irc://irc.freenode.net/#mobitopia">#mobitopia </a>was kind enough to build the simple, DLL-based guiengine example from the Nokia SDK for me on windows. I'm using it to test against my linux build. I copied all of the files (the .app, .rsc, and .dll) over to the phone and it works. Then I copied over my own .app file, built against the windows .lib, and that ALSO works. Yay! Now I see that my linux build isn't making the necessary .rsc file. Why not? Oops, that's my fault, when I took out the AIF file from the makefile I also removed the RSC. I just need to remember to copy the .rss file into the src directory next time. OK, I can make a .sis file for the application side of guiengine now on linux and it works OK. 

Now I have built my own DLL from the same source but on linux. If I run <code>strings </code>on the .lib files I see some differences. I'm not sure yet what the differences actually are. In any case, I can build the .app against the linux .lib, install it on the phone with the windows .dll still in place, and it will run. However it crashes when I attempt to draw a shape (with KERN-EXEC 3). 

Finally I have renamed C:/System/Libs/shapemanager.dll to Wshapemanager.dll and copied my own linux-built DLL into that directory. And I launch the app and it runs AND works. OK finally I have built I think a DLL that runs. 

Here is the makefile for the DLL. Note that U1 and U2 must ALWAYS be those values for a DLL file. U3 and USIS3 should be the same.

<pre>EPOC=/home/simon/sandbox/sdk2unix/gcc-target PATH=$(EPOC)/bin:/usr/local/er6/bin:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin include $(EPOC)/lib/makerules/dll TARGET=shapelistmanager U1 = 10000079 U2 = 1000008d U3 = 10005b7e USIS3 = 10005b7e OBJECTS=myshapelistmanager.o shape.o rectangle.o circle.o LIBS = $(EPOCTRGREL)/euser.lib  $(EPOCTRGREL)/estor.lib MTOP=\\System\\Libs CFLAGS+= -DHAVE_CONFIG_H -I. -I../inc -I$(EPOC)/include/libc -DNO_GLOBALS -O2 -D__EPOC32__ -DZLIB -Wall all:$(TARGET).sis -@mkdir -p s60 mv $(TARGET).sis $(TARGET).dll $(TARGET).Lib s60 $(TARGET).sis:$(TARGET).dll $(TARGET).pkg $(TARGET).dll:$(OBJECTS) $(TARGET).o $(TARGET).o: @echo &gt; $(TARGET).o clean: rm -f $(GENERATED) $(TARGET).pkg: @echo "Making $(TARGET).pkg..." @echo '&amp;EN' &gt; $*.pkg @echo '#{"$(TARGET)"},(0x$(USIS3)),1,01,1,NC,TYPE=SISAPP' &gt;&gt; $*.pkg @echo '(0x101F6F88), 0, 0, 0, {"Series60ProductID"}'&gt;&gt; $*.pkg @echo "$(TARGET).dll"-"!:$(MTOP)\\$(TARGET).dll" &gt;&gt; $*.pkg </pre>

Here's my makefile for the app. These UID3 values, by the way, are from the example code.

<pre>EPOC=/home/simon/sandbox/sdk2unix/gcc-target PATH=$(EPOC)/bin:/usr/local/er6/bin:/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin include $(EPOC)/lib/makerules/eikon NAME=guiengine U1 = 1000007a U2 = 100039CE U3 = 10005b7d OBJECTS = guiengine.o guiengineappui.o guienginedocument.o  guiengineapplication.o guiengineappview.o LIBS=$(EPOCTRGREL)/apparc.lib  $(EPOCTRGREL)/avkon.lib  $(EPOCTRGREL)/cone.lib  $(EPOCTRGREL)/eikcore.lib  $(EPOCTRGREL)/estor.lib  $(EPOCTRGREL)/euser.lib  $(EPOCTRGREL)/ws32.lib  ../engine/s60/shapelistmanager.Lib #../../../fromwin/guiengine/shapelistmanager.lib TARGET=$(NAME).app PKGVERS=1,1 PKGFILES=$(NAME).app $(NAME).rsc # $(NAME).aif CFLAGS = -O -DNDEBUG -I. -I../inc -DUID3=0x$(U3) -D_QUARTZ -D_EPOC32_61 -I$(EPOC)/include/libc CPPFLAGS += -D_QUARTZ -D_EPOC32_61 -I../inc all:$(PKGFILES) $(NAME).sis $(NAME).sis:$(NAME).app $(NAME).rsc $(NAME).pkg $(TARGET):$(OBJECTS) $(NAME).aifspec: echo "mbmfile=icon.mbm" &gt;&gt; $(NAME).aifspec echo "ELangEnglish=$(NAME)" &gt;&gt; $(NAME).aifspec semacode.o: $(NAME).rsc clean: rm -f $(GENERATED) $(NAME).aifspec </pre>
