# CFGMGR32.LIB must be before SETUPAPI.LIB to enable CM_* functions on Win9x
LIBS = advapi32.lib kernel32.lib ole32.lib cfgmgr32.lib setupapi.lib shell32.lib user32.lib
CPPFLAGS = -nologo -WX -W4 -EHsc -I.
RFLAGS =
LFLAGS = -nologo -release -opt:ref -opt:icf $(LIBS)

DEVCON_BIN = \
    devcon.exe
DEVCON_OBJ = \
    cmds.obj \
    devcon.obj \
    dump.obj \
    devcon.res
DEVCON_MSG = \
    msg.rc \
    msg.h \
    MSG00001.bin

all : $(DEVCON_BIN)

clean :
    @for %i in ($(DEVCON_BIN) $(DEVCON_OBJ) $(DEVCON_MSG)) do if exist %i del %i

$(DEVCON_BIN) : $(DEVCON_OBJ)
    link $(LFLAGS) -out:$@ $**

devcon.rc : msg.rc

*.cpp : devcon.h Makefile

devcon.h : msg.h rc_ids.h

$(DEVCON_MSG) : msg.mc
    mc $**

.cpp.obj::
    $(CPP) $(CPPFLAGS) -c $<
